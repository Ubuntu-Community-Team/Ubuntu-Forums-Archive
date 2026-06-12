---
title: "Linux is not ready for iPod"
date: 2006-07-24
forum: Desktop Environments
---

### Post by SirKillalot on 2006-07-24
Hi,
last week I bought me an iPod but I cant just get it work with my ubuntu desktop. Everytime I mount it the kernel gets an error and the drive gets mounted for read-only. I'm not the only one who has problems with the USB drivers of ubuntu, but I think they're really buggy. I hope they will do something, since I dont want to interact with my ipod on my brother's pc who has windows and itunes.
regards, 
sirk

---

### Post by s_h_a_d_o_w_s on 2006-07-24
there are some programs needed to access an iPod. Search" pod" in synaptic.

---

### Post by nalmeth on 2006-07-24
install GTKpod
Open GTKpod
Sync with the ipod
File -> Create Directories

and you should be good to go

---

### Post by s_h_a_d_o_w_s on 2006-07-24
I hink one is called yamipod

---

### Post by JoWilly on 2006-07-24
Banshee interacts completely with the ipod. banshee-dapp must be installed and the plugin activated in the prefs.

---

### Post by JoWilly on 2006-07-24
Furthermore, if you have a bug with ubuntu, it does not mean that "linux is not ready".

---

### Post by llamakc on 2006-07-24
My 15 year-old daughter has no problems with her iPod on her computer, running Ubuntu since Warty. Have you installed the necessary support packages? There's several pages on wiki.ubuntu.com for getting them up and running.

---

### Post by theboatashore on 2006-07-24
I used to have issues with (K)Ubuntu finding my iPod and mounting it correctly.  I managed to get it working when I edited /etc/fstab (unfortunately, I don't remember what I added and I don't have a backup of my old fstab).  I'm currently using Amarok on Dapper, and it's working perfectly.  I think they did a lot of work on Dapper to make sure that things like automounting devices works properly.

---

### Post by SirKillalot on 2006-07-25
I know that the programs to transfer songs with are working without problems but I think there is a problem with the kernel or the fat driver in linux. Many people have the problem that the kernel says that there's a

File System Panic (sdb2)
....
mounting device for read-only.

and so on.
This is pretty annoying. I know the iPod works perfectly on Windows.
Maybe I'll try to use my iPod with HFS+ or iPodLinux. Or wait for a better vFat driver...

---

### Post by Dubbayoo on 2006-07-25
I have had no problems with the mounting of my Nano, although it took me a while to figure out the quirks of gtkpod-aac. For a while I was ready to give up and use itunes via vmware xp guest. 
Now I use:
- easytag to edit id3 tags
- id3ren to rename files according to id3tags
- gtkpod-aac to sync my ipod
- rhythmbox to listen to music

---

### Post by SirKillalot on 2006-07-25
I tried to convert my iPod to HFS+ and use it unter Linux. Actually I can access pretty well on the filesystem, but when I reboot my iPod after the reformat it wont boot into the OS. It doesnt seem to accept the filesystem. Are there any advices how to convert the iPod to HFS+ in the right way?
Greetings

---

### Post by grim1234 on 2006-07-25
> **SirKillalot said:**
> I tried to convert my iPod to HFS+ and use it unter Linux. Actually I can access pretty well on the filesystem, but when I reboot my iPod after the reformat it wont boot into the OS. It doesnt seem to accept the filesystem. Are there any advices how to convert the iPod to HFS+ in the right way?
Greetings

Probably best if you have access to a mac, then just just ipodupdater from there. not sure about any of the x86 versions of osx (bar legality), or maybe emulating osx perhaps.

---

### Post by Dubbayoo on 2006-07-25
my understanding was that a fat32 formatted ipod was required; that may have been specific to a certain app like gtkpod though.

---

