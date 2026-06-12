---
title: "Blank Screen on Boot (Dell Vostro w/ NVidia 8400M)"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by jsgarvin on 2007-08-08
I just got my new Vostro 1700.  Initially I installed Ubuntu Server Edition and was able to successfully install ubuntu-desktop, gdm, etc, and had it behaving just like a normal computer... with the exception of wireless issues.  But due to the wireless problems, and since it appears my reasoning for choosing Server edition in the first place was mildly flawed, I decided to go back and give Desktop edition a try.

The normal install Desktop edition CD gave me the same tty errors that I see other people having, so I gave the "Alternate" cd a try.  That worked great, right up until the install was complete and the machine reboots for the first time.  During boot, the splash screen comes up, and the progress bar does it's thing and gets all the way to the end, and then.... the screen goes blank.  The hard drive activity indicator still flashes occasionally, but the screen just stays blank.

I'm sure the answer is going to be along the lines of booting into run level 3 and editing my xorg.conf, which I'm comfortable with (won't be my first time)... just curious if someone has seen this before and has some suggestions on what to look for and what to change.  Or maybe there's some other command line command I can run to auto-re-configure the xorg.conf after a text-mode install.

Thanks.

Note again that I didn't have these problems in Server edition.  Maybe I just need to apt-get the latest nvidia drivers in run level 3???

---

### Post by Rocket2DMn on 2007-08-08
Sounds like your X configuration is just bad by default, but that's an easy fix.  Hit CTRL+ALT+F2 to get to a terminal and login.  Rather than fixing xorg.conf manually which hardly ever works, we run the reconfiguration:
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a setup process for your hardware - please read, don't just ENTER your way through - use TAB to move around and SPACEBAR to select/enable.  Select your video driver when asked and on the resolutions page enable your monitor's highest resolution and everything less.  When the configuration is complete, run
```
sudo /etc/init.d/gdm restart
```
Now you should have the GUI.

---

### Post by jsgarvin on 2007-08-08
> **Rocket2DMn said:**
> Hit CTRL+ALT+F2 to get to a terminal and login.  

When? 

I just discovered that I've never booted into runlevel 3 in ubuntu, only Fedora, and my method for doing it in FC doesn't seem to work in Ubuntu (not exactly surprising, I guess).  I tried your suggested CTRL+ALT+F2 both at the blank screen and at the grub OS menu, and neither does anything.

---

### Post by Rocket2DMn on 2007-08-08
F1-F7 are different terminals you are able to access (F7 should be the GUI).  I've also never used runlevel 3 from my Ubuntu laptop, only from my FC5 server.  Try doing CTRL+ALT+F* for F1-F7 and see if you can get to a terminal.  If that doesn't work, try booting into recovery mode from GRUB - this will put you in a terminal as root, you can work from there without needing "sudo".  Try to reconfigure X from there.

---

### Post by jsgarvin on 2007-08-08
> **Rocket2DMn said:**
> F1-F7 are different terminals you are able to access (F7 should be the GUI).  I've also never used runlevel 3 from my Ubuntu laptop, only from my FC5 server.  Try doing CTRL+ALT+F* for F1-F7 and see if you can get to a terminal.  If that doesn't work, try booting into recovery mode from GRUB - this will put you in a terminal as root, you can work from there without needing "sudo".  Try to reconfigure X from there.

Well, CTRL+ALT+F1-7 don't do squat for me.  So I got in through recovery mode and ran it what way.  Still get a blank screen, but I suspect that has something to do with me taking educated guesses on the answers to some of the questions, rather than finding the right ones.  So, when I have some time tonight to really work on it, I'll try again.

Anybody know where to lookup things like refresh rates on laptop monitors???

---

### Post by Rocket2DMn on 2007-08-08
Most laptop screens refresh at 60hz.  If you have any specific questions from the reconfiguration, please don't hesitate to ask, I'd be glad to help out.

---

### Post by jsgarvin on 2007-08-08
Not to spoil the ending or anything but... WHOOHOOO!

Went through the dpkg-reconfigure stuff again in recovery mode, this time making the simplest and most conservative selections on all questions, including selected the 'vesa' video driver instead of 'nv' and this time, it all worked.  Well... good enough for now.

My max resolution is 1024x768 (ugh) and I'll want to switch to the true 'nvidia' driver very soon, but for now... it works... so I know while I screw around with getting it to work how I want it to, this is a good baseline to come back to.  Already backed up my /etc/X11/xorg.conf so I can easily roll back to here as often as necessary.

The first reboot after getting it to work, I got some sort of 'Hal' error dialogue after logging in, and certain network stuff was non-existent.  One more reboot and that cleared right up and easily connected to an open wireless connection in the area.  So, I'm actually typing this on my new Vostro 1700 Laptop, running Ubuntu, and connected to a wireless network.  :mrgreen:

Thanks for the help Rocket!

---

