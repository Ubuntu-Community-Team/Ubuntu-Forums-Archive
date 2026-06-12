---
title: "Portable Minecraft"
date: 2011-12-07
forum: Gaming &amp; Leisure
---

### Post by Mars11 on 2011-12-07
I've set up a way to play Minecraft off an external drive on Windows. Just unzip [this file]("goo.gl/VwtPJ") in the root of the drive you want to use. 

I now want to make a Linux version, but I'm not sure how to do it on Linux. Pretty much what I did was make a batch file that told the Minecraft.exe that the AppData folder was on the flash drive. Since in Linux Minecraft stores it's data in the home folder I was wondering if there's a way to tell the minecraft.jar file that the home folder is somewhere on the flash drive? 

I don't know if this is clear enough, but any help would be greatly appreciated.

---

### Post by donkyhotay on 2011-12-08
> **Mars11 said:**
> I've set up a way to play Minecraft off an external drive on Windows. Just unzip [this file]("http://dl.dropbox.com/u/16007317/Projects/Blog/Portable%20Minecraft/Portable%20Minecraft.zip") in the root of the drive you want to use. 

I now want to make a Linux version, but I'm not sure how to do it on Linux. Pretty much what I did was make a batch file that told the Minecraft.exe that the AppData folder was on the flash drive. Since in Linux Minecraft stores it's data in the home folder I was wondering if there's a way to tell the minecraft.jar file that the home folder is somewhere on the flash drive? 

I don't know if this is clear enough, but any help would be greatly appreciated.

What you want to do is make a bash script (similar to a batch script). I don't know if minecraft has a flag option to change the default save information but if it does simply use that in your script to change the save data. If minecraft doesn't have that functionality the other option I can think of would be to write your script so that it temporarily copies the save data to where it needs to go in the home folder and then copies back to the flash drive when done.

---

### Post by Mars11 on 2011-12-08
What I'm trying to do is make Minecraft playable fully from the flash drive. The only thing it'll use the hard drive for is Java. So I'm wondering if there's a way to tell Java/Minecraft that the home folder is located on the flash drive. Using a bash script or whatever.

---

### Post by donkyhotay on 2011-12-09
As I said, it's not a matter of telling java/minecraft where the home folder is. It's a matter of telling minecraft where the saved data (settings, world data) is located. That's dependent entirely on the minecraft launcher flags. I don't know offhand if minecraft has those options on launch. Even if it doesn't though you could write a script that copies the saved data from the flash drive to the home folder on launch and then copies back on close. It's not as elegent but it would work.

---

