---
title: "Yet another xgl snafu"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Steve S. on 2006-06-25
Ok, I knew it was risky, but I tried it anyway.  After trying the Kororaa livecd that uses xgl, I couldn't resist.

I saw this:
[http://www.ubuntuforums.org/showthread.php?p=739758](http://www.ubuntuforums.org/showthread.php?p=739758)  which said to try this:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389).

Then did what it said and opened an xgl session.  Can't really tell a difference...in Kororaa you could hit ctrl+alt then click on the desktop and rotate the window as needed.  None of that here.  One indication that I did something wrong?

Also, and most annoying, every window I open the top of it is out of my screen.  Now, even when I log back into the gnome session I can't see the top of the windows as I open them.  The desktop looks fine, but can't move any windows once I open them 'cause I can't click on the top of it...can't maximize, can only open and close from "File."  Is there another way to do this?

Also, in the gnome session, I look in Windows session and it says there was no settup for "unknown" window manager.  What gives?

Please help!  That top-chopped-off-the-windows thing is hugely annoying and I would love to get xgl up and running!  Thanks.

---

### Post by Steve S. on 2006-06-25
Looked around and saw the same problem here:
[http://www.ubuntuforums.org/showthread.php?t=201998&highlight=top+windows](http://www.ubuntuforums.org/showthread.php?t=201998&highlight=top+windows)

and here:
[http://www.ubuntuforums.org/showthread.php?t=203199&highlight=top+windows](http://www.ubuntuforums.org/showthread.php?t=203199&highlight=top+windows)

Would love to know how to even move the windows, but the alt+click doesn't seem to get it.

Please help!

---

### Post by JoWilly on 2006-06-25
I had this problem yesterday on a fresh install with the latest (at that time) quinn compiz/mesa/xgl packages. (it was working previously)

Updating to a new version of mesa/xlg/compiz released today on the raof repo fixed these problems.

I am using the 64bit versions from the raof repo; but I think new updates should be  hitting (or already have) this 32bit repo too :
[http://www.beerorkid.com/compiz/]("http://www.beerorkid.com/compiz/")

---

### Post by Steve S. on 2006-06-25
> **JoWilly]I had this problem yesterday on a fresh install with the latest (at that time) quinn compiz/mesa/xgl packages. (it was working previously)

Updating to a new version of mesa/xlg/compiz released today on the raof repo fixed these problems.

I am using the 64bit versions from the raof repo said:**
> http://www.beerorkid.com/compiz/[/URL]

Wow...apparently I'm not quite as dapper as you, JoWilly: I have no idea what you said.  I'm using the 32bit on a fresh install, if that matters.

In more laymans terms, would you please tell me how I can fix this problem?

Oh, by the way, on the occasional window that does open somewhere other than the upper corner of my screen, there are no "tops" on them, taskbar, whatever that is called.

---

### Post by JoWilly on 2006-06-25
[quote=Steve S.]Wow...apparently I'm not quite as dapper as you, JoWilly: I have no idea what you said.  I'm using the 32bit on a fresh install, if that matters.

In more laymans terms, would you please tell me how I can fix this problem?

Oh, by the way, on the occasional window that does open somewhere other than the upper corner of my screen, there are no "tops" on them, taskbar, whatever that is called.[/quote] 
Yes, this is the problem I had.

Just add the above repo to your /etc/apt/sources.list file ("sudo gedit /etc/apt/sources.list"), then start synaptic, reload the repo data and do an update... it should update your packages to the latest version. It should then work after an X server restart if the new fixes are already in the repo... they should be there (have not checked the 32bit repos as I'm on 64bit).

Edit:
And make sure you have "gnome-window-decorator" and "compiz --replace gconf" in your gnome startup session (menu/system/preferences/sessions).

---

### Post by Steve S. on 2006-06-26
[QUOTE=JoWilly]Yes, this is the problem I had.

Just add the above repo to your /etc/apt/sources.list file ("sudo gedit /etc/apt/sources.list"), then start synaptic, reload the repo data and do an update... it should update your packages to the latest version. It should then work after an X server restart if the new fixes are already in the repo... they should be there (have not checked the 32bit repos as I'm on 64bit).

Edit:
And make sure you have "gnome-window-decorator" and "compiz --replace gconf" in your gnome startup session (menu/system/preferences/sessions).[/QUOTE]

Thank you much...I'll check it today!

---

### Post by Steve S. on 2006-06-26
Sorry, JoWilly, but I have to ask a couple of more specific questions of you before I do this, just to be safe:

When you say add the above repo to my sources.list, I know how to add stuff, but what line specifically am I to add? Edit: according to the steps in this [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) I've already added that repo to my sources list, yeah?

I know how to start synaptic and use it, but will it list out which repo data you say I should update?  I'll be glad to reload it if I know which one to select for reloading.

Oh, and I'll make sure about the "gnome-window-decorator" and the "compiz --replace gconf".

Again, thanks for the all the advice, just looking for some specifics, if you don't mind...;)

---

### Post by Steve S. on 2006-06-26
I'm aware that I am bombarding everyone with questions but, if (big if) I actually get xgl running, then how do I activate it?  I know in Kororaa you hit ctrl+alt then click drag to rotate desktops, is this the same?  Do I need to format xgl in some way first?  Is there an xgl user manual of some sort or something?  The only stuff that I can find is how to install it, not how to use it.

---

### Post by JoWilly on 2006-06-26
Just click on the link I gave you; everything about how to add the repo to your system is explained there.

Once you have added the repo, you will not need to select anything - it will BE there. Just refresh the repo data with synaptic, update and apply changes.

To setup xgl there are many howtos, just search these forums.

The information in the forum link you gave is a little outdated. Here is what you need.

1. First setup 3d for your gfx card (drivers), and test it to confirm it works.
2. add the repo as per the forum link you posted above, this is good. And install the packages with synaptic.
3. edit /etc/gdm/gdm.conf-custom as per the forum link you posted (but if you are NOT using an ati card, use 0 instead of 1 for the server number (change it on 2 lines). Do not change anyting in /etc/gdm/gdm.conf, no need for this step.
4. Do not make a script to start compiz, only add "gnome-window-decorator" and "compiz --replace gconf" to your gnome session startup apps (menu/system/prefs/sessions).
5. restart the x server.

Nothing more is required.

Edit : yes the commands are the same (ctrl-alt, ctrl-alt-shift, alt-tab, f12, ...)

---

### Post by Steve S. on 2006-06-26
Unfortunately, that didn't get it.  Xgl seems to look cleaner, but nothing is really happening.

And the only way that I have the "tops" of the windows (the part that is right above the "File  Edit" etc, options) is when I run the default gnome session.

So, now do I try to salvage xgl?  If so, how do I check to see what I've done wrong and where to correct it?  If I don't try to salvage, how do I bail out of all this and get the tops of the windows back?  Save this gnome session and go from there?

Please advise.  Until I discovered that I could get the tops back with the default gnome, I was about to scrap the whole thing and reload Dapper.  Please help!

---

### Post by JoWilly on 2006-06-26
I just read in another thread that people are now having this same problem with the updates that appeared in this repo this morning (was working fine yesterday).

So, I guess you need to wait untill updated packages arrive to get this to work.

---

### Post by Steve S. on 2006-06-26
[QUOTE=JoWilly]I just read in another thread that people are now having this same problem with the updates that appeared in this repo this morning (was working fine yesterday).

So, I guess you need to wait untill updated packages arrive to get this to work.[/QUOTE]

Um..allrighty.  But how can I salvage what I have now?  Just make the default gnome as my session every time?

---

### Post by JoWilly on 2006-06-26
[quote=Steve S.]Um..allrighty.  But how can I salvage what I have now?  Just make the default gnome as my session every time?[/quote]

Just comment the lines you have added in /etc/gdm/gdm.conf-custom out (put a "#" in front of each line, this way you can enable it easily after you update the packages).

---

### Post by Steve S. on 2006-06-26
Thanks, jowilly, for the input on the xgl info.  It is very appreciated.

However, that doesn't really fix my problem on this: in the xgl or my standard gnome session, the tops of the windows are gone.  There is some script or other that is doing this because, when I run just the basic gnome session (not the typical default one I have been running) it has the tops of the windows and everything seems to be back to normal.

So, I ask again, how can I fix this problem so that my gnome session that I have been using up to this point returns to normal?

---

### Post by JoWilly on 2006-06-26
[quote=Steve S.]
However, that doesn't really fix my problem on this: in the xgl or my standard gnome session, the tops of the windows are gone.  There is some script or other that is doing this because, when I run just the basic gnome session (not the typical default one I have been running) it has the tops of the windows and everything seems to be back to normal.[/quote] 
I don't understand what you are saying. You have 3 sessions ? basic/normal/xgl ?

Where did you get basic and normal ?

In the xgl steps I gave you , you changed only 2 things to make xgl "work" :

1. edit /etc/gdm/gdm.con-custom
2. add gnome-window-decorator and "compiz --replace gconf" to the gnome session startup apps

So, if you comment out the lines you have added in point 1, your gnome is back to normal (no need to remove anything in point 2, you can keep it there for the next time you run xgl).

Now, if you did anything else previously or added any script to start compiz, I don't know what you did, but it was not needed. So I am afraid you only can help yourself as you alone know what you have done ;)

---

### Post by JoWilly on 2006-06-26
The end of your /etc/gdm/gdm.conf-custom file should look like this once it is commented out (removing the "#" will enable xgl).

```

[servers]
#0=Xgl 

[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer -kb
#flexible=true

```

---

### Post by Steve S. on 2006-06-28
Oh, well, can't figure it out.  It's some script I picked up in the assembly of this xgl thing.

Backed up my data, reinstalled.  No sweat.  Funny how you get better at this stuff the more you do it...;) Added a small windows partition for a dual boot so my efforts weren't waisted.

Thanks anyway, JoWilly.  I'll give it a shot in the future...

---

