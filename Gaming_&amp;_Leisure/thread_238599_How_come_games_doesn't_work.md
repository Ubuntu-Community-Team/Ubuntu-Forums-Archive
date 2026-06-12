---
title: "How come games doesn't work"
date: 2006-08-17
forum: Gaming &amp; Leisure
---

### Post by simukas on 2006-08-17
I attached the xorg.cfg because i can't any 3d games running whats the problem?

---

### Post by hopstah on 2006-08-17
wow.  so much information.  so many things to go on.  where to begin.....

give specifics!!  come on, if you want help, you need to give us enough to go on.  you didn't mention what games, what happens when you run them, if you have xgl/compiz installed.......

it's a give and take thing here, and you need to give a little more.

---

### Post by meng on 2006-08-17
Yeah maybe also throw in what video card you've got, the xorg.conf refers to a generic card/driver.

---

### Post by striketh on 2006-08-17
He most likely didn't install the graphic cards driver.

---

### Post by simukas on 2006-08-18
OK. I have a Gateway Performance 800 witch Sound Blaster LIve sound card WII card, My graphics card is integrated. My specs are 198 ram 800mgz. My mothre board is Intel 815. I hope this is enouth

---

### Post by simukas on 2006-08-18
s

---

### Post by simukas on 2006-08-18
I'm trying to run Egoboo, SCOURGE, Cube. I'm also trying to run Mupen64 and ePSXe(which works almost fine, but is to slow sometimes)

---

### Post by simukas on 2006-08-18
maybe GLEST

---

### Post by hikaricore on 2006-08-18
So you're trying to run a bunch of random games...  and trying to run hardware intensive emulators.  You may want to focus on a specific game and give as much info as you can about what happens when they run or fail to run.  For now forget about the emulators, you don't have the best memory/cpu setup to handle psx emulation, let alone n64 emulation.  Find a game you want to run and tell us what happens.  Also you may be incorrect about your system spec, unless your motherboard has 3 memory slots with 64meg chips in them.  Double check and take time to type it out, in your haste I believe you butchered your intended post.

Once you figure out what the exact problem is with your hardware/software setup, you should be able to easily configure the emulation software you mentioned.

---

### Post by lupine_nickt on 2006-08-18
...or 1x 128MB, and 1x 64MB... ;)

TBH, 800MHz. simply isn't enough for decent PSX emulation, and with 192MB of RAM, you'll be swapping to disc a lot as well - and that doesn't help. As for the graphics card... saying "it's integrated" doesn't really help too much. At the very least, a manufacturer name would be handy; a model number/name would be even better. It might also be stealing some of your RAM (e.g. you might actually have 256MB... but the integrated graphics card is snarfing 64MB). Have you got any free AGP/PCI Express slots? Or is this a laptop?

The quickest way to find out your current graphics card is to run the command 'lspci' in a terminal. 'lspci |grep VGA' might return the specific line you're looking for; if it doesn't return anything, just post the contents of lspci and we'll see what's there.

For basic 3D games (egoboo, Xmoto, armagetron, etc), then once the drivers are sorted out you should be able to play them fine. Anything requiring more power, however, is likely to necessitate at least a few upgrades.

xF,

...Nick

---

### Post by simukas on 2006-08-18
ok i made my pc miself so i know that i have one 128 and one 64 ram card. i'll try finding the card i'm using. tnx for help..

---

### Post by simukas on 2006-08-18
acutally i'm playing psx gamesa t full speed now :) :) :) :)

i didn't do anything...

---

### Post by simukas on 2006-08-18
this may help i hope [http://www.intel.com/support/graphics/intel815/index.htm](http://www.intel.com/support/graphics/intel815/index.htm) or [http://www.intel.com/design/chipsets/815/](http://www.intel.com/design/chipsets/815/)

---

### Post by simukas on 2006-08-19
try this [http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/) too or this [http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm&agr=N&ProductID=922&DwnldId=8211&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm&agr=N&ProductID=922&DwnldId=8211&strOSs=39&OSFullName=Linux*&lang=eng)

---

### Post by hikaricore on 2006-08-19
> **simukas said:**
> try this [http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/) too or this [http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm&agr=N&ProductID=922&DwnldId=8211&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm&agr=N&ProductID=922&DwnldId=8211&strOSs=39&OSFullName=Linux*&lang=eng)

....who exactly are you talking to?  you originally asked for help and are now posting random links to guides and packages.  I think you need to put the pipe down.

---

### Post by simukas on 2006-08-19
i'm just thinking aloud  ](*,) ](*,) ](*,) . Really i'm asking for people to read it and help explain it in a easier way..

---

### Post by hopstah on 2006-08-19
try this link:  [www.windowsxp.com](www.windowsxp.com)

---

### Post by simukas on 2006-08-19
well this is a community.. tnx you're really helping..

---

### Post by simukas on 2006-08-19
> **hopstah said:**
> Join me in my "No Thread Left Unanswered" iniative! 



yeah... shame...

---

### Post by hopstah on 2006-08-20
if you want help, you have to ask questions.  you can't just post links that you came across and expect someone to regurgitate exactly what it is that you need to do to get something running.  as someone said earlier, start with one game.  tell a bit about your system, and tell what happens when you try and run that game.  you can't expect people to magically pull some solution out of the air when you say "my games don't work" and then expect people to "explain it in an easier way" when you post links prefaced with "try this"

don't get me wrong, i want to help, as do most people on this forum, but it's frustrating when someone makes a thread similar to yours which shows that they haven't attempted to fix anything themselves, and haven't even attempted to make a somewhat coherent post that can be used to fix the problem.

that's my stance.

---

