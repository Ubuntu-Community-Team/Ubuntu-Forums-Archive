---
title: "GNOME crashing upon login-in"
date: 2007-05-30
forum: Desktop Environments
---

### Post by michux on 2007-05-30
Yesterday GNOME refused to log me in telling me that the session lasted only 10 seconds and I should take a look at my .xsession-errors file for more info. Clicking OK logged me off. 
This situation occurs every time I log in now. Sometimes it lets me work in spite of this message box -- if I don't clikck OK I can normally work. Sometimes it just logs me off automatically.


One of the strange things I noticed in the error file is this like:
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I uploaded my whole .xsession-error file here: [http://musielak.eu/tmp/.xsession-errors](http://musielak.eu/tmp/.xsession-errors)

Any help will be valueable.

---

### Post by mlind on 2007-05-30
Comment out or remove wacom device entries from your /etc/X11/xorg.conf. Remember to remove wacom references from ServerLayout section too. Make a backup of the file before modifying it.

Thread with similar problem
[http://ubuntuforums.org/showthread.php?p=1762954](http://ubuntuforums.org/showthread.php?p=1762954)

---

### Post by pauljwells on 2007-05-30
Something that can cause this sort of trouble is the clock being set wrong. Check the clock is showing the right time and date and reboot.

---

### Post by michux on 2007-05-30
I checked the time -- it is ok. I removed the wacom section -- the warning is not shown anymore but the message still appears. Here is exactly what it's saying:

```
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
```

I uploaded the news errors file. For some reason it is more verbose now:
[http://musielak.eu/tmp/.xsession-errors-news](http://musielak.eu/tmp/.xsession-errors-news)

BTW: I don't remember changing anything special before this happened. I used Ubunty Feisty for a month now on this PC and it did not cause such errors before.

---

### Post by michux on 2007-05-30
PS. I just tried logging in as a newly created user and this problem does not exist there. So it must be connected with some screwed-up GNOME personal settings. Any ideas where to look for it?

---

### Post by mlind on 2007-05-30
Make a backup of your ~/.gconf folder then relogin to your X session. You might lose some customized preferences you've set in gnome (like desktop shortcuts or panel applet settings), but you can always add these back. This should solve your issue.

```

mv ~/.gconf ~/.gconf_bak

```
Then press CTRL+ALT+Backspace

(If this didn't work, move ~/.gconf_bak to ~/.gconf again)

---

### Post by yann_soub on 2007-06-02
I had exactly the same problem, and moving the .gconf directory did not solve it. But thinking of what I have done just before, I removed the TOMBOY notes manager, which I had just set to be launched at startup. This totally solved my problem. Hope It can help.

---

