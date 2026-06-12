---
title: "What's a good way to get my multimedia keyboard buttons working?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by TeeAhr1 on 2006-06-10
Um...just like the title sez.  FWIW: I've got an HP keyboard, model #5183.

---

### Post by jon_gunnar on 2006-06-10
[QUOTE=TeeAhr1]Um...just like the title sez.  FWIW: I've got an HP keyboard, model #5183.[/QUOTE]
Have you tried **Keyboard Shortcuts**

---

### Post by TOPPEL on 2006-06-10
i've got a wicked keyboard shutcut keyboard.  "MS Digital Media Pro"

if i could assign buttons to all the shortcuts that would be quite a miracle.  i selected us for keyboard i think.  i dont know what its defined as the text installer is as smooth as cake.  my keyboard also has a slide that goes up and down in my browser like a optical mouse scroll wheel.  if i could get that working it would be uber cool.  

collecting .02 centavos

:)

---

### Post by TeeAhr1 on 2006-06-10
[QUOTE=jon_gunnar]Have you tried **Keyboard Shortcuts**[/QUOTE]
No, I'm talking about the "special" buttons on top.

---

### Post by NeghVar on 2006-06-10
The Keyboard Shortcut window doesn't do anything when you assign mulitmedia keys. It recognizes them but they don't do anything outside of that nice little window.

---

### Post by TOPPEL on 2006-06-10
[QUOTE=TeeAhr1]No, I'm talking about the "special" buttons on top.[/QUOTE]

yes i have plenty of those too :)

---

### Post by Viskovitz on 2006-06-10
There's a nice application called KeyTouch ([http://sourceforge.net/projects/keytouch](http://sourceforge.net/projects/keytouch)) which allows you to use almost all those keys, even those on the F-Keys (play, pause [Amarok only], reply, open MyDocs, new Document...). I have a Logitech Access Keyboard and it works very well. :)

---

### Post by TOPPEL on 2006-06-10
how difficult was for you to install ?

its been awhile since i haven't used a package manager to install programs.

---

### Post by jon_gunnar on 2006-06-11
[QUOTE=TeeAhr1]No, I'm talking about the "special" buttons on top.[/QUOTE]
I got a MS Multimedia keyboard and most of the special keys on top is possible to set up via the shortcuts.

---

### Post by TeeAhr1 on 2006-06-12
**jon_gunnar:** Well, I guess chalk up the HP model I've got as one that doesn't seem to fly with Shortcuts.  But I'm gonna note that for later drunken messing with, because there seems to be neat stuff there :) 

Do you what the shortcuts labeled, for instance, "0x76" or "0xa0" correspond to?  I thought it possible that those are the special keys, but it won't respond at all when I try to set one with a special key, nor do the keys appear to do anything now.

**Viskovitz:** I gave KeyTouch a half-assed try with Breezy, but it didn't work "out of the box" and I never put the effort into seeing why not.  Maybe it's time to go back to the drawing board with it :) 

Thanx, all!

---

### Post by frying_fish on 2006-06-12
I would suggest opening xev, and then pressing each key in turn, and seeing what your output is.
If it is something along the lines of this:
```

KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x4c, subw 0x0, time 3396868425, (584,207), root:(604,328),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"

```

Then the key is detected properly, and you just need to get the shortcut set up.  If however it has something that says "NoSym" where the above example has "c", you have an issue that the key is recognised, but not mapped to anything.  You will then need to follow this guide to set them up:

[http://doc.gwos.org/index.php/MultimediaKeys](http://doc.gwos.org/index.php/MultimediaKeys)

After that you should have more success with the keys and shortcuts, I will mention now that the keyboard shortcuts in preferences is useless for most programs, unless they interact with it correctly, so you may need to set some up in gconf, with the apps->metacity section, thats how I got mine working with the program I wanted, hopefully that will be of some help to you.

---

### Post by francf on 2006-06-12
For a graphical and easy solution, use [http://keytouch.sf.net](http://keytouch.sf.net).
Cons: Don't work on USB keyboards, so you need tu use an PS/2 adapter.
Generally included with your keyboard.

---

### Post by Enigmatic on 2006-06-12
I'm wondering if anyone else is having problems with Keytouch becoming unresponsive? It works fine after I install it, but after I rebooted I'd hit the volume key a few times, and then all the media keys wouldn't work. Keytouchd also uses 100% of my CPU power at that stage, and never seems to sort itself out. :(

---

### Post by TeeAhr1 on 2006-06-14
[QUOTE=frying_fish]I would suggest opening xev, and then pressing each key in turn, and seeing what your output is.
If it is something along the lines of this:
```

KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x4c, subw 0x0, time 3396868425, (584,207), root:(604,328),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"

```

Then the key is detected properly, and you just need to get the shortcut set up.  If however it has something that says "NoSym" where the above example has "c", you have an issue that the key is recognised, but not mapped to anything.  You will then need to follow this guide to set them up:

[http://doc.gwos.org/index.php/MultimediaKeys](http://doc.gwos.org/index.php/MultimediaKeys)

After that you should have more success with the keys and shortcuts, I will mention now that the keyboard shortcuts in preferences is useless for most programs, unless they interact with it correctly, so you may need to set some up in gconf, with the apps->metacity section, thats how I got mine working with the program I wanted, hopefully that will be of some help to you.[/QUOTE]
No joy.  Four of the nine are recognized (and actually go somewhere sensible; "web" to firefox, "search" to file search, "mail" to evolution, and "mute" mutes), but the others give no response whatever.  Thanks for the tip, though.

-pete

---

### Post by eaidoido on 2008-05-18
keytouch is amazing! thank you, finally i can use xfce and have the sweet functionality of the hp dv6000 multimedia keys

---

