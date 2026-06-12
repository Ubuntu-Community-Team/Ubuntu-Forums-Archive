---
title: "Urgent! Plz Help!"
date: 2008-01-20
forum: Desktop Environments
---

### Post by ugotpowned on 2008-01-20
ok, so FINALLY, after running off of the 7.07 live cd, i can remormat my drive. Of course, I need to have windows xp on it, but im going to install ubuntu too. i don't have time to search, as i have to go make hamburgers, but once im done me and my dad r gonna get down to working on the pc. so just any links to any guides, anything you know thats really special. also, im thinking ill just reformat, make a new partition, then use norton partition magic, but it wouldn't work last time (i tried SO Many times), but then again im kinda scared to install ubuntu first. i mean once u reformat, windows automatically starts installing, i think. no wait, i think it reformats then reboots, then I caould take out the cd, instlal ubuntu on anew reformatted drive, then windows, idk how itll work. eff, i gotta go, just help! :confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by erfahren on 2008-01-20
that post was a little confusing

I've seen people (elsewhere) use the term "reformat" interchangeably with "reinstall" - (like "I'm going to reformat my PC", which meant they were reinstalling Windows. That always bugged me.)  

- apparently you didn't mean it that way though, and I gathered that you currently have WinXP installed

if that's the case you don't necessarily need to do all that to install Ubuntu (7.07?) - you can use the LiveCD to create a partition for Ubuntu to be installed on. see: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

note: if you were set on reinstalling WinXP however, for whatever reason (like it just needs it sometimes) - after booting up to the WinXP disk delete the existing C:\ partition then create a new one (the size you want for Windows) and leave the rest unformatted - and then go forward with the install of WinXP. 

when you to install Ubuntu you can use that free unformatted space

(btw: yes, you're correct - when you select to format the new C:\ with the WinXP installer it will format then automatically start the install afterwards.)

you don't need Partition Magic and it's recommended that you just use Ubuntu's partitioner that is part of the installer (or Gparted, of course). 

- where's our hamburgers? did ya make enough for everyone? - lol

---

### Post by utakubeta on 2008-01-20
Take a deeeeeep breath, and say again what you want to do?

if you want to install 'nix just install it on any free space left on the drive, or another drive. I usually use a separate drive if I can because it saves confusion.

Linux in general is very multi-OS friendly... as long as it's the last OS installed.

That is if you want a dual boot you should be sure to install windows first, THEN install Ubuntu on whatever you have remaining as space.

good luck, Ubuntu is alot of fun once you get used to how things work. Be sure to install at a emulator, so that you can have windows on hand for some of the minor stuff (sorry no gaming outside of cedega in a emu). I find it very useful.

---

### Post by erfahren on 2008-01-20
oh, I forgot include this guide for installing using the LiveCD dual-boot with Windows
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

This site has alot of information - the guide is geared toward installing using the Alternate CD (text based installer) but there is still alot of other relevant information: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

note: if you ever decide to remove Ubuntu - look at the "Uninstall" page of the above site first - it might save you some trouble

good luck :)

---

### Post by ugotpowned on 2008-01-22
okay, so i installed ubuntu, it installed over my freshly installed windows, so what do you know - i reformat the hd AGAIN, install windows, and haven't done shizz wind ubuntu, cuz im scared the partitioner is gonna install over windows yet again. and im going to try again once I finish thie post. okay post finished, imma try installing ubuntu again. o btw, the hamburgers came out great, almost like in n out! WOOT! :guitar:

---

### Post by Rhubarb on 2008-01-22
When you install ubuntu, you have an option to reduce the existing partition (windows), and install ubuntu.

Alternatively you can use a partition editor like gparted (DO NOT USE PARTITION MAGIC - as it has some big problems with linux partitions).
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
Resize you windows partition to about 50% of the drive, make sure the last 50% of your drive is blank, no partitions, nothing.
When installing ubuntu, tell it to install on free space.

Please in future use better english, and try to make it clear and concise so others in this forum can better understand you.

---

### Post by ugotpowned on 2008-01-22
okay, i installed it. and when i wanna go to windows, it says hal.dll is missing or corrupt. wtf. this is what i did - 

1) put the live cd in which I ordered from Ubuntu

