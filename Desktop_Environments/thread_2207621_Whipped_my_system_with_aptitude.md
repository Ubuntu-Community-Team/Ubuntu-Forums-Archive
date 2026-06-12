---
title: "Whipped my system with aptitude"
date: 2014-02-24
forum: Desktop Environments
---

### Post by Jacob72 on 2014-02-24
Hello,

I have whipped my system when tyring to remove obsolete program with aptitude.

My system ended up with just a black screen. I loged in to tty terminal and ran 
```
xorg sudo /etc/init.d/xdm stop
```

And got:
 perl: Setting locale failed. debconf: Unable  to to initialize frontend: Dialog. No useable dialog-like program is  installed. Unable to to initialize frontend: Readline. Cant locate  Term/Readline.pm ... Falling back to frontend: Teletype.  /usr/sbin/dpkg-reconfgure: xserver-xorg is broken or not fully  installed.         

Then I tried ```
apt-get
```
and got:
E: Unmet Dependencies. Try apt-get -f install. 

I did this and the install was fail short.

Then ran ```
boot repair
```
Grub says; Minimal Bash-Like editing line editing is supported. Boot gets Error: you need to load the kernel 

Now on live CD Trial and ran Boot Repair, it did not fix the grub.

[http://paste.ubuntu.com/6987192/](http://paste.ubuntu.com/6987192/)

The trial system keeps stalling.

I ran
```
fsck from util-linux 2.20.1
e2fsck 1.42.8 (20-Jun-2013)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I tried installing gsmartcontrol but it opens and shuts imediately with being able to use it ...

I looked at my HD mount points in the Live CD install and they do not show any partitions.

Thanks

---

### Post by leeper69 on 2014-02-24
Hi jacob72 It will prtobably be easear for you to just reinstall and start over.  after backing up your personal data. it only takes me about 20 minutes to reinstall and reload the programs that I use.

---

### Post by Jacob72 on 2014-02-27
Hi Leeper69,

Thanks I did the reinstall.

Jacob

---

