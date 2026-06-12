---
title: "Tab Indices In Applications Are Black, hence un-readable"
date: 2012-09-12
forum: Desktop Environments
---

### Post by wkulecz on 2012-09-12
I can't stand using Unity so I'm looking at Xubuntu and LMDE for the future beyond 10.04.  Certainly with the current state of things, waiting for 14.04 in hopes things get better is not totally off the table.

I have to say the LMDE implementation of Xfce looks better and works a lot smoother than does Xubuntu

My problem on Xubuntu 12.04 is that the tab indices in applications are black and hence unreadable in applications like gedit, DevHelp, Glade, etc.  I note the problem also exists in Lubuntu that I've run on the Pandaboard ES.

I've tried different color schemes and themes and all change the look, but none fix the issue :(

Ideas?


The problem does not exist with Xfce on LMDE or Sabayon9. I'm close to eliminating Sabayon9 as it seems generally slower (for example Avidemux2 indexing a 1GB mpeg2 file from a DVD-R takes almost twice as long) and its package manager is very confusing and makes Ubuntu Software Center look good -- I still prefer Synaptic and apt-get.  Sabayon9 and LMDE are attractive for their "rolling" release feature that could greatly simplify my life by evolving systems instead of replacing them every 2-4 years.

These are "appliance" systems and only really need updates as I take advantage of newer libraries or kernel features to improve our custom applications, thus the enormous changes in the UI add no real value, but require retraining of all the users.

I'd like to stay with Ubuntu as although I don't like Unity and find it untenable for my development environment, it may be a simpler and better environment for the dedicated appliance users once I get the next generation applications finished.

---

### Post by Toz on 2012-09-12
> I have to say the LMDE implementation of Xfce looks better and works a lot smoother than does Xubuntu
Interesting. I'm of the opposing opinion.

> Ideas?
Does the problem exist of you use a gtk-3 theme like greybird?

Do you have any files in ~/.config/gtk-3.0 or /etc/gtk-3.0? If so, what are they and what are the contents of those files?

Also, do you have a ~/.gtkrc-2.0 or /etc/gtk-2.0/gtkrc file? 

Perhaps something is overwriting the default settings.

---

### Post by wkulecz on 2012-09-13
> **Toz said:**
> 
Does the problem exist of you use a gtk-3 theme like greybird?


Switching to greybird seems to have fixed it.  Even after switching back to Bluebird and rebooting.

How do I know which are gtk-3 themes?

Most are hideous and/or hard to read.



> Do you have any files in ~/.config/gtk-3.0 or /etc/gtk-3.0? If so, what are they and what are the contents of those files?

Also, do you have a ~/.gtkrc-2.0 or /etc/gtk-2.0/gtkrc file? 

Perhaps something is overwriting the default settings.

I did add a .gtkrc-2.0 file to remove the background color from text on desktop icons, but the problem was on initial install and didn't change with the addition of .gtkrc-2.0.

There is no ~/.config/gtk-3.0 file or directory.

In /etc/gtk-?.0 there are im-multipress.conf files and a settings.ini file in /etc/gtk-3.0.

I've no idea what package put these there.

I'm not sure why trying other "themes" didn't fix the issue before, but I'm just happy its gone now.  There have been a lot of updates between then and now.

---

### Post by Toz on 2012-09-13
> **wkulecz said:**
> Switching to greybird seems to have fixed it.  Even after switching back to Bluebird and rebooting.

How do I know which are gtk-3 themes?

The theme will have a gtk-3.0 directory.

> Most are hideous and/or hard to read.
I'm sorry, I don't understand. Are you saying that most gtk3 themes are hideous and hard to read?

> I did add a .gtkrc-2.0 file to remove the background color from text on desktop icons, but the problem was on initial install and didn't change with the addition of .gtkrc-2.0.
Ok.

> There is no ~/.config/gtk-3.0 file or directory.

In /etc/gtk-?.0 there are im-multipress.conf files and a settings.ini file in /etc/gtk-3.0.

I've no idea what package put these there.
Those are default files - don't worry about them. They are part of the libgtk-3.0 package:
```

$ apt-file search /etc/gtk-3.0/im-multipress.conf 
libgtk-3-0: /etc/gtk-3.0/im-multipress.conf

```
> I'm not sure why trying other "themes" didn't fix the issue before, but I'm just happy its gone now.  There have been a lot of updates between then and now.

At least its fixed.

---

### Post by wkulecz on 2012-09-13
> I'm sorry, I don't understand. Are you saying that most gtk3 themes are hideous and hard to read?

When I first noticed the issue I immediately tried changing themes.  Running Unity 2D or 3D I didn't have the problem, but switching to LxDE on the Pandaboard and Xubuntu on my amd64 immediately showed the issue.  First thing I tried was to change the themes, and most were IMHO god awful color combinations and/or hard to read.  The utilities selecting the themes show no indication as to which are "gtk3" or whatever.

I know people put a lot of effort into these themes, but as long as its not difficult to read I tend to stick to the default unless a quick look at some of the alternatives proves much easier to read.

Greybird seemed to be readable and switching to it and then back to bluebird seems to have cured the problem, so I'm happy now.  Haven't had a chance to see if it'll also work on the Pandaboard, but I recall there were meany fewer themes selections there.

Obviously there is some configuration issue in starting with Unity and them going to LxDE or Xubuntu, sorry I'm not in a position to be of any more help, but at least a work-around is here to be found now.

---

