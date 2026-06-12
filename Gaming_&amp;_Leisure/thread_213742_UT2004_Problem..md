---
title: "UT2004 Problem."
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by coday on 2006-07-11
Hi guys, this may be a n00b question, but I'll ask nonetheless.

I recently installed UT2004 from the CDs onto my newly created linux partition (im new to linux in general) and went to run the game last night. I encountered some problems when the loading screen came up, sat for about 30 seconds, went away, and stopped functioning. I checked my processes and found no trace that UT was running at all. So, with task manager open, I tried running it again. As the loading screen popped up, the .bin started, and was working. As soon as the loading screen went away, the .bin process went into sleep mode and quickly ended itself. Why is this happening? I tried opening with terminal, with the normal loader.
Am I missing some driver or something?

Specs for the linux box:

2.00 GHz Pentium Processor
nVidia mx 550 card (64 mb)
256 mb RAM

Thanks in advance...

---

### Post by MetalMusicAddict on 2006-07-11
Run the game from a terminal and post the output. Also Im not sure your videocard has enough to run the game.

---

### Post by coday on 2006-07-11
I'm sure my card can run the game, I was able to run fine with max settings
on windows.

I'll try the terminal run.

---

### Post by coday on 2006-07-11
Okay, this is what I got:

WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Driver problem?

---

### Post by jISh on 2006-07-11
Looks like you're missing the nVidia drivers.
Type:
```
sudo apt-get install nvidia-glx
```
In the console.

Then, edit your XORG.conf to reflect the proper settings.
So, push alt+f2, and enter
```
 gksudo gedit /etc/x11/xorg.conf
```

Scroll down to the "Device" section, then changed "driver" from "nv" to "nvidia" (if the installer didn't do it for you).

---

### Post by coday on 2006-07-11
Okay, ill try that. Update in a second.

---

### Post by jISh on 2006-07-11
You'll need to reboot, before you try playing again.

---

### Post by coday on 2006-07-11
Okay, so I did all that, rebooted, and had the same problem (with the bin ending itself and whatnot.)

I think it might have something to do with a 'blip' I encountered when doing the second thing J told me to do. When I tried to open XORG.conf with gedit, I was met by a blank gedit window. No text, no data, no nothing.

Once again, when I tried to run it in terminal I got the following:

WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by jISh on 2006-07-11
Err, don't use captial XORG in the command, it should just be gksudo gedit /etc/X11/xorg.conf

Also, it was a capital X in X11, that was my fault :O

Linux is case sensitive.
And you're having the same problem because your computer isn't using the newly installed drivers yet. You MUST make that edit to the file.

Reboot again, and during loading you should see the nvidia splash screen before you login.

---

### Post by coday on 2006-07-11
alright, I got the spashscreen, so I'll assume the game works fine.

If anything, ill post it here.

Thanks a bunch for your help d00dz!

---

### Post by jISh on 2006-07-11
Hope it worked out for ya ;O

---

### Post by Bmbshl on 2006-07-12
My problem is loading it from the cd's.  When I put the cd1 in the drive it shows up on my desktop. I go into the file and double click the installer....but when I try to "run in terminal" (the linux install not the .exe) nothing happens....the drive just spins forever without opening a terminal or giving me any information.  I know the cd is ok because I just installed it on my other partition in Windows.  Is there something critical that I have overlooked in the process?

Be gentle, I haven't found my Linux footing just yet.

---

### Post by Rosenrot on 2006-07-14
put your cd labelesd 1 in your cdrom drive

then open terminal

sudo sh /media/cdrom0/linux-installer.sh

;]
o and when instalatoin is done DO NOT select play now : ]

i hope you don't have as a hard time as i am fixing nvidia glx and sound issues 

hope this helps

---

