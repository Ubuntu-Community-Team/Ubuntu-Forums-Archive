---
title: "My computer is beeping when I turn it off!"
date: 2009-03-16
forum: General Help
---

### Post by Max-P on 2009-03-16
[COLOR="Red"]UPDATE: This topic is not solved, please read page 2![/COLOR]
Hi all,

When Ubuntu is powering off, it starts beeping very loud (system beeps) even if I blacklisted the "pcsprk" module. I doesn't stop beeping until the computer is completely powered off. It doesn't always do it, and I don't know why. There is no errors on the screen, no clue.

I am using Intrepid Ibex, 64 bits version.

Thanks for helping (before I get crazy)

---

### Post by LoneWolfJack on 2009-03-16
go to system -> administration -> system log

is there anything you would consider fishy in your debug, kernel or syslog?

---

### Post by OrangeCrate on 2009-03-16
Try this, it worked for me in Intrepid...

Enter at terminal:

sudo nano /etc/modprobe.d/blacklist

Add to the bottom of the list:

# this is how you mute annoying beeps in console and shutdown
blacklist pcspkr

---

### Post by skymera on 2009-03-16
System > Preferences > Sound

You can turn off system beep there too.

I don't, i love system beep.

---

### Post by unutbu on 2009-03-16
A while ago I updated my linux kernel. I installed 

```
linux-generic linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-headers-generic linux-image-2.6.27-11-generic linux-image-generic

```
but I neglected to install 
```

linux-libc-dev linux-restricted-modules-common
```

The machine seemed to run fine except that it made a incessant beeping sound when I tried to shut it off... everyone else was trying to sleep... quite embarrassing.

The problem went away after I updated the linux-libc-dev and linux-restricted-modules-common packages.

---

### Post by OrangeCrate on 2009-03-16
> **skymera said:**
> System > Preferences > Sound

You can turn off system beep there too.

I don't, i love system beep.

The last time I checked, that doesn't work on Intrepid, which the OP is using. But, maybe something's changed...

---

### Post by SuperSonic4 on 2009-03-16
Or you could physically remove the system speaker :D

---

### Post by Max-P on 2009-03-16
> **OrangeCrate said:**
> Try this, it worked for me in Intrepid...

Enter at terminal:

sudo nano /etc/modprobe.d/blacklist

Add to the bottom of the list:

# this is how you mute annoying beeps in console and shutdown
blacklist pcspkr
I said that it was already blacklisted.

> **unutbu said:**
> A while ago I updated my linux kernel. I installed 

```
linux-generic linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-headers-generic linux-image-2.6.27-11-generic linux-image-generic

```
but I neglected to install 
```

linux-libc-dev linux-restricted-modules-common
```

The machine seemed to run fine except that it made a incessant beeping sound when I tried to shut it off... everyone else was trying to sleep... quite embarrassing.

The problem went away after I updated the linux-libc-dev and linux-restricted-modules-common packages.
I just installed them, now I will see if it solves something.
> **SuperSonic4 said:**
> Or you could physically remove the system speaker :D
It's on a laptop, if it was a desktop, it would be removed for long :D

> **LoneWolfJack said:**
> go to system -> administration -> system log

is there anything you would consider fishy in your debug, kernel or syslog?
Everything seems normal. 

Thanks everyone for replying!

---

### Post by OrangeCrate on 2009-03-16
> **Max-P said:**
> I said that it was already blacklisted.

I saw that, but frankly, these forums are littered with posts of someone saying they did this, or they did that, and the reality was, they didn't.

I was just being sure that you had done it correctly. If so, then explore other reasons. There is a bug report on Launchpad discussing a similar issue with Intrepid. I'll let you find it on your own.

---

### Post by Max-P on 2009-03-16
> **OrangeCrate said:**
> I saw that, but frankly, these forums are littered with posts of someone saying they did this, or they did that, and the reality was, they didn't.

I was just being sure that you had done it correctly. If so, then explore other reasons. There is a bug report on Launchpad discussing a similar issue with Intrepid. I'll let you find it on your own.

Ok no problem, I already saw that kind of people too :)

