---
title: "Tightvnc screwed up Mythbuntu session"
date: 2012-04-23
forum: Desktop Environments
---

### Post by linuxuser21 on 2012-04-23
I'm running Mythbuntu and installed tightvnc server.  I ran tightvnc and after a while, needed to reboot.  Now when Mythbuntu starts up, it goes to the login screen; however, after entering credentials, something crashes and returns to login screen.

When this happened before, I tried removing xfce and reinstalling it, but didn't work and ultimately ended up reinstalling Mythbuntu all together.

I have also tried removing tightvnc server and rebooting to see if that had any effect on it; however, it did  not.

---

### Post by Toz on 2012-04-23
Ctrl-Alt-F1 and login at the text-only screen. Have a look at your ~/.xsession-errors file for a possible clue as to what caused it:
```
cat ~/.xsession-errors
```

---

### Post by linuxuser21 on 2012-04-23
> **Toz said:**
> Have a look at your ~/.xsession-errors file for a possible clue as to what caused it

Okay, ~/.xsession-errors displayed a bunch and some of it went off screen.  Is there a specific part you want me to look at or is there a way to export it so I can display it here and you can take a look at it?

Btw, is there a way to look at the stuff that went off screen?

---

### Post by Toz on 2012-04-23
At the terminal window, type in:
```
pastebinit ~/.xsession-errors
```
...and post back the link that gets generated.

The pastebinit program will upload the contents of your file to paste.ubuntu.com so it can be viewed online. We're looking for error-type messages.

---

### Post by linuxuser21 on 2012-04-23
[http://paste.ubuntu.com/943298/](http://paste.ubuntu.com/943298/)

---

### Post by Toz on 2012-04-23
> xfce4-session: Unable to access file /home/brent/.ICEauthority: Permission denied
Try changing the permissions on this file so that you own it or delete the file (it will be recreated).

---

### Post by linuxuser21 on 2012-04-23
> **Toz said:**
> Try changing the permissions on this file so that you own it

That did it! Thank you so much!:)

```
sudo chmod 777 /home/username/.ICEauthority
```

How exactly did the permissions on that change anyway?

---

### Post by Toz on 2012-04-23
I'm not exactly sure how that changes. I think it may have something to do with using sudo when you should be using gksudo (gksudo for graphical apps), but I haven't been able to confirm this.

For completeness sake, the file should be owned by you with permissions of 600:
```
-rw------- 1 USER USER 4682 2012-04-23 18:44 /home/USER/.ICEauthority
```

Can you mark this thread as Solved from the Thread Tools link above?

---

