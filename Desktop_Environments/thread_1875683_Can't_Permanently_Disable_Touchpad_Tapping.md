---
title: "Can't Permanently Disable Touchpad Tapping"
date: 2011-11-05
forum: Desktop Environments
---

### Post by calelettus on 2011-11-05
I've seen this pop up in the forums repeatedly with no real resolution.

I'm running Lubuntu 11.10 on a Dell Latitude D510. I hate the tapping feature of the touchpad but haven't found a way to permanently disable it.

Currently, I start Lubuntu then open a terminal screen and run:

"gpointing-device-settings"

The terminal window shows: "An X error occurred. The error was BadAtom (invalid Atom parameter)" and the Gpointing window opens.

I click on the AlpsPS/2 Alps button then the "Tapping" tab and see that the "Disable Tapping" button is already checked. 

I have to uncheck, then recheck the button to actually disable tapping. I then close the windows and tapping is disabled for that session only. Every time I restart the computer I have to do the same thing.

How can I make this change permanent and why am i getting the X error? Thanks.

---

### Post by amjjawad on 2011-11-05
Hi there,

If I remember correctly, I've seen that topic/thread somewhere either here or on LXDE Forum. Let me find it and get back to you :)

Please have a look at my signature - Lubuntu One Stop Thread :)

---

### Post by amjjawad on 2011-11-05
I found:

[http://forum.lxde.org/viewtopic.php?f=5&t=119](http://forum.lxde.org/viewtopic.php?f=5&t=119)

You could also search either on google or [www.googlubuntu.com](www.googlubuntu.com)

Please let me know if that was helpful?

---

### Post by kalehrl on 2011-11-05
Have a look at here:

[http://ubuntuforums.org/showpost.php?p=11358701&postcount=7](http://ubuntuforums.org/showpost.php?p=11358701&postcount=7)

---

### Post by glen-shennan on 2011-11-06
Disable Track Pad while Typing

Open /etc/xdg/lxsession/Lubuntu/autostart in your favorite text editor and append the following

```
@/usr/bin/syndaemon -d
```

Adapted from [http://sabiancrash.blogspot.com/2011/10/installing-lubuntu-natively-on-cr48.html]("http://sabiancrash.blogspot.com/2011/10/installing-lubuntu-natively-on-cr48.html")



Alternatively you could make a couple of scripts/shortcuts/something to execute

```
synclient TouchpadOff=2
```              (turn off tapping/scrolling)

```
synclient TouchpadOff=0
```              (all back on)

Hope that helps.

---

### Post by calelettus on 2011-11-06
> **kalehrl said:**
> Have a look at here:

[http://ubuntuforums.org/showpost.php?p=11358701&postcount=7](http://ubuntuforums.org/showpost.php?p=11358701&postcount=7)

This did it, thanks!

---

### Post by amjjawad on 2011-11-06
> **calelettus said:**
> This did it, thanks!

Please mark your thread as Solved if you don't have further Qs :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by calelettus on 2011-11-06
> **amjjawad said:**
> Please mark your thread as Solved if you don't have further Qs :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

Done. By the way amjjawad, although your suggestion did not solve my problem directly I greatly appreciate your Lubuntu One Stop page. It is amazing - filled with a tremendous amount of useful information.

I appreciate the time and effort you have put into it.

---

### Post by amjjawad on 2011-11-06
> **calelettus said:**
> Done. By the way amjjawad, although your suggestion did not solve my problem directly I greatly appreciate your Lubuntu One Stop page. It is amazing - filled with a tremendous amount of useful information.

I appreciate the time and effort you have put into it.

I do appreciate your nice words, that means a lot, thank you but I haven't done much :) actually nothing.
However, I'm so glad you liked my thread and found it helpful. I'm keeping it up to date and adding many stuff daily. Don't forget to bookmark it. Not because it's my thread but because it's really helpful :)

Good luck and if you need anything, let me know please. Even if I can't help directly, I'll show you the way :)

By the way, your thread is in post #3 on my thread ;)

---

