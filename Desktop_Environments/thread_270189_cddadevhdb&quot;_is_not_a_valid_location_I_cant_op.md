---
title: "cdda:///dev/hdb&quot; is not a valid location I cant open a cd"
date: 2006-10-02
forum: Desktop Environments
---

### Post by CameronCalver on 2006-10-02
Hello  today i decided i would like to install a game that is on a cdrom so i thought this would be an easy task but hey is wasnt,
i put the cd in the drive and up comes sound juices to rip the music off the game so i open nautilus and try to open the cd and it says 
```
cdda:///dev/hdb" is not a valid location.
```
AHHHH i cant even view the files what the.
So i tryed the same thing on my other computer and it does the same.
Does anyone no how i can fix this problem

---

### Post by eeried on 2006-10-16
I have experienced the same problems on other people's computers which have two CD / DVD drives.
We do need some doc on the Ubuntu or Debian file system in fact: /cdrom links to /media/cdrom which links to /media/cdrom0

Ubuntu seems to be lost when /dev/hdb is cdrom0 (it expects it to be hdc).

It's easy enough to mend matters in XMMS but we need an overall solution.

It is rather annoying to spread Linux and not to be able to play or burn cds when installing on other people's boxes :-\

Probably it's a question of master and slave drives but do we need to open the box and mess with the jumpers? or is there a smart Linux way of dealing with this kind of confusion?

Your help would be much appreciated :)

---

