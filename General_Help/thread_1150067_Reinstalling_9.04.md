---
title: "Reinstalling 9.04"
date: 2009-05-05
forum: General Help
---

### Post by sports fan Matt on 2009-05-05
If I wanted to reinstall 9.04 from the cd, (Since I cant seem to get into the bios to change it) how would I on a Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop and is there an option to select ext4 from the live cd?

---

### Post by pastalavista on 2009-05-05
Most PC's boot from the CD first by default. Just make sure the disk is loaded before you boot. You should see on the very first screen where it says 'Lenovo' or the brand of motherboard something like "Enter Setup" and a partcular key to press. On my laptop, it is F2 and on my desktop it is Delete. But I don't know what it is for Lenovo. When it is time to set up the partitions, there is a dropdown menu to select the filesystem.

---

### Post by sports fan Matt on 2009-05-05
is there much of an advantage?

---

### Post by pastalavista on 2009-05-06
I made my / partition ext4 and left my /home partition ext3. It boots a good bit faster than with 8.10 and I haven't had any problems except with ATI graphics drivers. My 3D rendering is a lot slower now, but I chose to stick with it until they fix it. I don't play a lot of games or use Compiz so it's fine for me. And it is fast and rock solid. Some people have had issues though so do more research if you're hesitant.

---

### Post by drs305 on 2009-05-06
On my lenovo to enter the BIOS you press the Lenovo Care key (a wrench looking icon on my laptop) or F12.

You select ext4 when you set up the partitioner. There are advantages to ext4 (I run it without problems) but overall at the moment the advantages probably don't outweigh the minuses.

It's been stable for me but you can mount ext3 files as ext4 and get some of the benefits PLUS the ability to remount as ext3 so windows drivers and other ext3 systems can read the files. I like ext4 but I'd say if you have to ask if you need to/should install it, the answer is 'probably not'. Just one opinion.

Here is an excellent post by Sef on the subject:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1133719]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1133719")

---

