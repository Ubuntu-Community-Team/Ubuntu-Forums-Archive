---
title: "Beryl works, but..."
date: 2007-05-01
forum: Desktop Environments
---

### Post by Muad'dib on 2007-05-01
Hello all. I have lurked here for about 3 weeks while I configured my dual boot Dell 2650. I am running Edgy and XP Pro.

The whole reason I wanted to use Linux is the freedom from the chains of having stuff I do not want foisted upon me by Microsoft. That said, here is where I am.

First, I configured my wireless with ndiswrapper and bcm43xx. My wireless works from boot now, every time. No issues whatsoever. It took about 6 complete reinstalls to do this. Next, I got my video support up and running by getting VLC media player. Firefox also works flawlessly. In this process, I have become fairly comfortable with the command line.

Last night I installed nvidia support. After I got my nvidia support working with the correct drivers, I compiled Beryl. The install went pretty smooth. After the final install, I had the Beryl icon, but no cube or wobbly windows. I rebooted and still no beryl efects, but the Beryl manager works and all. I did some looking, and found a few packages I did not get in a different how too, so after verifying the rest of the steps were the same, I compiled those Berly packages. After reboot, I get the Command line, and no screens found error for xorg.conf. No sweat, I did the repair configuration and rebooted. When I did this, I hear the drum, but get a screen thats 3 vertical lines. On a whim, I gave the machine a CTRL+ALT+BACKSPACE and pow, my screen shows up nice and all, and now beryl works (I have to start it after booting up, I will have it auto load after I get the bugs worked out). After I played with the cube a bit, I rebooted, but my computer would not power off. The screen turns off, but the computer is still powered on. I have to use the power button to turn it off now. When I reboot, sometimes X crashes, sometimes it does not. No matter what, I can CTRL+ALT+BACKSPACE  and start it, and beryl always works, but I still have to manualy turn my machine off.

I think my xorg.conf is still messed up. How do I get my xorg.conf back like it was (no, like a pinhead, I did not back it up, but this lesson is learned now)

TIA.

---

### Post by amohanty on 2007-05-01
to redo your x.org :

sudo dpkg-reconfigure xserver-xorg

default all the way through and you should be good to go.

HTH
AM

---

### Post by scanez on 2007-05-01
By the way, just having the Beryl icon in your taskbar does not mean Beryl is running. Right click on the icon, go to Select Window Manager and make sure Beryl is chosen.

---

### Post by Muad'dib on 2007-05-01
amohanty

Thats how I repaired the .conf file to begin with. It got me to a point where I can run, but its still kinda hosed. How is that file configuired to start with, and is there a way to rebuild it like it was originaly?

scanez

Yeah, I figured that part out after a bit. Before I downloaded the packages I was missing, I had the option of Metacity or Beryl, but I could not select Beryl.

Beryl will work now, I just have the shutdown issues, and the random X crash on boot up.

---

