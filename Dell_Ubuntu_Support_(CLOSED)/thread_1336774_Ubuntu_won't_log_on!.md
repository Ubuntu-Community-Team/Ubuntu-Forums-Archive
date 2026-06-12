---
title: "Ubuntu won't log on!"
date: 2009-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skykooler on 2009-11-24
Okay, a few hours ago Ubuntu Karmic installed an update. Nothing happened then, but about twenty minutes ago it started acting weird. I logged out, went to log in (hit the button for my account and typed in my password) and the screen went black, then gave me the splash screen - and then gave me the login screen again.

I tried this with several accounts; same result. I restarted the computer, and was again greeted by an eternal login screen, but this one now gave me an error message, saying that "gnome-power-manager" was corrupted and that I should contact my system administrator. (I am my system administrator.) I then tried logging in with the terminal; this worked flawlessly except I now couldn't use Firefox. I tried the LiveCD, which worked fine. I went back into the installed Ubuntu and typed ```
sudo apt-get --reinstall install gnome-power-manager
```This gave me a few error messages, which I will post once I restart in the installed version. (I'm on a LiveCD.) However, it said it was a successful install, but the problem is still there! 

Can Anybody HELP???

---

### Post by skykooler on 2009-11-24
What exactly it says when I go to log on is:
```
Install Problem!
The comfiguration defaults for GNOME Power Manager have not been installed correctly.
Please contact your system administrator.
```
While reinstalling I get a message saying: 
```
The following packages were automatically installed and are no longer required:
fgfs-base
Use apt-get auto remove to remove them.
```

Then when it get to the install section it says:
```
/usr/bin/mandb: can't write to /var/cache/man/5877: No space left on device
dpkg error processing fgfs-base (--configure):
subprocess installed post-installation script returned error exit status 1
```

Then at the end it says:
```
Errors were encountered while processing
fgfs-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So it seems like fgfs-base is at the heart of this problem. So what is fgfs-base and what can I do about it?

---

### Post by skykooler on 2009-11-25
Well, it seems that fgfs-base is the base files for FlightGear. I had FlightGear at one time and then uninstalled it, so I guess it didn't uninstall completely. How do I get rid of it? I can't seem to find it in the file browser.

---

### Post by skykooler on 2009-11-25
Okay, finally purged fgfs-base. I had to add thirty thousand folders, named "1" to "30000" to get Gnome Power Manager to reinstall without errors. And yet I still can't log in!!? Can somebody Please Help??!!!

---

### Post by teward on 2009-11-25
God, I keep giving the SAME ADVICE to everyone:  This is a MESSAGE BOARD.  It isn't like a chat room where you'll get INSTANT ANSWERS.  Just wait for someone to come around to help you!

---

