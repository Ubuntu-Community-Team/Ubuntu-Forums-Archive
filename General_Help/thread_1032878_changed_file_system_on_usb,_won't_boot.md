---
title: "changed file system on usb, won't boot ?"
date: 2009-01-06
forum: General Help
---

### Post by hayden78 on 2009-01-06
hi. I am very new to using Ubuntu, have always used windows. 

Anyway. I now have ubuntu 8.10 (intrepid?) on my older laptop, which I am trying to use Unetbootin to install on my desktop, because windows will not boot on it, not even to the prompt. 

When I try to use the usb, with UNetbootin, it says it is the wrong file system (FAT32). I was told I should change it to FAT32 (by UNetbootin) so I went into properties and did this. Now the usb stick will not mount. 

Could someone do me a huge favour, please, and explain to me like I am the biggest noob they have ever seen? I do know windows, but linux is very new to me. Though, I do not expect to get help with everything, I have done a bunch myself, but, a lot of the terminal stuff does not seem to work. 


Cheers. 

p.s. just let me know, please... if anything else you need to know.

---

### Post by Zeroberry on 2009-01-06
I assume it's unmounted then. Open the partition editor (System->Administration->Partition Editor) and selecting the usb drive. Right click it, format to FAT32 (make sure you select compatability for both windows and linux if you want that) and then click apply on the top icon bar. Then remove the usb (don't know why you have to do this, but it works for me =P) and put it in again. Should mount automatically.

---

### Post by hayden78 on 2009-01-06
yes, I have heard about this way, but I do not have this partitioner under my admin options. damn. this isn't going to work.

---

### Post by hayden78 on 2009-01-06
*bump*

sorry, I'm still loking for myself, trying to figure it out. I won't bump it again.

---

### Post by hayden78 on 2009-01-06
sorry, but here is what happens when i insert usb and it says it cannot mount:


mount: wrong fs type, bad option, bad superblock on/dev/sdc1, missing codepage or helper program, or other error in some cases useful info is found in syslog-try  dmesg l tail or so

---

### Post by Ahadiel on 2009-01-06
```
sudo apt-get install gparted
```
You'll then have "Partition Editor".

It's not mounting because you haven't actually changed the filesystem, but just change what it tries to mount as.

---

### Post by hayden78 on 2009-01-06
Thank you very much, Ahadiel... however, I cannot get these to download. :(


"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfsprogs reiser4progs jfsutils ntfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 351kB of archives.
After this operation, 2265kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gparted
Install these packages without verification [y/N]? y
0% [Connecting to 70.113.126.18 (70.113.126.18)]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main gparted 0.3.8-1ubuntu2
  Could not connect to 70.113.126.18:8080 (70.113.126.18), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.3.8-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.3.8-1ubuntu2_i386.deb)  Could not connect to 70.113.126.18:8080 (70.113.126.18), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I even tried the apt-get update, several times. It always gives me this answer. Am I to just forget this all together? It never seems to want to do anything when I attempt by terminal.

---

### Post by Ahadiel on 2009-01-06
Are you using a proxy or something?

---

### Post by hayden78 on 2009-01-06
I don't believe so. I do have a firefox proxy add on, but it is not enabled. 

bah. this is so confusing. 


but a nice challenge, more so than I was warned about.

---

### Post by Zeroberry on 2009-01-06
Turn off firewalls, double-check the proxy addon being off and heck, just for the fun of it, bypass the router and plug straight into the modem. Might work...

---

### Post by Ahadiel on 2009-01-06
Maybe try
```
sudo apt-get update --fix-missing
```

---

### Post by hayden78 on 2009-01-06
strange, when I try to go to the website listed in terminal, it says it cannot access server via my browser. 

"The requested URL /ubuntu/...untu2_i386.deb C was not found on this server."

---

### Post by hayden78 on 2009-01-06
welp, figured I'd come back and see if there were any fresh faces...



could someone maybe point me in a direction to get this partitioner program? As previously stated, my system>admin doesn't have it. 

I tried the apt-get thing, it won't connect.

---

### Post by hayden78 on 2009-01-07
Hello. 


I've been trying to mount a usb stick, which got all screwy after I was directed by a prompt to format the usb fat32. I couldn't figure out how to format the usb (thats another issue, nothing in terminal, as far as updates and such, will work. says it cannot connect) So, out of frustration went into properties and changed the file system to fat32, which caused the little problem to begin with. 

Anywho. After reading some other threads, I came across something that just looked right: 

"
The only way I fixed it was to rebuild my fstab

Quote:
sudo cp /etc/fstab /etc/fstab.old
Quote:
sudo blkid -c /dev/null
in another terminal

Quote:
sudo nano /etc/fstab '

After doing this, my usb stick blinked for a couple seconds, but still is unable to mount. 

then all of a sudden this came up: 


"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=728b2a64-8097-4079-95ca-dea9d54e7df7 /               ext3    relatime,erro$
$xternal-hard-drive-596525/# /dev/sda5
UUID=105558bb-9fc1-4af9-abe8-d6f53d450d16 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0"


I am thinking my usb is dev/sda1, just because it looks familiar. However, when I search for "dev/sda1", I am told it doesn't exit... but.. what about what is listed above? It says sda1 . Could someone please shed some light on this? Sorry for those who have already read this thread. I just cannot seem to let go of this, my curious nature is eating away at me. 


thanks for your patience.

---

