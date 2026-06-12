---
title: "Xubuntu - Sudden problems with how windows are displayed"
date: 2011-08-29
forum: Desktop Environments
---

### Post by George W. Tush on 2011-08-29
The top bar of every window is suddenly missing, along with the minimize/maximize buttons.  The application panel is no longer interacting properly with open windows.  Opening one of the standard games gives me the game, but in a 3" by 5" window which cannot be closed.  

What happened?  How do I fix this?  Thank you.

---

### Post by TransitMan on 2011-08-30
> **George W. Tush said:**
> The top bar of every window is suddenly missing, along with the minimize/maximize buttons.  The application panel is no longer interacting properly with open windows.  Opening one of the standard games gives me the game, but in a 3" by 5" window which cannot be closed.  

What happened?  How so I fix this?  Thank you.

I ran into a similar issue with Linux Mint XFCE. 
Turns out there is a problem with Nautilus. Go to synaptic, uninstall Nautilus, then go to your /home/yourusername folder and delete a folder named .cache

The reboot the computer. When you come back up and open files, browsers and games, the missing title bar should reappear.

---

### Post by thatguruguy on 2011-08-30
> **TransitMan said:**
> I ran into a similar issue with Linux Mint XFCE. 
Turns out there is a problem with Nautilus. Go to synaptic, uninstall Nautilus, then go to your /home/yourusername folder and delete a folder named .cache

The reboot the computer. When you come back up and open files, browsers and games, the missing title bar should reappear.

That's assuming that he has nautilus installed.  It sounds like the xfce window manager crashed, which I've seen happen occasionally on my mythbuntu box.  Open a terminal and type:
```
xfwm4 --replace
```

---

### Post by zapominai on 2011-08-30
> **TransitMan said:**
> I ran into a similar issue with Linux Mint XFCE. 
Turns out there is a problem with Nautilus. Go to synaptic, uninstall Nautilus, then go to your /home/yourusername folder and delete a folder named .cache

The reboot the computer. When you come back up and open files, browsers and games, the missing title bar should reappear.

thanx, this help me.

---

### Post by George W. Tush on 2011-08-30
> **zapominai said:**
> thanx, this help me.

Yes, it helped me, too.  Thanks to all of you for the assistance.  It is much appreciated.  Things are running properly now with XFCE.

Note:  Removing Nautilus removed Ubuntu as a possible interface when logging in.

---

### Post by XubuRoxMySox on 2011-08-30
Two li'l things to help us all out:

OP (original poster) please mark your post as SOLVED so the rest of us who might be having the same problem can find the solution! And...

Please tell us what version of Xubu you're asking about when you ask a question... sometimes the answer for one release doesn't apply in different releases.

Thanks!

---

