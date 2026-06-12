---
title: "Minecraft: Getting stuck at the white mojang screen?"
date: 2011-12-03
forum: Gaming &amp; Leisure
---

### Post by acornty on 2011-12-03
Hello fellow minecrafters,
I've got a problem when installing any mods. I'm attempting to install Better than wolves mod which requires mod loader. I download mod loader drop the necessary files into minecraft.jar, delete meta-inf and close it and start up minecraft. I log in and the screen goes to the white mojang screen where it just hangs. I've left it there for a over an hour now and decided its not just my crappy computer lagging. So can someone help me? I've never heard of this problem before and hope someone knows a solution. 

More info:
I'm on ubuntu 11.10- gnome 3 shell(I've tried using unity as well as default gnome and run into the same problems)
I've tried running minecraft with openjdk 6 as well as sun java 6 and run into the same problem.

Any help is appreciated!
Thanks,
Tyler 

P.S I can install optifine just fine.

---

### Post by ExileAmongYou on 2011-12-04
Just a quick couple of things to check, you might have already covered them:

First off, have you checked the mods' forum pages/websites to make sure they're compatible with the version of Minecraft you're running? It seems like it takes a few weeks for mod creators to get their mods up and running again after a new Minecraft version is released.

Are you adding the mods to the right minecraft.jar? You don't put them in the one you originally downloaded, you put them in /home/<user>/.minecraft/bin/minecraft.jar, in the hidden minecraft folder in your home directory.

---

### Post by acornty on 2011-12-04
> **ExileAmongYou said:**
> Just a quick couple of things to check, you might have already covered them:

First off, have you checked the mods' forum pages/websites to make sure they're compatible with the version of Minecraft you're running? It seems like it takes a few weeks for mod creators to get their mods up and running again after a new Minecraft version is released.

Are you adding the mods to the right minecraft.jar? You don't put them in the one you originally downloaded, you put them in /home/<user>/.minecraft/bin/minecraft.jar, in the hidden minecraft folder in your home directory.

Yup! Believe me, I've quadrupedal checked everything.

---

### Post by Dubslow on 2011-12-21
Arg same issue, though Ubuntu 11.04.

---

### Post by dolphin194 on 2012-01-06
I have the same issue with ModLoader on Ubuntu 10.04 LTS x64 with the Oracle JRE 6

---

### Post by CrammitTheFrog on 2012-01-07
Along with what ExileAmongYou was saying, try to run it without any mods.  If that works, try adding one mod at a time.  I haven't had any problems running it, but I'm using Unity...

---

### Post by dolphin194 on 2012-01-17
I have found that the problem is related to the File Roller application. I believe it keeps corrupting the minecraft.jar when you modify it. Try it with an application other than File Roller (the default Archive Manager in Ubuntu). 

I was able to modify it with the Minecraft Patcher, which can be found here: [http://www.minecraftforum.net/topic/232701-11update-19-mcpatcher-hd-fix-231/](http://www.minecraftforum.net/topic/232701-11update-19-mcpatcher-hd-fix-231/)

---