I think it's fixed in the today's updates (or with the solution of unutbu (installing "missing" packages, but I'm not sure.) I can't really test it since it doesn't always do this. I will reply if it does it again.

[COLOR="Red"]UPDATE: This is not solved, please read page 2![/COLOR]

---

### Post by Max-P on 2009-03-22
Ok nothing here worked, it just did it again! There is nothing in the system logs (the messages are from more than 20 minutes before). Any idea?

---

### Post by Max-P on 2009-03-25
Nobody:confused:? It still very annoying :(

---

### Post by jmore9 on 2009-03-25
Did you check to see if it is trying to turn off something that is allready off ?  That could cause it to beep away on shutdown.

Just my 2 cents

---

### Post by Max-P on 2009-03-25
> **jmore9 said:**
> Did you check to see if it is trying to turn off something that is allready off ?  That could cause it to beep away on shutdown.

Just my 2 cents

Thanks for helping. How do I do that? The only thing I can say is that it does it not far while or after it stops de samba deamon because I can see the "* Stopping Samba Daemons..." on the screen, but it always shows even when it shuts down normally.

---

### Post by Max-P on 2009-04-06
Please somebody help there :mad:

---

### Post by unutbu on 2009-04-06
I do not know if this will help or not, but perhaps it is something to try:

Open a terminal and type
```

sudo /etc/init.d/samba stop
```

This will run the same script that the computer runs to stop samba at shutdown.
Does this also cause your computer to beep?

You can restart samba by typing
```

sudo /etc/init.d/samba start
```

Also, please post the output of 
```

ls -l /etc/rc{0,2}.d/
```

This will show us a list of scripts that are run when you shutdown. 
Perhaps something in there may give someone an idea.

---

### Post by oldos2er on 2009-04-06
"even if I blacklisted the "pcsprk" module"

 Perhaps double check /etc/modprobe.d/blacklist to make sure you didn't misspell pcspkr.

---

### Post by Max-P on 2009-04-08
Here's the output:

[QUOTE=Terminal]
max-p@max-p-laptop:~$ ls -l /etc/rc{0,2}.d/
/etc/rc0.d/:
total 4
lrwxrwxrwx 1 root root  20 2009-03-10 21:45 K00apt-cacher -> ../init.d/apt-cacher
lrwxrwxrwx 1 root root  17 2009-03-10 21:45 K00hddtemp -> ../init.d/hddtemp
lrwxrwxrwx 1 root root  13 2008-08-19 12:06 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  18 2009-02-06 19:51 K01nxsensor -> ../init.d/nxsensor
lrwxrwxrwx 1 root root  18 2009-02-06 19:51 K01nxserver -> ../init.d/nxserver
lrwxrwxrwx 1 root root  17 2008-08-19 12:06 K02usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  16 2009-03-10 21:45 K08vmware -> ../init.d/vmware
lrwxrwxrwx 1 root root  17 2009-03-10 21:45 K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  14 2009-03-10 21:45 K11cron -> ../init.d/cron
lrwxrwxrwx 1 root root  25 2008-09-13 10:50 K12sl-modem-daemon -> ../init.d/sl-modem-daemon
lrwxrwxrwx 1 root root  16 2008-08-19 12:06 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  15 2009-04-04 19:12 K19samba -> ../init.d/samba
lrwxrwxrwx 1 root root  19 2008-09-20 18:41 K19setserial -> ../init.d/setserial
lrwxrwxrwx 1 root root  23 2009-01-31 09:58 K20akiradrelease -> ../init.d/akiradrelease
lrwxrwxrwx 1 root root  16 2008-08-19 12:06 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  19 2008-12-16 20:03 K20cinestart -> ../init.d/cinestart
lrwxrwxrwx 1 root root  22 2008-10-25 21:41 K20cpufrequtils -> ../init.d/cpufrequtils
lrwxrwxrwx 1 root root  15 2009-02-26 13:28 K20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  20 2009-02-28 15:04 K20fancontrol -> ../init.d/fancontrol
lrwxrwxrwx 1 root root  25 2008-11-02 20:03 K20inetutils-inetd -> ../init.d/inetutils-inetd
lrwxrwxrwx 1 root root  14 2009-02-03 19:50 K20ntop -> ../init.d/ntop
lrwxrwxrwx 1 root root  17 2008-09-19 10:17 K20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2008-09-19 10:17 K20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  14 2009-02-07 10:22 K20wicd -> ../init.d/wicd
lrwxrwxrwx 1 root root  17 2008-08-20 09:47 K20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  16 2009-01-31 18:36 K20xinetd -> ../init.d/xinetd
lrwxrwxrwx 1 root root  19 2008-08-19 18:30 K22mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  23 2008-08-19 18:30 K23mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  20 2008-11-11 20:25 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  23 2008-09-20 18:41 K30etc-setserial -> ../init.d/etc-setserial
lrwxrwxrwx 1 root root  13 2009-03-10 21:45 K39ufw -> ../init.d/ufw
lrwxrwxrwx 1 root root  20 2008-08-19 12:06 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  14 2008-09-20 18:44 K51lirc -> ../init.d/lirc
lrwxrwxrwx 1 root root  26 2008-08-19 12:06 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  28 2009-03-10 21:45 K74dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  17 2009-03-10 21:45 K80openvpn -> ../init.d/openvpn
lrwxrwxrwx 1 root root  15 2008-12-25 17:05 K85bind9 -> ../init.d/bind9
lrwxrwxrwx 1 root root  22 2008-11-11 20:50 K86avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  21 2008-08-19 12:06 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r-- 1 root root 353 2008-10-14 09:02 README
lrwxrwxrwx 1 root root  41 2008-08-19 12:06 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  22 2008-08-19 12:06 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx 1 root root  18 2008-11-11 20:37 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2008-08-19 12:06 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2008-08-19 12:06 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2008-08-19 12:06 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2008-08-19 12:06 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  14 2008-08-19 12:06 S90halt -> ../init.d/halt

/etc/rc2.d/:
total 4
lrwxrwxrwx 1 root root  20 2009-03-10 21:45 K00apt-cacher -> ../init.d/apt-cacher
lrwxrwxrwx 1 root root  17 2009-03-10 21:45 K00hddtemp -> ../init.d/hddtemp
lrwxrwxrwx 1 root root  16 2009-03-10 21:45 K08vmware -> ../init.d/vmware
lrwxrwxrwx 1 root root  17 2009-03-10 21:45 K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  14 2009-03-10 21:45 K11cron -> ../init.d/cron
lrwxrwxrwx 1 root root  16 2009-02-19 20:43 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  23 2009-02-19 20:43 K20akiradrelease -> ../init.d/akiradrelease
lrwxrwxrwx 1 root root  16 2009-02-19 20:43 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  19 2009-02-19 20:43 K20cinestart -> ../init.d/cinestart
lrwxrwxrwx 1 root root  25 2009-02-19 20:43 K20inetutils-inetd -> ../init.d/inetutils-inetd
lrwxrwxrwx 1 root root  14 2009-02-19 20:43 K20ntop -> ../init.d/ntop
lrwxrwxrwx 1 root root  15 2009-02-19 20:43 K20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  19 2009-02-19 20:43 K20tftpd-hpa -> ../init.d/tftpd-hpa
lrwxrwxrwx 1 root root  24 2009-02-19 20:43 K20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  14 2009-02-19 20:43 K20wicd -> ../init.d/wicd
lrwxrwxrwx 1 root root  16 2009-02-19 20:43 K20xinetd -> ../init.d/xinetd
lrwxrwxrwx 1 root root  19 2008-12-22 22:05 K22mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  23 2009-02-19 20:43 K23mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  13 2009-03-10 21:45 K39ufw -> ../init.d/ufw
lrwxrwxrwx 1 root root  22 2009-02-19 20:44 K40dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root  14 2009-02-19 20:43 K51lirc -> ../init.d/lirc
lrwxrwxrwx 1 root root  28 2009-03-10 21:45 K74dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  17 2009-03-10 21:45 K80openvpn -> ../init.d/openvpn
lrwxrwxrwx 1 root root  15 2009-02-19 20:43 K89klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  18 2009-02-19 20:43 K90sysklogd -> ../init.d/sysklogd
-rw-r--r-- 1 root root 556 2008-10-14 09:02 README
lrwxrwxrwx 1 root root  19 2008-08-19 12:06 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  19 2009-03-10 21:52 S01readahead -> ../init.d/readahead
lrwxrwxrwx 1 root root  21 2008-10-25 21:41 S05loadcpufreq -> ../init.d/loadcpufreq
lrwxrwxrwx 1 root root  17 2008-08-19 12:06 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-08-19 12:06 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  25 2008-08-19 12:06 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root  34 2008-08-19 12:06 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  14 2008-08-19 12:06 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  25 2008-09-13 10:50 S12sl-modem-daemon -> ../init.d/sl-modem-daemon
lrwxrwxrwx 1 root root  22 2008-11-11 20:50 S14avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  15 2008-12-25 17:05 S15bind9 -> ../init.d/bind9
lrwxrwxrwx 1 root root  13 2008-11-15 13:21 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  22 2008-10-25 21:41 S20cpufrequtils -> ../init.d/cpufrequtils
lrwxrwxrwx 1 root root  14 2008-11-11 20:25 S20cups -> ../init.d/cups
lrwxrwxrwx 1 root root  20 2009-02-28 15:04 S20fancontrol -> ../init.d/fancontrol
lrwxrwxrwx 1 root root  22 2009-02-20 08:26 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  23 2008-08-19 12:06 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  19 2008-08-19 12:06 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2009-04-04 19:12 S20samba -> ../init.d/samba
lrwxrwxrwx 1 root root  17 2008-09-19 10:17 S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  17 2008-08-20 09:47 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  13 2008-08-19 12:06 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-08-19 12:06 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-08-19 12:06 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  24 2009-02-07 10:40 S28NetworkManager -> ../init.d/NetworkManager
lrwxrwxrwx 1 root root  13 2008-08-19 12:06 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  31 2008-11-11 20:36 S30system-tools-backends -> ../init.d/system-tools-backends
lrwxrwxrwx 1 root root  20 2008-11-08 09:45 S50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  20 2009-03-10 21:47 S50lm-sensors -> ../init.d/lm-sensors
lrwxrwxrwx 1 root root  24 2008-08-20 09:47 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2008-08-19 12:06 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-08-19 12:06 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-08-19 12:06 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2009-02-06 19:51 S99nxsensor -> ../init.d/nxsensor
lrwxrwxrwx 1 root root  18 2009-02-06 19:51 S99nxserver -> ../init.d/nxserver
lrwxrwxrwx 1 root root  18 2008-08-19 12:06 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-08-19 12:06 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  24 2008-08-19 12:06 S99stop-readahead -> ../init.d/stop-readahead
[/QUOTE]
It seems to have a lot of things there I'm not using :s


It's not samba, I let it stop/start for about 10 minutes and everything went fine. The samba stop message always appear anyway, since usplash is disabled.


pcspkr is blacklisted correctly, no program is able to make the system beep, except on shutdown.

---

### Post by Max-P on 2009-04-10
bump :cry:

---

### Post by unutbu on 2009-04-10
I have an idea, but it (1) is not entirely safe, and (2) will require a fair amount of work on your part.

I'm going to throw it out here, so you can think about it, and maybe you or others will think of a better idea. See below for an explanation of the risk.

I think that if you do the tests described below, you will find the script that is causing the beeps. Once we know which script is causing the problem, we can study what commands are being run by the script, and maybe figure out the cause of the problem.

Anyway, the idea is this:

Each file in /etc/rc0.d gets run at shutdown. The scripts get run in the order that 
they are listed by "ls -l /etc/rc0.d". K00apt-cacher gets run first, then K00hddtemp, and so on. Since you see a message about shutting down samba, we know the machine gets as far as the K19samba script.

Since it starts beeping a little before, during or after the K19samba script, we
can probably reasonably assume the beeping is caused by one of these scripts:

```
K09apache2
K11cron
K12sl-modem-daemon
K16dhcdbd
K19samba
K19setserial 
K20akiradrelease
K20apport
K20cinestart
K20cpufrequtils
```

So the idea is to delete the symlink for one script at a time so it is no longer run during the shutdown process. 

For example,
```

sudo rm /etc/rc0.d/K09apache2
```

Note that deleting the symlink is not the same as deleting the script itself (which is located in /etc/init.d. Restoring the symlink is easy. See below for the command.)

Then shutdown and test if it solves the beeping problem.


**The risk**: I do not know exactly what these shutdown scripts do. I don't have K20akiradrelease or K20cinestart on my machine, for example.

Generally, it is not polite (to the computer) to not run shutdown scripts. What could go wrong? Here's one thing I imagine: Programs may want to save their state, and if you remove the shutdown script, they may not get a chance to save their state before being shutdown abruptly. I think there is only a mild chance of there being a problem caused by temporarily removing the shutdown script, but please note carefully: I can not guarantee that it is perfectly safe. If you have been powering off the machine to stop the beeps, then you have already been skipping some of the shutdown scripts. You are going to have to decide if taking this risk is worth it to find out the cause of the beeping. 

Or, wait a bit. Maybe someone will have a better idea.

If it doesn't solve the problem, then restore the symlink:
```

sudo ln -s /etc/init.d/apache2 /etc/rc0.d/K09apache2
```

Repeat until you find the problem script.

---

### Post by Max-P on 2009-04-11
Well, I can try that but it will be very long as it beeps randomly, once or twice a week. I will at least remove the scripts of programs I don't run or don't have anymore. I think it will be easier to delete everything and start over with a new Jaunty install, when it will be released. It's time to clean everything anyway.

Thanks for helping everyone, but I think now there is no hope for me to solve this :(

---

### Post by josel777 on 2009-04-27
> **Max-P said:**
> Well, I can try that but it will be very long as it beeps randomly, once or twice a week. I will at least remove the scripts of programs I don't run or don't have anymore. I think it will be easier to delete everything and start over with a new Jaunty install, when it will be released. It's time to clean everything anyway.

Thanks for helping everyone, but I think now there is no hope for me to solve this :(

I have the same exact problem. For me it started beeping when I upgraded to 8.10. I tried everything but nothing helped. I just installed 9.04 and the beeping when shutting down is still there. I am using Ubuntu 64 bit on AMD.

Here are my posts:
[http://ubuntuforums.org/showthread.php?t=1139234](http://ubuntuforums.org/showthread.php?t=1139234)

[http://ubuntuforums.org/showthread.php?t=990723](http://ubuntuforums.org/showthread.php?t=990723)

---

