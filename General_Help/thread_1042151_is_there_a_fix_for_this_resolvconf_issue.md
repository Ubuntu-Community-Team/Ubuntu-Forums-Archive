---
title: "is there a fix for this resolvconf issue"
date: 2009-01-17
forum: General Help
---

### Post by hart02 on 2009-01-17
can anyone tell me the if there is a fix for this?if so what steps does it take?

```
rm: cannot remove '/etc/resolvconf/run/interface/* read only file system /etc/rcS.d/S07resolvconf: 116: cannot create /etc/resolvconf/run/enable-updates: read only file system
```

I have it and it is very frustrating. :confused:

i found this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250189]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250189")

but it does it clarify a solution and what step were taken.

I currently am using kernel 2.6.27-11,wicd network manager and virtualbox. the message
> I manage to see where is the mount error.

The problem raised at file /etc/rcS.d/S01mounkernfs.sh. This file calls a function called domount

I put some echo lines to debug and some "read CONTINUE" to stop execution....

It seems theres is and Incorrect use of mount when executing:

 mount -n -t tmpfs -omode=0755,nodev,noexec,nosuid /var/run

and

 mount -n -t usbfs -odevgid=127,devmode=664 -onoexec,nosuid,nodev,devgid=127,devmode=664 /proc/bus/usb

and also

 mount -n -t tmpfs -omode=1777,nodev,noexec,nosuid /var/lock

I all this examples seems that DEVNAME parameter is missing.... I read somewhere that /lib/init/mount-functions.sh has changed the number of parameters....

Then I've gone to /etc/init.d and fount two files mountkernfs:

 mountkernfs.sh

and

 mountkernfs.sh.dpkg-dist

It seems that during upgrading, I say NO to reemplacing my modified mountkernfs.sh file (This modification I think that is related with Virtual Vox if I remember well). I found that at upgrade log:

 $ sudo cat /var/log/dist-upgrade/apt-term.log | grep mount

My solution:

 $ cd /etc/init.d
 $ sudo mv mountkernfs.sh.dpkg-dist mountkernfs.sh

does not make sense to me.
i dont have 
 mountkernfs.sh.dpkg-dist

or mountdevsubfs.sh.dpkg-dist and i dont want to edit any files incorrectly. i go to etc/resolvconf/run/interface/ and i contains no files for network interfaces specificically eth2. I have changed the boot priority of S07resolvconf to S12 and it still has that error. so now i either have to find a soluton. could try reinstalling resolvconf or i start fresh and reformat. i dont want to reformat because i have the way i want it.it took a while too.so if anyone knows a step by step approach it would be appreciated.:)also are there any wicd bash scripts that are available that someone has made that i can use that could fix this or improve performance. an fsck did not fix it when i used a live cd and gparted.

---

### Post by Yellow Pasque on 2009-01-17
Can you give a little more background info? What are you trying to do when you get the error message? Mount something? Boot?

---

### Post by hart02 on 2009-01-17
it is when i boot up that i get this message.

---

### Post by hart02 on 2009-01-17
bump

---

### Post by Yellow Pasque on 2009-01-17
I would try moving the resolvconf script to S38,(make sure the networking script has a greater number than 38) but from the bug reports, it looks like most people need to purge/completely remove resolvconf and reinstall it.
[https://launchpad.net/ubuntu/+source/resolvconf/+bug/33362](https://launchpad.net/ubuntu/+source/resolvconf/+bug/33362)

Is the error preventing your system from booting or functioning?

---

### Post by hart02 on 2009-01-17
It can boot to login but the is no network connection

---

### Post by hart02 on 2009-01-17
Is there alternative to the resolvconf package? I have an ip address on eth2 but no network connection.

---

### Post by Yellow Pasque on 2009-01-17
Did you try purging and reinstalling?

---

### Post by hart02 on 2009-01-17
yes i did do that. it went back to S07.changed it to S38 i rebooted and it had showed no error while booting. i logged in my account, i checked if i could connect locally; nothing. went into /etc/resolvconf/run/interface/ and as far as i know there was no files. rebooted and got the error.Right now it is not installed. i repurged it.

---

### Post by hart02 on 2009-01-17
reinstalled resolvconf and left it at S07. I rebooted and got that error message still. the /etc/resolvconf/run/interface/ does not have anything in it.

---

### Post by maghajan on 2009-09-11
I get this same message during bott up, can anyone help???  Thanks...

---

### Post by dcstar on 2009-09-12
> **maghajan said:**
> I get this same message during bott up, can anyone help???  Thanks...

If there are any **"read only filesystem**" errors then find out what is causing that problem and the rest will go away once it is fixed.

---