2) Clicked in install, then the little question (time zone, blah blah)

3) Partition - I did the first choice. My hd size is 70 gb, and windows is already installed. So I say 15.5 gb. It says windows is on #5 partition, but the last screen, which summarizes what ur giong to do, says its going to do something with partitin #6 and #3

4) so it does the install, and I reboot, but I want to go to windows xp, and what do you know - a black screen comes up and it says hal.dll is missing or corrupt. 

5) i can still go in comptuer and access my files when I go into Ubuntu, so i didn't lose my songs (which is all i had on the freshly installed windows partition anyways)

BTW, when i installed windows, i did use full hd space (exept the 1 gb recovery partition) 

Im THINKING, since it DOES give me the options to do it, that I should do just  a 40 gb paritition for windows, and leave the rest of the 30 or so gigs unallocated or w/e. but WTF is this hal.dll bs?? :mad:

---

### Post by Rhubarb on 2008-01-23
I don't know why windows is complaining about a missing HAL file.

What version of ubuntu are you using (is it 7.10?), and what version of windows are you using (vista?).

There was a problem with older versions of ubuntu (7.04 and older) resizing vista partitions, but this should no longer be a problem with the latest ubuntu 7.10

---

### Post by ugotpowned on 2008-01-23
> **Rhubarb said:**
> I don't know why windows is complaining about a missing HAL file.

What version of ubuntu are you using (is it 7.10?), and what version of windows are you using (vista?).

There was a problem with older versions of ubuntu (7.04 and older) resizing vista partitions, but this should no longer be a problem with the latest ubuntu 7.10


Windows Xp Sp2, and ubuntu 7.10 =/

---

### Post by Rhubarb on 2008-01-23
Ok, that's weird.
If you have the patience to install xp and ubuntu again:

When installing xp, you have the choice of creating a partition for it.
Delete all your existing partitions on the drive (you can use the win xp install to do this), then create an ntfs partition of half your hard drive.  Install windows to that.

Then when you install ubuntu, tell it to install to free space.
This should work for you.

---

### Post by ugotpowned on 2008-01-23
> **Rhubarb said:**
> Ok, that's weird.
If you have the patience to install xp and ubuntu again:

When installing xp, you have the choice of creating a partition for it.
Delete all your existing partitions on the drive (you can use the win xp install to do this), then create an ntfs partition of half your hard drive.  Install windows to that.

Then when you install ubuntu, tell it to install to free space.
This should work for you.

well, i DID try using system rescue cd or w/e, the x86 dowload, and it worked, and at the boot screen i type fb800 or something like these ONE instructions told me. i did, then after that I was supposed to be able to type in run_qtparted, but it said it couldn't run for some reason. every approach has a dead end! but ill try what u said this weeken, cuz i really want ubuntu (since college is started and shizz....)

---

### Post by bentheexo on 2008-01-23
hal.dll in a nut shell:

The file hal.dll, is required for windows to operate. It is used by windows when communicating with your computer's harware. It acts as a translator between windows and your hardware, so that the same windows 'commands' can be executed on hardware manufactured by a variety of different vendors. If hal.dll is unavailable, windows will not function correctly.

hal.dll is flagged as a system process and does not appear to be a security risk. However, removing Hal Library may adversly impact your system.

The Process Server database currently registers hal.dll to Microsoft.

This is part of Microsoft Windows.

---

### Post by ugotpowned on 2008-01-23
> **bentheexo said:**
> hal.dll in a nut shell:

The file hal.dll, is required for windows to operate. It is used by windows when communicating with your computer's harware. It acts as a translator between windows and your hardware, so that the same windows 'commands' can be executed on hardware manufactured by a variety of different vendors. If hal.dll is unavailable, windows will not function correctly.

hal.dll is flagged as a system process and does not appear to be a security risk. However, removing Hal Library may adversly impact your system.

The Process Server database currently registers hal.dll to Microsoft.

This is part of Microsoft Windows.

i see...thanks for the info! And once again, Im going to try tonight to do the dual boot linux. I really need linux too, as my dad is gonna desconnect dsl and aircrack-ng (as ive heard and read) is alot easier to use on linux to hack the wireless routers around my house (yes im that desperate for internet!) :popcorn:

---

