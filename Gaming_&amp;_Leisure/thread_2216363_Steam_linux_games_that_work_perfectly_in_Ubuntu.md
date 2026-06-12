---
title: "Steam linux games that work perfectly in Ubuntu?"
date: 2014-04-11
forum: Gaming &amp; Leisure
---

### Post by hst19 on 2014-04-11
Hi! I'm new to Ubuntu and recently I installed the native Steam client. Does anyone know which popular games have a reputation for running without problems? I've had a very bad experience with Team Fortress 2 in Ubuntu 12.04 (my hardware meets the requirements) with massive lag making it unplayable. Apparently it is a common problem...

I'm very afraid to spend money and data (my ISP isn't very generous :() to download games only to find that they don't work. If you guys know of any games which are known to work nicely, please let me know. Also, what can I play without problems with Wine?

My specs:

Ubuntu 12.04 64-bit
Intel i3 @ 2.4 Ghz
Nvidia Geforce GT 335M (1 GB) with bumblebee 3.2 (with primus and 32-bit libs installed)
2 GB RAM

---

### Post by silex89 on 2014-04-11
In a system with the specs you show, Team Fortress 2, Dota2, Left4Dead2, Counter Strike titles and Amnesia should work fine. I'm running Saucy in an AMD based laptop (A10 processor, quad core, AMD Richland APU) which in terms of performance lays between an i3 and i5; all open source graphic drivers and playing great these games.

The recent kernel, Mesa and DDX driver updates made a huge progress since 12.04 came out. So my suggestion would be to try out with Trusty once it's released and see for yourself. With that hardware you should be able to render and play those games just fine (and even more heavy duty OpenGL games as well).

If the games you're interested in are still not playable even with the latest open source code, try with the NVidia proprietary driver; it may be a bit risky (in the past, installing these closed source drivers would break your desktop) but if you really want to try it...go for it!. I'll stick with the AMD open source code because it delivers good performance overall.

---

### Post by hst19 on 2014-04-12
Hey thanks for the reply. I do have the Nvidia driver (version 331) installed. Any ideas about Windows games with wine?

---

### Post by oldrocker99 on 2014-04-12
I play a raft of Windows games with wine. PlayOnLinux, in the repos, has many, many scripts for installing Windows programs, from (since you asked about games) GOG.com as well as Steam. I'm playing Skyrim and Oblivion from the same Steam for Windows client that PlayOnLinux installed for Skyrim. I've also successfully installed and played The Witcher 2, but it is coming pretty soon to a native Linux engine.

If you want to support wine development, you can buy a subscription to CrossOver, from [http://www.codeweavers.com](http://www.codeweavers.com); sales directly fund wine's development. I have such a subscription, but I have gotten better results with PlayOnLinux. Go figure. 

Kubuntu 14.04/MATE
AMD Phenom II 965
nVidia 650ti, 331 drivers
16GM RAM

---

### Post by frostschutz on 2014-04-12
Are you planning to update to 14.04? It may work better with recents software/drivers. HL2/TF2/L4D2 worked fine for me, except my hardware is a bit on the weak side (only Intel Haswell igpu). I still have some crashes with Portal 2...

---

### Post by jbaerboc on 2014-04-13
I played and beat Metro Last Light from the Steam Client in Linux Mint [based on Ubuntu] so would assume it would work well in Ubuntu as well.

---

### Post by Ranko Kohime on 2014-04-14
> **hst19 said:**
> Hi! I'm new to Ubuntu and recently I installed the native Steam client. Does anyone know which popular games have a reputation for running without problems? I've had a very bad experience with Team Fortress 2 in Ubuntu 12.04 (my hardware meets the requirements) **with massive lag making it unplayable**. Apparently it is a common problem...

I'm very afraid to spend money and data (my ISP isn't very generous :() to download games only to find that they don't work. If you guys know of any games which are known to work nicely, please let me know. Also, what can I play without problems with Wine?

My specs:

Ubuntu 12.04 64-bit
Intel i3 @ 2.4 Ghz
Nvidia Geforce GT 335M (1 GB) with bumblebee 3.2 (with primus and 32-bit libs installed)
2 GB RAM
Depending on what resolution you are running at, you might be up against hardware limits.  Bumblebee was—and to the best of my knowledge still is—a little sketchy.  I take it since you're using Bumblebee that you have an Optimus graphics setup in a laptop?  It's entirely possible that the game is running on the Intel graphics rather than the Nvidia.  Although, assuming you're using Sandy Bridge (which is to my knowledge the first use of Optimus graphics), that particular discrete GPU isn't really that much more powerful than the Intel one, and actually slightly weaker than the next generation Intel graphics.

That being said, I review games for their compatibility with Linux, and while I don't cover Optimus compatibility (I don't own a laptop with it), I do use my Intel Sandy Bridge laptop as a benchmark for how well the games will run on lower-spec machines.  If you're interested, please check out my YouTube channel in my signature.  :)

---

### Post by hst19 on 2014-04-15
> **jbaerboc said:**
> I played and beat Metro Last Light from the Steam Client in Linux Mint [based on Ubuntu] so would assume it would work well in Ubuntu as well.

That's interesting! It's kind of cool that this game is available natively in linux!

---

### Post by hst19 on 2014-04-15
> **Ranko Kohime said:**
> Depending on what resolution you are running at, you might be up against hardware limits.  Bumblebee was—and to the best of my knowledge still is—a little sketchy.  I take it since you're using Bumblebee that you have an Optimus graphics setup in a laptop?  It's entirely possible that the game is running on the Intel graphics rather than the Nvidia.  Although, assuming you're using Sandy Bridge (which is to my knowledge the first use of Optimus graphics), that particular discrete GPU isn't really that much more powerful than the Intel one, and actually slightly weaker than the next generation Intel graphics.

That being said, I review games for their compatibility with Linux, and while I don't cover Optimus compatibility (I don't own a laptop with it), I do use my Intel Sandy Bridge laptop as a benchmark for how well the games will run on lower-spec machines.  If you're interested, please check out my YouTube channel in my signature.  :)

Hm..I agree that bumblebee is a bit unpolished still...with the nouveau driver it wasn't switching off the dedicated card at all..Now I've come up against another issue..the laptop just shuts down when I try to run Portal from steam, usually a minute or two into the game. I'm going to try this trick to see if it helps, as shown here [https://bbs.archlinux.org/viewtopic.php?pid=1326090#p1326090](https://bbs.archlinux.org/viewtopic.php?pid=1326090#p1326090) and here [http://crunchbang.org/forums/viewtopic.php?id=30733](http://crunchbang.org/forums/viewtopic.php?id=30733). :idea:

---

### Post by batden on 2014-04-19
Intel Core 2 Duo, 4 GB RAM, old GeForce GT 240 here... enough to play HL2 and L4D2 multiplayer using **Enlightenment 19** (Unity is a resource hog compared to E):
[http://ubuntuforums.org/showthread.php?t=2203190&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=2203190&highlight=enlightenment)

You really should upgrade to the latest Ubuntu release... and add more RAM to your PC to enhance your gaming experience and increase overall responsiveness  ;)

---

