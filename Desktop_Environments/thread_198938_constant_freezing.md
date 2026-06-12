---
title: "constant freezing"
date: 2006-06-18
forum: Desktop Environments
---

### Post by dracule on 2006-06-18
I am plagued by constant freezing. Every so often the screen will completly lock up. I opened up System Moniter to see if it was the CPU not being able to keep up, but once it would freeze, it was like no time went by and the cpu moniter would start exactly were it left off without any jump. and timers (like on websites) would start again exactly where they were before freezing. I never had any types of problems like this with 5.10 or any other new linux distros, so i dont think its my machine. just right now it frooze twice in a row, once for about 4 minutes and another time for about 15 seconds.  i dont think its my CPU not being powerful enough becuase im just on firefox and i used firefox all the time with 5.10 and SuSE 10.

---

### Post by LKRaider on 2006-06-18
Are you using a nVidia card with the accelerated nvidia drivers? They have a known bug that freezes the X when the system is under load.

Switch to the nv driver if you want to avoid that. Another idea is to use Xgl instead, which doesn't seem to suffer from this.

If you are not using nVidia, please state your hardware details so others can help.

---

### Post by dracule on 2006-06-18
I have an old Nvidia TNT2 16mb ram card (I only use this computer to check email, and as a remote HDD for data), so it might be that driver, could you please tell me how to switch drivers?

---

### Post by LKRaider on 2006-06-19
Do this, type Alt+F2 and execute this command:
```
gksudo gedit /etc/X11/xorg.conf
```

Inside the file, find the parts that reads something like this:
```

Section "Device"
	(...some more lines...)
	Driver		"nvidia"

```
And change the Driver to "nv" instead.

Go to the Section named "Module" (on the beggining of the file), and make sure it has two lines that look like this:
```

	Load	"GLcore"
	Load	"dri"

```
Copy them in there if they are not there, then save the file and close the editor.

You now have to restart your X, so logout from your session, and when you are back to the login screen, press Ctrl+Shit+Backspace and it should start with the new driver.

If by any chance it is already listed as "nv", then you are already running with the unaccelerated driver, and you probably should post a bug report about it.

---

### Post by dracule on 2006-06-19
now the freezing keeps getting worse, it will freeze for 6 minutes on the login screen and then it will freeze for about 3 minutes and then i can move my mouse around for about 2 seconds, then it will freeze again for longer and ill move my mouse and it will freeze for longer. one time it frooze for 15 minutes and it never did unfreeze so i had to crash my session, would it help if i booted into the script only session?(no graphical, only terminal like), and how do i do that if i dont have a grub menu...

PS.. since the freezing is so bad i now cant change that, so i probably need to know how to boot into the script only session.

---

### Post by LKRaider on 2006-06-19
If you have no Grub menu (did you remove it?), the easiest way is using the live CD, mounting the HD, and then editing the files from there.

This system behaviour is very strange. How much RAM do you have? Did you setup a swap partition correctly? Do you see HD activity when the freeze happens?

---

### Post by dracule on 2006-06-19
i have 256mb of ram, and 729mb of swap.(the most it ever uses is 150mb) the computer is a little old (2000) and has a 450mhz pentium 3 processor. but like i say i have had no problems running this new of a Distro before. 

my computer is old so it makes noise (small little popping noises) when it processes information, but when it freezes my computer is completely silent.

no HDD activity light comes on, it just completely freezes, my usb wifi activity light stays on too (if the light was on when it frooze, if it wasnt on when it frooze it just is off). 

i reinstalled a couple of times before, but previous installations did the same thing. but this time im weary of reinstalling because i just spent 6 hours setting up and compiling my wifi driver.

i have no grub menu because it didnt set one up (i had no other distro on my computer at the time)

---

### Post by jesusrp on 2006-06-21
This happens to me as well, suddenly Ubuntu 6.06 freezes, and happened as well with Xubuntu 6.06, and never returns the control, i have no other way than press 5 seconds Power button and restart the system.

My system specs are:
Athlon XP 3200+
Nvidia 6600 GT
1Gb DDR RAM
250 GB HDD
DFI with Nforce Mobo

---

### Post by brimbleshoes on 2006-06-21
Me also, except I have an added problem, my apps also just close randomly.  Nautlius, Terminal, JVM, Thunderbird, Firefox... tb and ff just close, the others give me an error window.

OptiPlex GX620, ATI X600 PCIE video, using fglrx, and hyperthreading=on.  1g of RAM

very weird...

---

### Post by dracule on 2006-06-21
I guess ill just go back to ubuntu 5.10 because it is still doing it. There must be a serious bug.

---

### Post by dracule on 2006-06-21
I guess ill just go back to ubuntu 5.10 because it is still doing it. There must be a serious bug.

---

### Post by brimbleshoes on 2006-06-21
[QUOTE=dracule]I guess ill just go back to ubuntu 5.10 because it is still doing it. There must be a serious bug.[/QUOTE]

I'm using 6.06 on an HP box right now...and my AMD64 box at home and it works great however, the OptiPlex has given me trouble....

I think the optiplex gx620 has the intel 945G chipset, and the generic "ati" driver fir the PCIE dvi card in the xorg.conf didn't work either.  I had to use "radeon" for the live cd to work.  But it just unstable, my apps would close or freeze at random.

---

