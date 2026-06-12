---
title: "Outof hd space"
date: 2006-06-25
forum: Desktop Environments
---

### Post by lnx_usr_86 on 2006-06-25
i am runnin a pentium 4 2.4 with 512 mb ram and a3.2 gb hard drive. my system was running fine until i decided to install ltsp, after starting the install i realised i didnt habve any availiable space so i waited a few mins   then i tried to quit install but no luck so i logged off no icannot log on. it keeps saying im out of hd space and cannot write  sum file for my user. is there anyway to  get arround this or are there any files i cann delete so i have sum room to logon in x so i can fix. 

p.s. my command line knowledge is limited any help is appreciated

---

### Post by hippy4life on 2006-06-25
there may be a better way to do this but if you happen to have a live cd hanging around, slap that in. boot up and delete a couple of non essential files, dont go crazy 50mb should be enough i reckon.

try deleting some mp3/videos or other such stuff or clear out your home directory if its on the same partition


that being said, maybe you should spring for a slightly larger HD since a 200gig sata2 drive cost me less than £50

---

### Post by aysiu on 2006-06-25
You can boot into recovery mode and then type ```
apt-get clean
``` to remove all the .deb files from /var/cache/apt/archives

---

### Post by hippy4life on 2006-06-25
[QUOTE=aysiu]You can boot into recovery mode and then type ```
apt-get clean
``` to remove all the .deb files from /var/cache/apt/archives[/QUOTE]

see i knew there was a better way ;)

---

### Post by lnx_usr_86 on 2006-06-25
my other two hd are 160 and 80 gb i put ubuntu pn the small one so i could back up my windows stuff.

---

