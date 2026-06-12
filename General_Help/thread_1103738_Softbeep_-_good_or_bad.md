---
title: "Softbeep - good or bad?"
date: 2009-03-23
forum: General Help
---

### Post by Sesshomaru on 2009-03-23
Want to stop my system beep coming from my PC.  But I still want a beep, just from my speakers instead.


I found Softbeep, but I also saw that there might be some problems with it.

Anyone using it with Ubuntu?  Anyone encountered any problems? 


I'm using a Creative sound card, just FYI.

Thanks!

---

### Post by Sesshomaru on 2009-03-25
*Bump*

---

### Post by scottuss on 2009-03-25
What events do you want audio alerts for? Gnome provides audio alters via Preferences > Sound. To be honest I disable the PC speaker all together, the beeps are annoying. Especially when pressing backspace when there is no text in a text entry box. Argh!

---

### Post by Sesshomaru on 2009-03-30
> Especially when pressing backspace when there is no text in a text entry box. Argh! 

Yes, this is part of what I want to stop.  I don't want to disable my internal speaker altogether since it is connected much needed diagnostics at startup.


I simply don't want it beeping at me in Ubuntu.  I cannot think of any reason that my internal PC speaker needs to beep when I am using the OS.



So, if not Softbeep, does anyone have any other way of redirecting the PC speaker beep to my sound card and thus my speakers?

Or is Softbeep good/no "crash Ubuntu and make me go grey" stuff?

Thanks!

---

### Post by scottuss on 2009-03-30
If you disable the PC speaker in Linux it will not affect your BIOS POST beep sounds for diagnostics. The speaker itself will not be physically disabled, Linux will just not have the module loaded to use it. That's the best way of doing it I'd say.

---

### Post by Dr Small on 2009-03-30
Try:
```
sudo modprobe -r pcspkr
```

That should disable the pcspkr module, and if it works, you can add that to /etc/modprobe.d/blacklist to make it permanent.

---

### Post by Sesshomaru on 2009-03-30
Thanks scotuss and Dr. Small.

Do you know if there is a way to get the beeps to be channeled through the sound card/speakers instead of the internal speaker?

Thanks!

---

### Post by Sesshomaru on 2009-04-02
*bump*

Still trying to find out if there is a way to get the beeps to be channeled through the sound card/speakers instead of the internal PC speaker?


And if anyone has used Softbeep, I'd appreciate their input on their experience with it.

---

### Post by Dan Again on 2009-04-05
I would like to make the system "beep" come from a specified sound file that I choose...is this possible?

---

