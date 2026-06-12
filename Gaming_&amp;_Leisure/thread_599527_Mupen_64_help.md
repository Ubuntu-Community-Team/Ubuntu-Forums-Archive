---
title: "Mupen 64 help"
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by BomarJr on 2007-11-01
Hi, I have looked for a whle now and I have not found an answer, but how do you MANUALLY Install Mupen 64? I have found that install script and it helps alot but i just want to know how do manually install it so it'll lanuch. Thank You

---

### Post by dfreer on 2007-11-01
ummm. 
1. download mupen64 from the website:
[http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2](http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2)
2. Extract the files.
3. Enter the new folder and double-click the mupen64 executable
4. Profit!!

Perhaps if you are having problems, you could launch it in terminal and post any error messages you get?

---

### Post by BomarJr on 2007-11-06
sorry i wuz on vacation for a few weeks ;) umm i have already tried all of that & i still get that same error:

Cannot open /home/bomarjr/Roms and Emulators/mupen64-0.5/mupen64: No application suitable for automatic installation is available for handling this kind of file.

please help. i know about that install script but i really need toinstall this manually.

---

### Post by dfreer on 2007-11-06
Can you try this?
```
cd ~/Roms\ and\ Emulators/mupen64-0.5/
ls -l
sudo chmod a+x ./mupen64
./mupen64
```
This program doesn't need installed to run, it should just run.

---

### Post by acoustibop on 2007-11-07
You sure you didn't download the Windows version, BomarJr?

---

### Post by BomarJr on 2007-11-07
oh jeez, acoustibop i think you're right, i tried opening the one i had on my ubuntu desktop and then the one dfreer had the link to and his worked so i think i downloaded the windows version :P man i feel like an idiot .  thank you guys that was my bad. if you want to know the reason why, it's because i wanted to see if it'll run on my ps3 ubuntu. i'll tell you guys my test results when i get the chance but until then have your fingers crossed. :grin:

---

