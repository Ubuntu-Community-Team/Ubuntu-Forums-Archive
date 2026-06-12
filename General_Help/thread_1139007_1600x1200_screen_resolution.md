---
title: "1600x1200 screen resolution"
date: 2009-04-26
forum: General Help
---

### Post by Barmaleychik on 2009-04-26
Hello,

I just installed 9.04 and found that the highest resolution my computer offers was 1280x1024. I wonder: can Ubuntu support 1600x1200 resolution at all? If yes, do I need to reinstall Ubuntu to make it working?

Thank you in advance

---

### Post by alberto ferreira on 2009-04-26
If your hardware supports it (monitor and graphics card) Ubuntu supports it and you don't have to reinstall.

I haven't got 9.04 yet but I believe that you can change the resolution in the Gnome-Panel (equivalent to windows taskbar/startbar) >System> Preferences > Screen Resolution.

If it doesn't work press Alt+J (the equivalent to Windows's execute) then type the command :> gksu displayconfig-gtk fill the prompt with your admin (sudo) password and from there select your hardware.

Note: gksu >> launches the command that comes after with administrator (sudo) privileges.

---

### Post by bladeswords on 2009-04-26
No, you don't need to reinstall.  Try running this in the terminal 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

When it is done restart X (ctrl+alt+backspace) and then you should have the extra resolutions avaliable to you.

---

### Post by jaygo on 2009-04-26
I believe ctrl+alt+backspace is disabled by default now. How would you restart x otherwise?

---

### Post by Barmaleychik on 2009-04-26
Ctrl Alt Backspace did not work for me (nothing happened). So I turned off my computer and turned it on again. Is it equivalent to restarting X?

BTW, I still do not have 1600x1200 despite I tried both suggestions in this thread.

Please, help

---

### Post by jaygo on 2009-04-26
yes, restarting the PC will also restart X. 

It seems that the "Display" applet is failing to detect the correct settings for some of us. On my laptop, it thinks the screen can go much higher than it's actually capable of and it shows almost all the resolutions with a 0Hz refresh rate. (And it's only displaying scrambled video)

I don't know where we can go to fix this. In 8.10, I tried manually editing an xorg.conf but ubuntu wouldn't load it correctly on booting. Perhaps there's an update for the software behind "Display" -- I think it's xrandr??

You can try forcing your res up if you're sure it's capable of it, though I have no idea what will happen:
in the terminal:
xrandr -s 1600x1200 -r 60 (or whatever your refresh rate should be at 1600x1200)

---

### Post by Barmaleychik on 2009-04-26
Many thanks Jaygo for your respond. I tried the code which you suggested but got a message: 

             Size 1600x1200 not found in available modes

I can not believe that I can not make ubuntu perform very common task of sending standard 1600x1200 signal to a very common 3 years old samsung monitor with a standard nvidia card.

Is it because very new 9.04? Was it better in 8.10? 

Is there a solution?

Please, help!!!!!!!!!!!!!!!!!:confused:

---

### Post by jaygo on 2009-05-05
Barma,
The issue is with the switch to auto-detecting the displays. I think it's mainly an issue with older hardware, but I'm not sure. Regardless, you need to force X (as in xrandr) to add the resolution you want, and you'll need to edit the xorg.conf file to do this.

First off, though, do you know what refresh your display can handle at 1600x1200? Verify it's max refresh rate for 1600x from the manual or online.

Secondly, are you using the "restricted" nvidia driver? You can check under system > administration > hardware drivers. It will say activated or not.

Copy & paste your /etc/X11/xorg.conf file here for me and we'll go from there.

========= (for later) =========
**Important**: you'll need to actually restart your PC to test the new xorg.conf each time. (For some strange reason, with 8.10 & 9.04 you can create a working xorg.conf that works from the command line but will fail when loaded automatically at boot. So it would test okay until you rebooted, at which point it would fail)

[This page]("http://wiki.debian.org/XStrikeForce/HowToRandR12") has a lot of info on xrandr, which is both the problem and the solution here. Check it out if you need more info.

---

### Post by Barmaleychik on 2009-05-06
Dear Jaygo

Thank you very much for your reply! It is nice to know that people do offer help on Ubuntu forums! Previously I found that many posts are left unanswered (not only mine).

At the moment I have fixed my problem with the screen resolution. The fix was really easy, the difficult part was to find out what to do. The reason why I am putting it here is the hope that someone else may get into a similar problem and despite I am no an expert in Ubuntu by any means I will add my two cents in the common couse I strongly believe - which is open source.

My solution was simply to install nVidia drivers, which I get from sinaptic installer. It took me several attempts to install it since after first three or four tries the driver was not installed (yes, I did restarted X and rebooted the whole machine several times - don't ask me why the drivers were not installed initially); finally it did installed itself and then everything became perfect and everything was working - even my monitor was detected automatically. I do not have to edit my xorg.conf file any more.

Bottom line - the drivers for the video solved the case.

Thanks again,

Barmaley

---

### Post by CatKiller on 2009-05-06
> **jaygo said:**
> I believe ctrl+alt+backspace is disabled by default now. How would you restart x otherwise?

```
sudo /etc/init.d/gdm restart
```

---

### Post by jaygo on 2009-05-11
good news, barmaley. By the way, I usually manage my nvidia driver installation through the "Hardware drivers" section under administration, then all it takes is a reboot.

@catkiller, thx for the tip

---

