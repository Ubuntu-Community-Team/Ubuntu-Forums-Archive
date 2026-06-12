---
title: "Xp partition wont load (hal.dll error) Any easy fix with Ubuntu?"
date: 2009-02-04
forum: General Help
---

### Post by otz070 on 2009-02-04
Ok my xp partition Got messed up and [COLOR="RoyalBlue"](<windows root> system32 hal.dll is missing or corrupt.)[/COLOR] I tried to use Ubuntu to replace the file but It didn't work... unless I did it wrong... I really don't want to have to reinstall windows on this computer because, There are things that I still need on that partition, but I also will be eventually scrapping that partition in trade for a larger ubuntu one. (this is an old computer so backups arent really the best option right now.)



After some quick research and remembering that the problem started when I deleted the leftmost partition (see gpartd screen)
I have come to figure that the problem is most likely a problem with the windows boot.ini pointing to the wrong partition or it is corrupt so I'm guessing that is where to start.....

Anyway Just need to get the xp partition working again.
Thanks:)

---

### Post by Dies on 2009-02-04
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Step 4 gives clear instructions on how to repair boot.ini which is more than likely your problem. 

Or you could just remake the partition you deleted since you don't appear to be using the space for anything anyways. ;)

---

### Post by caljohnsmith on 2009-02-04
Did you previously have an sda1 partition that you deleted? If so, that's most likely the issue, because then you need to reconfigure your boot.ini file. I went ahead and configured a boot.ini file so that I believe it will work with your setup, so how about downloading the attached "boot.ini.txt" file to your Ubuntu desktop and do:
```
sudo mount /dev/sda2 /mnt
mv ~/Desktop/boot.ini.txt /mnt/boot.ini
```
Let me know if that works or not.

---

### Post by otz070 on 2009-02-05
Going to try the above suggestion (download boot.ini and work with terminal and such;) thanks!:D) 

And a little more additonal info just incase this don't work (while I'm thinking of it):
The first partition I deleted was an old windows restore partition that I NEVER use so I figure get back the 4gib free space.... unfortunatuly the windows xp partition that I want to move decides to do otherwise (Basically Join the 4gib with the winxp then shrink right then add to ubuntu drive....(hopefully thats worded clearly enough to understand) Since thats not seeming to work I decided to make the 4gib drive as a music drive that I can access for both systems (mp3 ogg ect.) (Eventually)

Ok off to try this now........;)

---

### Post by otz070 on 2009-02-05
Yes:) finally fixed. the boot.ini file didn't work though, but the remake partition did thanks!!!!!!!!!:)
Just made the 4gib for my music drive while I was twiddling with the partition editor and restarted (hoping for the best) and it works yay for me!!!

---

### Post by mbuller10 on 2009-12-18
Thanks a million caljohnsmith, I got the exact same error after formatting ubuntu 9.10, and your solution worked perfectly

---

