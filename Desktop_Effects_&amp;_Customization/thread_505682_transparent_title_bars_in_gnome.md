---
title: "transparent title bars in gnome"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by danylong on 2007-07-20
hello i was wondering if it is possible to have a transparent title bar in gnome without beryl or  compiz
i cant install either of these because my video card is unsupported
if you dont understand what i mean by transparent title bar i mean like in the vista theme for beryl found here:
[http://www.beryl-themes.org/content/preview.php?preview=1&id=42875&file1=42875-1.jpg&file2=42875-2.jpg&file3=&name=Vista-Linux](http://www.beryl-themes.org/content/preview.php?preview=1&id=42875&file1=42875-1.jpg&file2=42875-2.jpg&file3=&name=Vista-Linux)

all help is appreciated

---

### Post by marsmissionaries on 2007-07-20
it is not posible.

---

### Post by darrenm on 2007-07-20
Surely your card will do composite?

---

### Post by danylong on 2007-07-20
well i have a nvidia riva tnt2 and ive been told a couple times that it wont run beryl because nvidia doesnt support it anymore
when i have tried to run beryl i get my drivers running and it has a terrible screen resolution and whenever i try to set beryl as the window manager it crashes and goes back to gnome
if you know a way to do it that would be excellent

---

### Post by psyopper on 2007-07-20
Sure it's possible. You can set any image you like as the background for your Gnome tool bar. Just right click on the tool bar, choose Properties and go to the Background tab. Hit the radio button marked "Background Image" and browse to and select your background image. If that image happens to be a .png with transparency it will display it with transparency.

Try it with the attached file. Save it to your desktop and point Gnome to it as I described above.

Have fun!

---

### Post by SuSUntu on 2007-07-20
> **psyopper said:**
> Sure it's possible.


Yep.

> **psyopper said:**
> 
 You can set any image you like as the background for your Gnome tool bar. Just right click on the tool bar, choose Properties and go to the Background tab. Hit the radio button marked "Background Image" and browse to and select your background image. If that image happens to be a .png with transparency it will display it with transparency.


But not as described above. That post offers info about the Gnome panel (referred to as the "tool bar"). The OP was asking about the "title bars" of open application windows.

So ... how you do it  is to run XFWM instead of Metacity as your windows manager. I like XFWM better than Metacity, for a number of reasons, and I think you'll find it nice as well, especially since it can do what was specifically requested in this thread.

Follow these directions to get it running (very easy):

[http://ubuntuforums.org/showthread.php?t=88393](http://ubuntuforums.org/showthread.php?t=88393)

And be sure to see my post #78 which corrects / updates one of the steps for Feisty:

[http://ubuntuforums.org/showthread.php?t=88393&page=8#78](http://ubuntuforums.org/showthread.php?t=88393&page=8#78)

Hopefully you won't run into hardware issues like you did with Beryl ... you shouldn't as XFWM is a much simpler, lighter window manager. The only thing is is that any compositing is going to be more resource / hardware intensive than a windows manager without compositing turned on.

I usually only have XFWM set for transparency on windows that are inactive, but I changed the settings and took a screenshot to show you what things look like with full window decoration transparency on both active and inactive windows. Note the Desktop icons visible through the title bars.

PS:

I can run this setup with the Radeon (non-proprietary) drivers.

---

### Post by psyopper on 2007-07-21
Woops, I stand corrected. Thank's for understanding my misunderstanding and actually giving danylong a good answer! 

I grant you all permission to ignore anything I might say for the next three days...

:)

---

### Post by danylong on 2007-07-21
ok thanks susuntu im installing it now ill post back if i have any problems

---

### Post by danylong on 2007-07-21
thanks so much it works i love it

---

### Post by SuSUntu on 2007-07-21
> **danylong said:**
> thanks so much it works i love it

You're welcome.

---

