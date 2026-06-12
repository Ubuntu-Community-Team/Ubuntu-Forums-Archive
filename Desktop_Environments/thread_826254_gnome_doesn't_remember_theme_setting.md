---
title: "gnome doesn't remember theme setting"
date: 2008-06-11
forum: Desktop Environments
---

### Post by bstanley on 2008-06-11
Hi!

I am running  Ubuntu 8.0.4 with gnome 2.22.2 and Compiz.

I can reset the theme to one that is different than the default one
but when I reboot, my settings are once again the default theme.

I can change my wallpaper and it remembers that.

I have applied all available updates to the system.

I installed Ubuntu under Windows XP as an application program.

How do I get gnome to remeber by theme settings?

---

### Post by bstanley on 2008-06-13
Hi Folks!

This is not a hard question.

Does anyone know why gnome in Ubuntu 8.0.4 would not remember

your theme settings when you log out?

It keeps going back to the default theme.

---

### Post by bstanley on 2008-06-17
Ok, since I am getting so many responses on this post (NOT),

here's another clue for you all:

         Example --  if I change the gnome theme to 'Darklooks',
                     everything seems to work ok.  The color of the
                     panel bars (top and bottom) turn to the black
                     color that they are suppose to.

                     When I log out and back in, the panel bars have
                     gone back to the default gray color.

Is this a bug in the current gnome release or is there some way to make
all the attributes of the theme stick across logins?

---

### Post by mjbennison on 2008-08-25
The darklooks theme is broken... but it can be fixed. In a terminal enter:[INDENT][FONT=Courier New]gksudo nautilus[/FONT]
[/INDENT]then navigate to [FONT=Courier New]/usr/share/themes/Darklooks/gtk-2.0[/FONT]

You should find a file called [FONT=Courier New]gtkrc[/FONT]. 

Edit this and search for an entry (in  style "clearlooks-tooltips") which reads:[INDENT][FONT=Courier New]bg[NORMAL] = @tooltip_bg_color[/FONT]
[FONT=Courier New]     fg[NORMAL] = @tooltip_fg_color[/FONT]
[/INDENT]Change this to read:[INDENT][FONT=Courier New]bg[NORMAL] = @tooltip[COLOR=Red]s[/COLOR]_bg_color[/FONT]
[FONT=Courier New]     fg[NORMAL] = @tooltip[COLOR=Red]s[/COLOR]_fg_color[/FONT]
[/INDENT]Note all we've done is add the extra 's'. 

Save and exit and then it should be OK. Worked for me anyway... 

See the bug report at [https://bugs.launchpad.net/ubuntu/+source/gnome-themes-extras/+bug/215472](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-extras/+bug/215472) for more.

---

### Post by bstanley on 2008-09-24
Thanks mj!

I had almost given up on this thread.

I applied the changes you suggested and they worked like a champ!


:)

---

### Post by viperdh on 2008-11-18
WOW, I'm running Ubuntu 8.10, installed Darklooks theme and had the same problem, however mine was not saving at all.  Once I had set the theme everything currently loaded would change to it - after that anything loaded would be theme-less

THANK YOU SO MUCH
> **mjbennison said:**
> The darklooks theme is broken... but it can be fixed. In a terminal enter:[INDENT][FONT=Courier New]gksudo nautilus[/FONT]
[/INDENT]then navigate to [FONT=Courier New]/usr/share/themes/Darklooks/gtk-2.0[/FONT]

You should find a file called [FONT=Courier New]gtkrc[/FONT]. 

Edit this and search for an entry (in  style "clearlooks-tooltips") which reads:[INDENT][FONT=Courier New]bg[NORMAL] = @tooltip_bg_color[/FONT]
[FONT=Courier New]     fg[NORMAL] = @tooltip_fg_color[/FONT]
[/INDENT]Change this to read:[INDENT][FONT=Courier New]bg[NORMAL] = @tooltip[COLOR=Red]s[/COLOR]_bg_color[/FONT]
[FONT=Courier New]     fg[NORMAL] = @tooltip[COLOR=Red]s[/COLOR]_fg_color[/FONT]
[/INDENT]Note all we've done is add the extra 's'. 

Save and exit and then it should be OK. Worked for me anyway... 

See the bug report at [https://bugs.launchpad.net/ubuntu/+source/gnome-themes-extras/+bug/215472](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-extras/+bug/215472) for more.
Done the trick

---

### Post by ions on 2008-12-12
I just had the same problem occur.  mjbennison's post fixed it, thanks!

---

### Post by fesghelbahal on 2009-12-06
I have recently installed a ubuntu 9.10. It saved some of the preferences of the previously installed ubuntu. I can change them, but it doesn't save them. i.e when I log out and log in again, it's exactly as the preferences of the llast ubuntu.

It's not just about the theme. I have this problem with background, panel icons and also Pidgin accounts (I should add my accounts to pidgin, after every log in).

This trick didn't even work on the theme.

---

