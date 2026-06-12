---
title: "Installation seems too...automated"
date: 2006-03-05
forum: Desktop Environments
---

### Post by B_Stil on 2006-03-05
My first post didn't get any responses so I thought I'd explain the situation a bit more.

I got a fresh copy of the iso from the website and created an installation CD (there should only be one right?).  Then I go through the installation.  Set up my partitions, yadda yadda, everything seems to work fine.  So I sit back and wait....and wait, and wait.  The only input from me the installation program asked was the regional, keyboard, and clock settings.  The rest of the installation was a download off the cd, a reboot, then installation of packages.  Not once did it ask me to set up a root account, just one for a user.  Also, there was nowhere to set up my display or mouse settings.

So after completing installation it fired up GTK, and my mouse didn't work.  I was still able to log in but I couldn't even use the keyboard to select any options.  Afterwards I'm stuck at the desktop with no mouse movement and the only keyboard commands I can execute are CTRL+ALT+F1 and CTRL+ALT+BKSP.  I tried using vim in the console to edit my xorg.conf file but since the system apparently set up an arbitrary root password and didn't bother to let me know what it was, I was pretty much screwed from the beginning.

So here's my question.  Is this a typical Ubuntu 5.10 installation or did I download the wrong ISO?  It seems to me there should be more user input during installation.

---

### Post by OffHand on 2006-03-05
All I can say it is not typical.
Everything worked on my machine right after install.
I'm still a n00b myself tho so I cannot help you.
Goodluck

---

### Post by kaamos on 2006-03-05
Ubuntu encourages the use of sudo over a separate root account. The first user creater will be a member of the "admin" group that has sudo rights. The root account is disabled by default and if you need a root terminal, just type "sudo su".

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-03-05
You're usually not asked what kind of keyboard and mouse because Ubuntu usually detects these--I'm frankly surprised that it didn't!

Nevertheless, you were right-on--press Control-Alt-F1 and log in.
Then type ```
sudo dpkg-reconfigure xserver-xorg
``` and you can specify mouse and keyboard (and monitor).

Ubuntu uses *sudo*, not *root*, so administrative users (like the one you created during the installation process) can temporarily assume root privileges by entering their password and using the *sudo* command.

---

### Post by B_Stil on 2006-03-05
Thanks for the help.  Right after I posted this I saw the wiki on sudo and I can understand why they did it that way.

I tried manually configuring and still no mouse.  Does the fact that it's a USB mouse affect anything?  I don't have another PS/2 mouse to try but the line related to it in my xorg.conf file said "ImPS2" which I think means wheel mouse on PS/2.

---

### Post by aysiu on 2006-03-05
Ubuntu detected my USB mouse just fine. That doesn't mean it will detect *all* USB mice fine. Maybe yours is too new a model?

---

### Post by B_Stil on 2006-03-05
Nope, it's a 6-year-old Logitech Wheel Mouse.  Just two buttons and a wheel.  It's worked with every other Linux distro I've tried so it must be something quirky with Ubuntu.

---

### Post by aysiu on 2006-03-06
My honest opinion, then--don't use Ubuntu.

Hardware detection should be the #1 reason to use a distro. Yes, Ubuntu has simplicity, freedom, free cost, consistent release cycles, and a supportive community, but if a distro doesn't detect your hardware, you're better off using something else.

If Ubuntu didn't detect my hardware, I'd certainly be using Mepis instead.

---

### Post by Jason_25 on 2006-03-06
With all respect, are you serious?  Abandon ubuntu over a mouse?  5-10 bucks for a new mouse is nothing when the os is free.  I encourage you to keep trying ubuntu despite the trouble with your mouse.  BTW, you may need to check the mouse on another system.  I've never heard of something as simple as a mouse not being detected though.  Maybe plug and unplug it a few times to make sure it has a clean connection?

---

### Post by aysiu on 2006-03-06
Well, it's up to the individual user what she finds important.

Personally, I wouldn't buy a new mouse when I already have a mouse. Distros don't very that much when it comes to day-to-day use, really.

If someone's really dedicated to using Ubuntu, she may think it a worthy investment to ditch her old mouse for a new one, but if someone's not dedicated to using Ubuntu, I don't see any reason for her to stick with it if another distro will detect the mouse straight out.

---

