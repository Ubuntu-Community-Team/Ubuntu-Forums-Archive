---
title: "fluxbox - desktop settings"
date: 2005-06-10
forum: Desktop Environments
---

### Post by byen on 2005-06-10
Hey fellas,
Just installed Fluxbox and  though i find it a little slow...i like it! but have one simple question (embarassingl!)

how do i change my desktop background? is there a help-page for fluxbox? is there a place where i can find how tos?

thank you.

---

### Post by Psquared on 2005-06-10
[QUOTE=byen]Hey fellas,
Just installed Fluxbox and  though i find it a little slow...i like it! but have one simple question (embarassingl!)

how do i change my desktop background? is there a help-page for fluxbox? is there a place where i can find how tos?

thank you.[/QUOTE]

How did you install?? Synaptic??

You need several extras - but for background you need fbsetbg or esetroot. I believe FB can use any image for a background so just use fbsetbg to point to the file you want it to use.

Fluxconf is another program you need which does not get installed by default. You use it to set some basics and file locations for menus and such.

In FB, styles = themes. If you open a theme file there is usually a line which sets the background. You can fiddle with those and point to a different file for a different background.

I hope this helps.

---

### Post by byen on 2005-06-10
Hey Psquared..thnk yu for replying.
I used apt-get function to install FB and it seems to be doing ok! to start off with I tried changing using the following:
fbsetbg [ -fFcCtTaA /home/byen/decor/nova ] [-l] [-h] [-d] [-p]

and i get:
Usage: fbsetbg [-u/-U [wallpapersetter]] [-fFcCtTaA /path/to/wallpaper]
                [-r/-R /path/to/wallpaperdirectory]
                [-b/-B bsetrootoptions] [-l] [-h] [-i] [-p]
Use ``fbsetbg -h'' for a complete help message.


POP UP error - fbsetbg: isnt a existing wallpaper or a valid option.

where am i going wrong?

thank you.

---

### Post by Psquared on 2005-06-10
The best way to figure out the syntax is to use gedit to open up a style file and examine the line which loads the background image or wallpaper. esetroot and fbsetbg have different uses and sometimes one will work where the other won't.

---

### Post by byen on 2005-06-11
googled it and found this!
fbsetbg -f /home/user/pathofimage
tried it and added it to the init file...works now!

thank you for your suggs guys! Go Ubuntu!

---

