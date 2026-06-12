---
title: "Pressing CANC prints 1 instead ... what's wrong?!?!?"
date: 2011-04-04
forum: Desktop Environments
---

### Post by robitabu on 2011-04-04
This is odd, happens since yesterday only. Everytime I press the CANC key on the keyboard a "1" is printed on the screen instead (well, a 1 character is sent to any active application, even if it's not printed like inside a text editor window, sometimes nothing is printed at all but the normal CANCELLING behaviour of the CANCEL key is not worting anyway).

That's weird, I really don't know what's happening and I'm lost, I can't figure out where to look for.

Any other key is working correctly. I restarted Ubuntu 10.10 and still happens. Strangely enough that happens with my user profile only; on the same machine other users are not experiencing the same prob during their session.

Any advice where to start and find out what's happening?

---

### Post by Krytarik on 2011-04-04
Did you check the settings in "System -> Preferences -> Keyboard"!?

---

### Post by robitabu on 2011-04-04
> **Krytarik said:**
> Did you check the settings in "System -> Preferences -> Keyboard"!?

Shure I did, I also gave a look at Keyboard Shortcuts, nothing there :-(
My keyboard is not listed (Logitech LX710) but worked correctly untill a few days ago without any custom changes done. I don't think I touched anything about the keyboard configuration at all!
Problem is, I use Linux again after a few years I didn't, things are different now, I'm reading there's XKB now ... I don't know how keys are handled now, what's the precise processing logic behind (not to mention the softwares involved in that). Docs look pretty fragmented and inconsistent. If only I knew where to start checking.

---

### Post by Krytarik on 2011-04-04
> **robitabu said:**
> 
My keyboard is not listed (Logitech LX710) but worked correctly untill a few days ago without any custom changes done.
Ah, that were you, I remembered reading another post about the keyboard layout of the Logitech LX710:
[http://ubuntuforums.org/showthread.php?t=1693856](http://ubuntuforums.org/showthread.php?t=1693856)

I tried to figure that time which keyboard model is most similar to those. But obviously, you don't know until you try them. So please do that.

---

### Post by robitabu on 2011-04-04
> **Krytarik said:**
> Ah, that were you, I remembered reading another post about the keyboard layout of the Logitech LX710:
[http://ubuntuforums.org/showthread.php?t=1693856](http://ubuntuforums.org/showthread.php?t=1693856)

I tried to figure that time which keyboard model is most similar to those. But obviously, you don't know until you try them. So please do that.

Right ... that's me.

Anyway, strangely enough ... I went back home, restarted Ubuntu again ... CANC works correctly again O.o   Still, without having done anything! ??? !!! I'd like to know what happened (something must have been happened!) ... who knows.

Thanks anyway, I really hope that doesn't happen again ... Btw I will read on and try to understand how to make a custom profile for my Keyboard in the next future, I'd really like to use more conveniently a few keys and I'd love to see the correct layout appearing in the Ubuntu Keyboard Configuration window :-)

---

### Post by Krytarik on 2011-04-04
> **robitabu said:**
> 
Anyway, strangely enough ... I went back home, restarted Ubuntu again ... CANC works correctly again O.o Still, without having done anything! ??? !!! I'd like to know what happened (something must have been happened!) ... who knows.
Glad to hear that at least for now it works!
> **robitabu said:**
> Thanks anyway, I really hope that doesn't happen again ... Btw I will read on and try to understand how to make a custom profile for my Keyboard in the next future, I'd really like to use more conveniently a few keys and I'd love to see the correct layout appearing in the Ubuntu Keyboard Configuration window
Good luck with that! You should earmark "/usr/share/X11/xkb". I just most recently gathered some experience in remapping individual keys. I turned CapsLock into a real search key. Unfortunately, I didn't manage so far to affect the key also at the console, generally it should work the way I set it up. Also, I didn't manage so far to modify the key system-wide for X incl. GDM, because
1.) GDM apparently doesn't respect any settings made in the "Keyboard" preferences
2.) usual system-wide "/etc/X11/Xmodmap" isn't respected anymore by default, and even running it manually through "/etc/X11/Xsession" doesn't work

Please give notice when you start a thread about your matter, I'm ready to learn more regarding that.

Greetings.

---

### Post by robitabu on 2011-04-04
> **Krytarik said:**
> 
Please give notice when you start a thread about your matter, I'm ready to learn more regarding that.

I will. I think I will flood the forum with those threads :-)

Cheers!

---

