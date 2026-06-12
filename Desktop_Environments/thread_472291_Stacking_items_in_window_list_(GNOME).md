---
title: "Stacking items in window list? (GNOME)"
date: 2007-06-12
forum: Desktop Environments
---

### Post by clk99 on 2007-06-12
Quick question:

In GNOME, is there any possible way (setting, 3rd party applet, anything) to have the items in the window list applet stack on top of each other when the panel is a certain size like in KDE and Windows?  Thx

---

### Post by CautionaryX on 2007-06-12
Yes there is, just right click on the window list applet (there should be a bar to the left of it that will allow you to do so) and go to preferences.

Hope that answers your question.

---

### Post by clk99 on 2007-06-12
This is all I see in preferences for the window list:

[[IMG]http://img143.imageshack.us/img143/305/screenshoten3.th.png[/IMG]](http://img143.imageshack.us/my.php?image=screenshoten3.png)

And under the Size tab there's only a couple input boxes for minimum and maximum size.

---

### Post by clk99 on 2007-06-12
Ah, nevermind, I got it figured out, thanks.

But now another question, is it possible to stack application launchers?

---

### Post by CautionaryX on 2007-06-12
Okay, try setting the Windows Grouping option to Always Group Windows. If you have more than one instance of an application open (like firefox or the terminal) it should now stack like the windows list does in WinXP.

---

### Post by clk99 on 2007-06-12
Oh, heh, you may have misunderstood me, what I meant is for the windows to be listed in 2 rows.  Nonetheless, you still helped me find the option, I just wanted to clarify so that my last question made more sense.

---

### Post by clk99 on 2007-06-13
Also, is it possible to set the maximum height of items in the window list (obviously not in the preferences, but maybe somewhere in code)?

---

### Post by clk99 on 2007-06-14
Okay, I answered my own question about the application launchers, I just installed quick-lounge-applet.  But since I'm on a stacking icons frenzy, now I'm wondering if it's possible to have the icons in the notification area shown in multiple rows, too.  Anyone?

---

### Post by ClearBlueSky on 2007-06-20
I was looking to do the exact same thing with the window list listing windows in multiple rows. What exactly did you do that solved this problem?

---

### Post by clk99 on 2007-06-20
> **ClearBlueSky said:**
> I was looking to do the exact same thing with the window list listing windows in multiple rows. What exactly did you do that solved this problem?

```
sudo apt-get install quick-lounge-applet
```Log out and back in, right click panel and add it.  To add icons to it you right click the handle and go to preferences.

---

