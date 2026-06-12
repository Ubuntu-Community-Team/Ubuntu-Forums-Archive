---
title: "&quot;Save image as&quot; window is too large and partially off the screen"
date: 2012-03-17
forum: Desktop Environments
---

### Post by MetCom45 on 2012-03-17
*SOLVED*

Hi,

I am using Ubuntu 11.10, 32-bit, up to date as of today. 

I have CompizConfig Settings Manager installed.

I am running Firefox 11.0 and whenever I right click on an image>Save image as... The window that pops up is far too large, and it sticks off the right hand side, and the bottom of the screen about an inch or so. Which in turn forces me to drag the window over so I can click "Save".

Can anyone help me figure out how to change the default size of such a pop-up window?

Thank you, very much!

By the way, I'm a cute girl. I figure that will help me in getting this resolved.

EDIT: The same exact issue happens in Chromium. Linked to CompizConfig Settings or Unity possibly??

*SOLVED*

---

### Post by Krytarik on 2012-03-17
> **MetCom45 said:**
> By the way, I'm a cute girl. I figure that will help me in getting this resolved.
So, after more than 3 hours with no response at all for such a simple issue, that doesn't seem to work too great. :P

To solve this, just resize that window; it should be remembered then. ;-)

Regards.

---

### Post by MetCom45 on 2012-03-17
> **Krytarik said:**
> So, after more than 3 hours with no response at all for such a simple issue, that doesn't seem to work too great. :P

To solve this, just resize that window; it should be remembered then. ;-)

Regards.

Haha yeah it didn't work too well, and I'm actually a dude anyway.

I have tried resizing the window, thinking the same thing you did, and it does not save the resized window.

Thanks for the response though, I appreciate it!

---

### Post by Krytarik on 2012-03-17
> **MetCom45 said:**
> Haha yeah it didn't work too well, and I'm actually a dude anyway.
Yeah, I kinda took that possibility into account. :D

> **MetCom45 said:**
> I have tried resizing the window, thinking the same thing you did, and it does not save the resized window.
Damn it, that was used to work that way in Gnome 2 (and I even know where that info is stored), but after testing that myself in both an Oneiric 11.10 and a Precise 12.04 Live ISO, I can confirm that that doesn't work in Gnome 3 so far.

However, judging from that that window isn't really *that* big sized, you must be using a really low resolution, right!?

---

### Post by MetCom45 on 2012-03-18
> **Krytarik said:**
> Yeah, I kinda took that possibility into account. :D



Haha I thought someone might suspect me here :p

> **Krytarik said:**
> 
Damn it, that was used to work that way in Gnome 2 (and I even know where that info is stored), but after testing that myself in both an Oneiric 11.10 and a Precise 12.04 Live ISO, I can confirm that that doesn't work in Gnome 3 so far.

However, judging from that that window isn't really *that* big sized, you must be using a really low resolution, right!?

Yeah haha, that's like the first thing I tried. I really wish it worked!

Haha nope! 1920x1080. The "Save Image As..." window is full sized, 1920x1080, and it's just offset on the screen. About an inch or so right and down.

---

### Post by Krytarik on 2012-03-18
> **MetCom45 said:**
> Haha nope! 1920x1080. The "Save Image As..." window is full sized, 1920x1080, and it's just offset on the screen. About an inch or so right and down.
Yeah, that's definitely *not* the window size I was referring to. :P

Upon googling that matter, I came across this AskUbuntu thread, indicating that the old GTK2 File Chooser configuration file might be pulled:

[http://askubuntu.com/questions/96375/why-are-my-file-selection-dialogs-so-big-how-do-i-make-them-smaller](http://askubuntu.com/questions/96375/why-are-my-file-selection-dialogs-so-big-how-do-i-make-them-smaller)

And that's indeed true, in both Oneiric 11.10 and Precise 12.04, but only for *some* apps, for example, Firefox, Chromium, and LibreOffice - these are the ones I've tested, alongside Gedit.

So either delete the file "~/.config/gtk-2.0/gtkfilechooser.ini" altogether, thus making the concerning apps use the defaults instead, or at least make sure the concerning settings are set to sensible values:
```
[Filechooser Settings]
LocationMode=path-bar
ShowHidden=true
ExpandFolders=false
ShowSizeColumn=true
[COLOR=Blue][B]GeometryX=186
GeometryY=130
[/B][/COLOR][COLOR=Red][B]GeometryWidth=780
GeometryHeight=628
[/B][/COLOR]SortColumn=name
SortOrder=ascending
```The 'GeometryX/Y' settings might have an effect on the positioning in your case, but in mine, Compiz under Lucid 10.04, they are always getting reset to these values - no matter how I set the "Placement Mode" of Compiz' "Place Windows" plugin.

---

### Post by MetCom45 on 2012-03-18
> **Krytarik said:**
> 

So either delete the file "~/.config/gtk-2.0/gtkfilechooser.ini" altogether-

That looks like the exact solution I was looking for.

How do I navigate to the file in which this value is stored? I haven't used Ubuntu thoroughly since 9.10.

I am familiar with using gedit in the terminal to edit values and such, I just don't remember navigation and whatnot very well.

EDIT: Never mind. I have re-familiarized myself. Thank you very much for the help Krytarik, I really do appreciate it!!

Issue solved!

---

### Post by splurben on 2012-06-15
Deleting  "~/.config/gtk-2.0/gtkfilechooser.ini" worked for me.

I've been looking for a fix to this problem for AGES!

Someone should edit the Subject of this post to include "Solved"

---

### Post by fbicknel on 2012-06-15
MetCom45 can do that by select 'mark thread solved' from the Thread Tools link.  I presume the forum monitor/staff folks could do the same.

---

