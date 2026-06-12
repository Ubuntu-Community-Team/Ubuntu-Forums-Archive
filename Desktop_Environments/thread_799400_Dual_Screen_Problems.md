---
title: "Dual Screen Problems"
date: 2008-05-19
forum: Desktop Environments
---

### Post by justfishy on 2008-05-19
So I've been messing with Ubuntu for a while, not using it for anything serious. One of the first things I did was set up my dual screens. I had it perfect and everything was peachy. 

I wanted to customize my desktop a little more so I installed emerald, had to fiddle with it a little bit to work. On the reboot I get the menu bars across both screens, wouldn't normally be a problem, but anything that loads up full screen spans both screens. System popups also come up center of the screens. Backtracking doesn't help. The video card seems to treat the dualies as one screen. A screen shot below for clarification.



[http://i191.photobucket.com/albums/z156/undergroundsilva/Screenshot-1.png]("http://i191.photobucket.com/albums/z156/undergroundsilva/Screenshot-1.png")

---

### Post by abhiroopb on 2008-05-19
Which video card do you have? What did "do" to set up the dual screen? (please be precise)

---

### Post by justfishy on 2008-05-21
I have a Radeon X1300, I used the bigdesktop from this thread, (I think, I did this a while ago)

[http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by justfishy on 2008-05-26
bump

Anyone??

---

### Post by justfishy on 2008-06-04
Bump

---

### Post by 741 on 2008-06-04
I have exactly the same problems. I have an NVidia 7950 GT and used the standard nvidia-settings command, then set it to TwinView. It just stretches a single screen across the two.

I'd like windows to maximize to the screen they're in. Also, popups/dialogs to appear in one screen or another. Lastly, ability to shuffle windows between screens with a hotkey. Fixing any of these problems would be great.

Basically, I'd like to be able to have a separate workspace on each screen. I've looked in a lot of places, but no one seems to have any real solutions. So they'd be appreciated :)

---

### Post by cafe-ristretto on 2008-06-13
dump

Dell D830, nVidia Corporation Quadro NVS 135M, nvidia prop drivers, and using nvidia-settings to get dual screens.  

Maximizing and centering does not happen on primary screen - spans both.  Any ideas?

---

### Post by soccerboy on 2008-06-13
I believe, the stretch is the only way that ubuntu (at the Xorg level) currently deals with dual monitor setup.  You probably have to wait until the next XOrg release before this problem may be in a state to troubleshoot.

---

### Post by cafe-ristretto on 2008-06-13
Thanks for the quick response!!

I used to run Fluxbox (on Gentoo) on this machine.  I wonder if it's possible to run Fluxbox on top of Gnome and get the proper maximizing behavior?

---

### Post by abhiroopb on 2008-06-13
Works for me (7400) try restarting the computer...

---

### Post by soccerboy on 2008-06-13
you can run whatever window manager you want in gnome.
you probably have to run something to the effect of:
metacity --replace
replacing metacity with your window manager of choice.

---

### Post by 741 on 2008-06-13
Enabling Xinerama in the nvidia-settings GUI and restarting my computer after making changes instead of just restarting the X Session seemed to fix the major problems I was experiencing.

All I'd really like with dual screens is a "Send Window to Monitor Left" and "Send Window to Monitor Right" hotkeys, but these are minor complaints.

---

### Post by cafe-ristretto on 2008-06-13
Where do you set xinerama in the nvidia-settings GUI?  Are you meaning Twinview?  And, if you are restarting, are you saving your changes to the xorg.conf file first, and then restarting, as opposed to just choosing the apply button?

I'm starting to wonder if it's a limitation or bug with me GPU - nVidia Corporation Quadro NVS 135M (rev a1)

---

### Post by cafe-ristretto on 2008-06-13
Installed Fluxbox, set up Twinview with nvidia-settings, like I did with Metacity, and maximizing works as expected - it's isolated to the screen.  So, is this a bug with Metacity?

Incidentally, I really like Fluxbox.  But, I like Metacity too.  Dang.

---

### Post by 741 on 2008-06-13
I have it set as separate X Sessions for my (now 3) monitors. There's a checkbox in the main layout settings to "Enable Xinerama." I believe these were the settings that made everything work properly for me, though I'll confess that I was mucking around with enough options that something else might have helped.

I had to save the settings manually which required using the command "gksudo gedit /etc/X11/xorg.conf" (I believe that's the path), then previewing the file that NVidia suggests saving, and copying and pasting that into gedit. I believe I wasn't allowed to save because I wasn't root, but saving manually wasn't substantially more difficult. Then I just restarted the X Session with Alt+Ctrl+Backspace to check problems.

---

### Post by abhiroopb on 2008-06-14
You must save changed to the xorg file. And note DO NOT "merge" changes...this caused me problems later on. Simply set up the monitor using the graphical tools, set which one you want default, and click apply. Then if everything is as it should be, save it the xorg.conf file.

---

