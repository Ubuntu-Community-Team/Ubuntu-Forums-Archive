---
title: "Keyboard shortcuts + compiz. Can't type 'e.'"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Fuzz on 2007-10-27
So I set up my compiz how I like it, and was playing around with the shortcut keys for it (which I was having problems because I wanted to set alt-tab to expo but it wouldn't let me. Then trying to set it back to Super+E, it wouldn't take the super command so it set the shortcut to "e" which was a problem because I got expo every time I tried to type.

So I reset compiz to defaults and set everything back up. Now compiz is set back to Super+E, but when I type 'e' nothing happens. Is there a way to reset this?

Thanks.

---

### Post by stapler123 on 2007-10-27
I did the same thing at one point, I ended up not being able to type my password in at the logon screen because it had the letter I screwed up in it.

 I ended up using ctrl-alt-f1 and logged in to the whole terminal thing that way. Then used dpkg-reconfigure xserver-xorg and using that to load the default keyboard layout.

I'm pretty sure you can do the same thing in gnome by going to "settings" > "Preferences" > "Keyboard" and resetting it to defaults.  You may have to restart the xserver by loggoing out and pressing crtl+alt+backspace

As for setting the compiz shortcuts I find you need to double click on the "Name" column of the action you are trying to edit, and type in the Command you want to use, rather than trying to get it to recognize it automatically.

---

### Post by Fuzz on 2007-10-27
Ok I figured out the keyboard thing couple minutes after I had posted but thanks for the tip on setting the shortcuts, it worked.

---

