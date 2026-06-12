---
title: "Mounting partitions on boot without fstab"
date: 2012-05-12
forum: Desktop Environments
---

### Post by gdi2k on 2012-05-12
I have encrypted partitions on external USB hard disks. I would like these to mount automatically on boot after I log in (using my password, which unlocks my keyring, containing the necessary keys). 

I can get them to mount instantly by clicking on them in the left bar of Thunar (no password prompt as it has the keys in the keyring). But this is a hassle as I have 3 of them, and if I forget my backups don't run. 

I have all the automounting options set, and unplugging / replugging does work as expected (encrypted partitions mount automatically). 

I've seen a lot of suggestions for using fstab to achieve this, but this isn't feasible for me as the disks are connected to a docking station, and I'm constantly docking and undocking the laptop. 

In the last few versions of Ubuntu (using Nautilus) this worked fine. Is this just a limitation of Thunar?

---

### Post by dentaku65 on 2012-05-12
> **gdi2k said:**
> I have encrypted partitions on external USB hard disks. I would like these to mount automatically on boot after I log in (using my password, which unlocks my keyring, containing the necessary keys). 

I can get them to mount instantly by clicking on them in the left bar of Thunar (no password prompt as it has the keys in the keyring). But this is a hassle as I have 3 of them, and if I forget my backups don't run. 

I have all the automounting options set, and unplugging / replugging does work as expected (encrypted partitions mount automatically). 

I've seen a lot of suggestions for using fstab to achieve this, but this isn't feasible for me as the disks are connected to a docking station, and I'm constantly docking and undocking the laptop. 

In the last few versions of Ubuntu (using Nautilus) this worked fine. Is this just a limitation of Thunar?

I supposed that you can do it via /etc/rc.local for example:
```
/dev/sdxx /media/<your_mountpoint> <options>
/dev/sdxx /media/<your_mountpoint> <options>
/dev/sdxx /media/<your_mountpoint> <options>

[COLOR="Red"]exit 0[/COLOR]
```
Note that "[COLOR="Red"]exit 0[/COLOR]" must be present at the end of rc.local file and, of course you have to give execution permissions:
```
sudo chmod +x /etc/rc.local
```

by

---

### Post by gdi2k on 2012-05-12
Thanks for the pointer regarding rc.local, but I don't think this will work for me as the partitions are luks encrypted, and the keys are in my keyring. I would need to store the key files on the root partition, which defeats the object of encryption. 

I was able to find a bug about the issue from 2010: 
[https://bugzilla.xfce.org/show_bug.cgi?id=3490](https://bugzilla.xfce.org/show_bug.cgi?id=3490)

Sounds like they have a working patch, but no idea if it can still be applied to current source code as it's very old. I've asked, so maybe we'll see.

---

### Post by dentaku65 on 2012-05-12
> **gdi2k said:**
> Thanks for the pointer regarding rc.local, but I don't think this will work for me as the partitions are luks encrypted, and the keys are in my keyring. I would need to store the key files on the root partition, which defeats the object of encryption. 

I was able to find a bug about the issue from 2010: 
[https://bugzilla.xfce.org/show_bug.cgi?id=3490](https://bugzilla.xfce.org/show_bug.cgi?id=3490)

Sounds like they have a working patch, but no idea if it can still be applied to current source code as it's very old. I've asked, so maybe we'll see.

I'm not so familiar with disk encryption; perhaps you should find a way to start a script of automount in xfce session-manager that store the keys inside the disks; here a couple of links:

[https://help.ubuntu.com/community/GPGKeyOnUSBDrive](https://help.ubuntu.com/community/GPGKeyOnUSBDrive)
[http://www.alessiotreglia.com/etichette/bash/](http://www.alessiotreglia.com/etichette/bash/)

---

### Post by cryptotheslow on 2012-05-12
This is a little dumb script I use to mount an external LUKS drive:

```

#!/bin/sh
## mount securetoshiba
echo "Opening LUKS mapping"
sudo cryptsetup luksOpen /dev/sdb1 securetoshiba
echo "Mounting to /media/securetoshiba"
sudo mount /media/securetoshiba

```Along with this /etc/fstab entry:
```

# LUKS ext4 on toshiba usb drive
/dev/mapper/securetoshiba     /media/securetoshiba        ext4    defaults,noauto 0 1

```I think if you messed with your sudo'ers setup to allow your user to run cryptsetup and mount unchallenged then you could use something similar and autorun the script at login.

Would probably be wise to make the script a little more clever to cope with your docked / undocked scenarios.

I know you said using fstab was not an option, but using the noauto option there then checking whether the drives are physically present in the script before attempting to mount gets around that. Admittedly a bit kludgy :)

*edit - *Thinking about it the script would also need to check which USB disk is appearing on which /dev/sdX as they could potentially move around. This is getting less sensible the more I thing about it!

---

### Post by gdi2k on 2012-05-12
Thanks for the suggestions, but it sounds like I'd be getting a bit of a quagmire and possibly out of my depth. 

However, I did make good progress using a much simpler approach. I can invoke thunar-volman --device-added [sysfs address] to make it think I just inserted the device, and it will then act according to its settings defined in the UI (thunar-volman-settings). 

So after booting, provided I have the "Mount removable drives when hot-plugged" enabled in the Settings, I can use: 
```
thunar-volman --device-added /sys/block/sdb/sdb1
```
to get my drive mounted. So I can bung this into my log-in scripts and it will work. Good news! :-) 

But during testing with my multiple drives, I've found that the drives don't always appear at the same sdX locations - so the same disk might be /sys/block/sdb/sdb1 one time and /sys/block/sdc/sdc1 the next time. 

So now I just need to figure out how to get a sysfs address based on UUID - I've Googled for this, but can't find anything useful. Any pointers appreciated!

---

### Post by gdi2k on 2012-05-12
Ok, managed to get it done, here's my dirty script (improvement suggestions welcome): 
```
#!/bin/sh	
sleep 10
thunar-volman --device-added /sys$(udevadm info -q path -n /dev/disk/by-uuid/09f41052-ce64-4d14-9684-e0b5bd241a5c) # Back Up Stick 8GB
thunar-volman --device-added /sys$(udevadm info -q path -n /dev/disk/by-uuid/d4d5eda8-19df-403a-8f0c-78f2a7cbf221) # Seagate 1TB
thunar-volman --device-added /sys$(udevadm info -q path -n /dev/disk/by-uuid/59e1ee00-8169-45a6-91da-3f7e2a6982d5) # WD 500GB
```

Replace the UUIDs with those of your drives, save the script to a location of your preference like ~/.auto-mount and set it to automatically start from Settings -> Settings Manager -> Session and Startup. 

You can fetch the required UUIDs from
```
ls -lah /dev/disk/by-uuid/
```

You will want to make sure that you have set "Mount removable drives when hot-plugged" enabled on Settings -> Settings Manager -> Removable Drives and Media. You also need to "Enable Volume Management" from Thunar -> Edit -> Preferences -> Advanced -> Volume Management (it is byb default in Xubuntu I think).

---

