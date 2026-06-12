---
title: "Redefining the keyboard - for real this time"
date: 2011-01-25
forum: Desktop Environments
---

### Post by Quchen on 2011-01-25
(Using 10.10)

Hey there,

I've successfully managed to remap my character keys according to my needs (by modifying /usr/share/X11/xkb/symbols/), however I can't seem to be able to change my function keys there. What I'd like to do is redefine the *whole* keyboard, including the ctrl, menu, alt, ... keys. I would especially like to map the menu key to be the right super key. (It's a pity the keyboard preferences menu doesn't provide a "define it yourself" option, but only - in my eyes - pretty useless alternatives)
There are some workarounds on the forums here, but they seem to solve very specific problems such as a stuck super key, or defining the F keys to execute some command, which isn't exactly what I need :\

Thanks in advance,
David


Edit: Thanks to [georgemc's link](http://forums.fedoraforum.org/showthread.php?p=1400641#post1400641) the problem has been solved, see post #5 for my personal rough explanation. (I changed menu to right super)

---

### Post by Quchen on 2011-01-30
... I can't possibly be the only one with that problem :(

---

### Post by Copper Bezel on 2011-01-31
You're not alone, but I don't know that this is really a feature most folks have any need for and I don't know that a solution exists. I'd love for a simple way to make my CapsLock key read as Alt+Left....

I think the solution would be in modifying a custom keyboard layout beyond the options given by the layout itself, not in changing global settings for how the keyboard reads in X11. I don't know how to do that, though, either.

---

### Post by georgemc on 2011-01-31
A little while ago I played around with remapping the "Super Key" in F13.  Since it uses Gnome the principals are the same in U10.04.1.

This is a post on the Fedora forums and may be relevant

[http://forums.fedoraforum.org/showthread.php?p=1400641#post1400641](http://forums.fedoraforum.org/showthread.php?p=1400641#post1400641)

Hope this helps.  Seams like a lot of work.

George

---

### Post by Quchen on 2011-01-31
Hm.
Well in the Keyboard options of Gnome there's the infinitely long menu where you can choose some options for each buttons, which of course doesn't offer a "define stuff yourself" one. Where does that menu manipulate the keys internally? It covers super, caps, ... after all.

Edit: Thanks a lot georgemc, the link you're posted works very well! Goodbye menu key, hello second super key. I don't think I can change th Fn key on a thinkpad though, that'll be my next challenge ... some day.
To sum it up what I've done in case the link doesn't work anymore:
1. Open console, run[FONT=Courier New] xev | grep keysym[/FONT]. This will open a small window that logs your input to the console.
2. Push the function keys you want to change; note down their keycodes (e.g. keycode **167**)
3. Choose a place you want your configuration to be saved. This file has to be run every time you boot, so keep it in some accessible and persistent location. Run [FONT=Courier New]xmodmap -pke > ~/.myKeyboardConfig[/FONT]. This writes your current keyboard map to ~/.myKeyboardConfig.
4. Open the file you've just created with an editor. The lines are sorted by keycodes; now look for the keys you want to change/reassign, and simply switch what stands behind the = with whatever you want the key to do. (In my case I changed "Multi_key Multi_key Multi_key Multi_key" to "Super_R NoSymbol Super_R", mapping another super key to the former menu key.

---

