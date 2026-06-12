---
title: "Tooltips/Info popup color scheme change"
date: 2007-05-09
forum: Desktop Environments
---

### Post by ectospasm on 2007-05-09
I have been searching, and I can't figure out how to change the default color of the tooltips/mouseover info popups/info balloons/etc.  Right now, I have a dark theme which consists of almost white text foreground with a dark and/or black background.  The tooltip bubbles appear with the new foreground color, but the old light orange background color.  This makes them nearly impossible to read.  I just need to know what gconf setting I can use to change that look.  As far as I can tell, this is the only thing stopping me from using this color scheme.

---

### Post by ectospasm on 2007-05-10
I figured it out.  I had to override the style "clearlooks-tooltips" in .gtkrc-2.0.  Here's the block I used:

```

style "clearlooks-tooltips" = "clearlooks-default"
{
        xthickness = 4
        ythickness = 4
        bg[NORMAL] = { 0,0,0 }
}

widget "gtk-tooltips" style "clearlooks-tooltips"
```

I now have apps that display completely black tooltips;  I'm working on that fix.

EDIT:  I fixed all my tooltips problems.  Logging out and logging back in solved it.

---

### Post by orb9220 on 2007-05-10
> I had to override the style "clearlooks-tooltips" in .gtkrc-2.0. 

Where is that file?

I looked in home and all I see is .gtkrc-1.2-gnome2 file and in it is 
> 
# Autowritten by gnome-settings-daemon. Do not edit

include "/home/orb/.gtkrc.mine"

which of course there is no .gtkrc.mine file that i could fine.

---

### Post by diatribe on 2007-05-10
the .gtkrc file should be in the directory the theme is installed in (/usr/share/themes/theme_name or ~/.themes

---

### Post by orb9220 on 2007-05-11
Thanks bunch

---

### Post by Frem on 2007-05-15
So, to sum it all up, for happy yellow tooltips (In Xubuntu)

Open a terminal, type stuff in:
```
sudo mousepad /usr/share/themes/Clearlooks/gtk-2.0/gtkrc
```

Paste the following at the end of the file:
```

style "clearlooks-tooltips" = "clearlooks-default"
{
        xthickness = 4
        ythickness = 4
        bg[NORMAL] = { 1.0,1.0,0.75 }
}

widget "gtk-tooltips" style "clearlooks-tooltips"
```

Switch to a different theme, than back again. Yellow tooltips. Yay!

The same thing will work for normal Ubuntu, just swap *mousepad* out for *gedit* in the terminal command.

And, for your amusement, the bug thread which lead to the ugly gray tooltips: [link]("http://bugzilla.gnome.org/show_bug.cgi?id=412982").

---

