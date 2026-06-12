---
title: "Conky and AWN take forever to load on startup"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by picpak on 2007-11-22
Ok, now that I have a computer fast enough to run Gnome, I've decided to give it a fair shot. However, there's one major problem: any program that I add in System>Preferences>Sessions takes *forever* to load up. So much so, that I forget that they're even supposed to load up, and then all of a sudden Conky and AWN pop up out of nowhere.

Meanwhile, the programs I didn't manually add load up instantly.

Any idea what's going on here?

---

### Post by Six_Digits on 2007-11-22
Having a similar problem with both also. I'm going to try changing the boot priority of the two applications... I'll let you know.

---

### Post by Six_Digits on 2007-11-22
[http://ubuntuforums.org/showthread.php?t=386078](http://ubuntuforums.org/showthread.php?t=386078)

Try the script. Should work.

---

### Post by picpak on 2007-11-22
It didn't work. :( Thanks for trying though!

---

### Post by picpak on 2007-11-23
Turns out the problem is with xfwm4. The latest SVN version makes everything you load on startup take forever to show up. I switched to Openbox and it works perfectly.

---

### Post by Six_Digits on 2007-11-23
What is xfwm4? Window manager for XFCE?

---

### Post by picpak on 2007-11-24
That's exactly it. I followed [this guide](http://ubuntuforums.org/showthread.php?t=610606), except that I forgot to do step 4.

---

