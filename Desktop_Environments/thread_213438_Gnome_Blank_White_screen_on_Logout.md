---
title: "Gnome Blank White screen on Logout"
date: 2006-07-11
forum: Desktop Environments
---

### Post by xthaparian on 2006-07-11
i get Blank white screen when I logout from the session.

This does not happen when i press CTRL - ALT -BKSPACE

Any suggessions?

---

### Post by Steven_B on 2006-07-21
I had the same problem.  It seems to have gone away after switching from the fglrx X.org driver to the ati driver.  What video card and driver are you using?

---

### Post by Anduu on 2006-07-22
I use the xorg-driver-fglrx driver from the repos and this happes to me every so often...I just ctrl+alt+backspace when the screen goes white and everything comes back.

---

### Post by Steven_B on 2006-07-22
When I Ctrl-Alt-Backspace, it locks up completely.  When I have the white screen, the keyboard responds, and I can type in my username and password.
I was using the 8-26 fglrx driver with an Xpress 200.

---

### Post by Anduu on 2006-07-22
> **Steven_B said:**
> When I Ctrl-Alt-Backspace, it locks up completely.  When I have the white screen, the keyboard responds, and I can type in my username and password.
I was using the 8-26 fglrx driver with an Xpress 200.

I have had nothing but problems using ATIs proprietary driver...everything from poor performance to numerous annoying display issues like locking up on logout.

---

### Post by Steven_B on 2006-07-26
The same thing happens with the 8.24 driver.  I'm not using the 8.25 driver from the repositories, because that crashed almost every time I logged out.
Is there a way to fix this, or do we just deal with it?

---

### Post by Steven_B on 2006-08-16
The same happened with the 8.26 and 8.27 drivers.  [I]I don't know why, but commenting out the lines:
	#Option	    "VideoOverlay" "on"
	#Option	    "OpenGLOverlay" "off"
in xorg.conf seems to have made the problem go away.
Now I have working 3D again! \\:D/[/I]
EDIT: It **isn't** fixed.  It didn't happen for a while, but it's back. :(

---

### Post by ashrack on 2006-08-23
Heres a temporary workaround:
[http://ubuntuforums.org/showpost.php?p=1411811&postcount=3](http://ubuntuforums.org/showpost.php?p=1411811&postcount=3)

And please add the bug report here:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/50535](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/50535)
and also here:
[http://ati.cchtml.com/show_bug.cgi?id=239](http://ati.cchtml.com/show_bug.cgi?id=239)

And hopefully ATI will do something about this bug if we continue to fill those bug reports! Since this BUG is more than half a year old!!!

---

### Post by Christoph.W on 2007-11-16
I know this thread is quite old, and I'm not entirely sure if it's the right place, but I have a similar problem with nVidia:

I recently installed Gutsy on a computer that has an nVidia GeForce 6200 graphics card and installed the proprietary driver using the restricted drivers manager (I never touched xorg.conf manuallly), and enabled compiz desktop effects. Now every time I log out, I get a totally blank white screen, except that I can still see and move the mouse pointer. When I press Ctrl+Alt+Backspace, I can see the desktop wallpaper of the user that was logged in last for a short time, before X restarts and everything is back to normal. Of course, all open sessions that had been managed by GDM are terminated after that.
This is very annoying since that computer is used by other family members who are absolute computer novices, and I'm trying to "encourage" them to make the switch from Windows ...

---

### Post by desertboy on 2007-11-16
Same problem here, can still log in but the screen is completely white except mouse pointer on the switch user screen, only happens after a log lout.

---

### Post by Christoph.W on 2007-11-21
*bump*

---

### Post by EscapeCharacter on 2007-11-23
Hello All,

I have recently installed Gutsy and have had this problem, not with my account, but with my wife's as we both share this machine. I have also have an nVidia cards, a 7600GS. It doesn't happen all the time. Often I come to find the machine in this state once the monitor returns from power saving mode (ie. wakes up). Ctrl-Alt-Bcksp gets resets the display and return me to my gdm login screen.

I hope someone can resolve this along with the other problem I am having with the delay on getting the logout dialog box up after selecting Quit from the System menu.

^]

---

