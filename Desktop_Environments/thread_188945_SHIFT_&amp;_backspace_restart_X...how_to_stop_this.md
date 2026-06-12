---
title: "SHIFT &amp; backspace restart X...how to stop this?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by mark2741 on 2006-06-04
I thought it was my install of dapper but it turns out that somehow my system is configured to restart x whenever I hold down shift and hit the backspace key. I thought the system was crashing every once in a while whenever I was typing for some odd reason, but then realized it was due to this. I have the habit of hitting the backspace just before releasing the shift key sometimes, so obviously this "feature" is not working for me.

I doubt it is this way by default. My guess is it was enabled during the process I went through while installing compiz/xgl. I got compiz working (I think), but none of the keyboard commands (like switching desktops, etc) worked. But I got the wobbly windows effects and when I manually switched desktops with my mouse I got the effect. But they kind of annoyed me so I don't use it anymore (by enabling "thefuture" in a terminal, per the how-to I followed to install it).

Back to the problem: how do I disable this keyboard shortcut of X restarting every time I hit the shift and backspace combo? I searched google and found this command:


xmodmap /usr/share/xmodmap/xmodmap.us

And that works temporarily - it doesn't work once I reboot. I tried adding sudo to the front of the above statement but that didn't make any difference. So how I do disable this key combo permanently? Incidentally, I tried the 'keyboard shortcuts' list in gnome but restarting x is not listed. I'm on dapper. TIA

---

### Post by grigpi on 2006-06-04
Go to System->Preferences->Session, pick the last tab, click add and enter ```
xmodmap /usr/share/xmodmap/xmodmap.us
```

---

### Post by panurge77 on 2006-06-04
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

add this line into your thefuture script

---

### Post by mark2741 on 2006-06-04
Grigpi - thanks so much, your solution works like a charm!

Since I don't use the compiz thing (I never run the "thefuture" script anymore), I'm not going to bother figuring out where that script is located and how to edit it to include the key change there.

---

### Post by tUrtleAE86 on 2006-06-05
[QUOTE=panurge77]xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
add this line into your thefuture script[/QUOTE]

When i used the suggested solution of changing the keymap to xmodmap.us, i wasn't able to use any of my meta-keys for Compiz shortcuts anymore. But, this worked perfectly for me! Thanks!

---

### Post by funnyguyfunnyguy on 2006-06-08
I need to add this to "thefuturescript." I take it that this means that I don't just type this in the terminal, but rather I need to add it to a file, a la gedit. Where is the script located, and how do I run it one I have added it?

Thanks so much

---

### Post by Sukarn on 2006-06-14
If you installed XGL and Compiz following the instructions at the forum, then you most probably also created a script called "thefuture" in /usr/bin. Hence, its /usr/bin/thefuture
Instructions were given (although not clearly as the english was a bit poor) in the same guide. It was supposed to be launched by this process -
Go to System -> Preferences -> Sessions. Add "/usr/bin/thefuture" in "Startup Programs" (although the guide told you to add it to sessions).

---

