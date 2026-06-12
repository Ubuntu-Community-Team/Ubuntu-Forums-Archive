---
title: "Cedega does not recognize my graphics card"
date: 2007-01-08
forum: Gaming &amp; Leisure
---

### Post by NorthernPaladin on 2007-01-08
Thats my problem. You see, I converted myself to linux this weekend because windoze got f***d up. Now I want to get my games up and running. I installed cedega but it wont recognize my graphics card. The card is nvidia geforce ti4200, ubuntu is 6.10. What to do? And remember, I installed ubuntu(my first other OS than windoze) just this weekend, so I don`t understand anything about it. Thank you all in advance

---

### Post by Tuna-Fish on 2007-01-08
What driver are you using for your card? type glxinfo into terminal and post the output here.

---

### Post by NorthernPaladin on 2007-01-08
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None



I haven`t installed any drivers, I haven`t installed anything else but the OS and cedega  and those patches ubuntu suggested in the beginning

---

### Post by NorthernPaladin on 2007-01-08
Ok, I downloaded the drivers, and when I typed in the terminal "sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run" I got message "Verifying archive integrity... Error in check sums 72654237 2337677326" What to do?

---

### Post by Tuna-Fish on 2007-01-08
Actually, I think you're best off with downloading and using EasyUbuntu ***or*** Automatix2. ( [http://www.ubuntuforums.org/showthread.php?t=308303](http://www.ubuntuforums.org/showthread.php?t=308303) ) They are automated scripts that install the drivers for you, much easier than installing them manually. If you are a glutton for punishment (like me...), follow the instructions at: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Tuna-Fish on 2007-01-08
note: nvidia drivers are on the last tab in Easy Ubuntu.

---

### Post by NorthernPaladin on 2007-01-08
Ok, I downloaded easyubuntu as stated in the instructions, the problem is when I click applications-->system tools--> easyubuntu it asks for password and then nothing happens

---

### Post by Tuna-Fish on 2007-01-09
> **NorthernPaladin said:**
> Ok, I downloaded easyubuntu as stated in the instructions, the problem is when I click applications-->system tools--> easyubuntu it asks for password and then nothing happens

Do you have synaptic, apt-get or something like that running? You can only run a single tool that installs stuff trough apt at a time.

(well, you can run more than one by deleting a lock file at /var/lock but that would be monumentally stupid.)

---

### Post by NorthernPaladin on 2007-01-09
Booted my computer, still nothing happens

---

### Post by Tuna-Fish on 2007-01-09
very weird. run it from terminal ( easyubuntu ), and post the message if any

---

### Post by NorthernPaladin on 2007-01-09
Remember, I`m a n00b. Whats the whole command?

---

### Post by NorthernPaladin on 2007-01-09
By the way, already installed the drivers with automatix2. Now I`ll boot my computer to see if it made a change!

---

### Post by Sammi on 2007-01-09
I used this exelent script to install the newest nvidia drivers: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Very easy to install and run.

---

### Post by NorthernPaladin on 2007-01-09
Whoops, installed drivers with automatix2-->now when I type glxinfo in terminal I get an message that it crashed. I`ll try that script right now by the way

---

### Post by NorthernPaladin on 2007-01-09
YEEAAHHHH!!!!! Now that I ran that script, cedega recognizes my Ti4200!!
Thank you Sammi for the great help
And thank you for being very nice Tuna-Fish
I still haven`t tried if it actually works, but this is some progress at least!

---

### Post by Sammi on 2007-01-09
No problemo, glad to help :D

What games are you going to be trying?

Have you considered [Wine]("http://www.winehq.org") as an alternative to Cedega?

---

### Post by NorthernPaladin on 2007-01-09
Well, the games are Guild Wars(normal and nightfall) and Counter Strike Source. I`ve tried GW, problems. Searching for the forum for answers

---

