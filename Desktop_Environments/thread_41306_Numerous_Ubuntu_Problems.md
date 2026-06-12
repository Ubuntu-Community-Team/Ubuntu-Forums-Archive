---
title: "Numerous Ubuntu Problems"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Slapzstick on 2005-06-12
1. I get a lot of XML parsing errors. I even get one when I try to view Firefox's history menu. I am using the pre-installed version of firefox.

2. My soundcard doesn't work. It is a Soundblaster Audigy 2 ZS. amixer output:[http://pastebin.ca/14211](http://pastebin.ca/14211)

3. My windows partition(ntfs) won't mount. It isn't listed in /dev and when I try to mount it as described in the unnofficial guide it doesn't work. It is listed as sda1 in fdisk. fdisk output([http://pastebin.ca/14213](http://pastebin.ca/14213))

Any help would be greatly appreciated!

---

### Post by Slapzstick on 2005-06-13
Does anyone have any ideas?

---

### Post by desdinova on 2005-06-13
[QUOTE=Slapzstick]Does anyone have any ideas?[/QUOTE]
 1) Either try the backports version of FF or remove your profile and try it again

3) SDA = scsi disk? You should just be able to replace hda with sda in the guide... What errors do you get?

---

### Post by Curlydave on 2005-06-13
[QUOTE=desdinova]1) 
3) SDA = scsi disk? You should just be able to replace hda with sda in the guide... What errors do you get?[/QUOTE]

That was my thought too. You need to do "/dev/mount/sda1". (I also dual-boot with Windows on a SATA drive.)

---

### Post by imightbegiant on 2005-06-13
1) I've seen this happen when you upgrade firefox while still running it. It's fixed just by killing all firefox processes and starting it again.

2) By default, the Audigy 2 is muted for some reason. run

```
$ alsamixer
``` 
 
and scroll right and unmute the <Audigy A>. Toggling mute is done by pushing 'm'

---

### Post by Slapzstick on 2005-06-13
I fixed the hard drive thing. As for the sound card audigy A is not listed in that window.

---

### Post by Slapzstick on 2005-06-13
Okay here is the status so far:

Windows not mounted -**Fixed**

Firefox messed up -  **fixed** 

[SIZE=4]Sound Card not working - *not fixed* [/SIZE]

---

### Post by Slapzstick on 2005-06-13
The only thing not working is my sound card. I really want this fixed. Please help!

---

### Post by nocturn on 2005-06-14
You posted the mixer output for your card, so I assume it is detected correctly?

Did it work in another OS (other distro, windows)?
Does it work with a liveCD?

How do you test the sound?

---

### Post by Slapzstick on 2005-06-14
It works for windows. I test it by playing music and stuff.

---

### Post by nocturn on 2005-06-14
[QUOTE=Slapzstick]It works for windows. I test it by playing music and stuff.[/QUOTE]

Which program do you use to play music?
Are you using gnome?

---

### Post by desdinova on 2005-06-14
After a reboot, run demsg in a console and look for sound related things - also try alsamixer and check your volume levels.

---

