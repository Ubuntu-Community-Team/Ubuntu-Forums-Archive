---
title: "gtk-window-decorator --replace freezes the entire system"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by Izkata on 2007-11-08
I can't seem to find this problem already posted in any thread, so...

gtk-window-decorator is freezing up my computer, and I can't figure out why.  If I run "gtk-window-decorator --replace" in a terminal, there isn't even any output - metacity/emerald disappears, then everything except the mouse freezes.  I can't even switch to one of the terminals with CTRL+ALT+F[1-6].  I need to do a hard boot to get out of it.

This morning it was working perfectly.  I don't know what went wrong since then.

I tried reinstalling compiz and libdecoration0 (using Synaptic to remove configuration files, too), and all that happened made it worse - Gnome was defaulting to Compiz Fusion and Emerald, but now it's defaulting to Compiz Fusion and the gtk-window-decorator - so I'm stuck in Fluxbox to do anything.

Any help fixing gtk-window-decorator, or at least making Compiz Fusion start using Emerald as the default window decorator again?

---

### Post by Izkata on 2007-11-09
No help?  Not even changing Gnome/Compiz's default window decorator from Fluxbox?

---

### Post by Izkata on 2007-11-09
Okaaay, it seems to be working fine now, but I have no idea why...

The various things I did since that first post were:

1.  "sudo touch /forcefsck" and reboot - 3 times, I think it was.
2.  Use gconf-editor to change the setting in the Window Decorator plugin to default to "emerald --replace" when there isn't already a window decorator.
3.  Switch to (and log in on) CTRL+ALT+F6 while the GUI was logging in, then running "pkill gtk-window-decorator" after login appeared complete (although all that was visible was the mouse and a black screen.
4.  Trying "gtk-window-decorator --replace --metacity-theme human", which failed since human isn't a theme...  (Well, it's an Ubuntu theme, so I took a guess)

And yet it appears to be working fine right now.

---

### Post by vasilator on 2008-04-09
Hello there.This is my first post ever.I was looking around the net about this problem.I have too.When it happened i had no sound and the sound applications(music players,video players) just freeze.I killed the gtk-window decorator and everything was working fine.Now I'm using beryl emerald as my window decorator.Everything seems to be fine.One question.Where exactly is the Window Decorator plugin in the gconf-editor?Thanks a lot in advance.

---

### Post by mgmiller on 2008-04-19
I recently went through some fun to install and try different window decorators.  One important thing is when issuing the commands to change the decorator, do not run them from a terminal.  Weird things happen if you try to run these from a terminal.

Instead, hit alt/F2 and enter the command in there.

Here is a list of the commands to try switching things around.

Run the commands from alt/F2

To enable metacity/compiz:
  ```
gtk-window-decorator --replace
```

To enable emerald:
  ```
emerald --replace
```

To enable metacity with compiz turned off:
  ```
metacity --replace
```

---

