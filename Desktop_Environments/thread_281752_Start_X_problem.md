---
title: "Start X problem"
date: 2006-10-21
forum: Desktop Environments
---

### Post by pluisje on 2006-10-21
Hi all,

As a complete Linux noob all went pretty well when I installed it a month ago and I was a bit proud of myself :) .

tonight something went terribly wrong I suppose because i cant reach KDE anymore.

What I did today was an upgrade of my Nvidia driver via the Synaptic manager after adding a extra repository found here on the forums.

Upgrade went well but when I restarded my pc it left me with the standard console (no graphhical interface).

After running "startx" the Nvidia screen comes up but puts me back to the console again with some errors.

Some of the errors I see are:

Error opening /dev/wacom : no such file or directory
(EE) xf860openserial : cannot open device /dev/wacom

and at the end

waiting for X server to shut down FreeFontPath: FPE "usr/share/X11/fonts/misc"
refcount is 2, should be 1; fixing

There is a lot more I suppose but I cant scroll up in the screen and I don't know how I can log this into a file.

I did some searches here and on google but i can't find any solution how to get my Windowmanager back. :( 

Suggestions are very welcome

---

### Post by kidders on 2006-10-21
Hi there,

This kind of thing often happens when you play around with display drivers. Whether your changes will work is always a bit of a shot in the dark. If the driver is misconfigured, mis-installed, or otherwise upset with you, you just wind up with a black screen of death hehe. ](*,)

Something to bear in mind about your X logs is that errors about input devices (such as wacom pens) may always have been reported ... especially if you haven't got one ... so they may have nothing to do with whatever has gone wrong for you. As a general rule, you should never let something tweak your xorg.conf without backing it up first, but I guess it's too late for that, so let's try something else:

Step one is to try to put your xorg.conf back the way it was, so at least X (and then KDE) loads for you. Then visit nvidia's website and see if they tell you how to install their new drivers manually. Specifically, you're interested in ...

[LIST]
[*]Whether the driver really is compatible with your card.
[*]Whether you need to remove references to other driver modules from your xorg.conf, such as DRI or GLX, for instance.
[*]Whether the driver you've installed is really on your computer.
[/LIST]

As you mentioned, X's logs are very verbose. You're mostly interested in lines that start with (EE), which are errors. Mine shows me...

```

$ grep \(EE\) /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

Remember to escape things like brackets (as shown), that have special meanings for **grep**. You might also be interested in the **less** command, which will let you scroll through long things, screen by screen.

**Edit:** The important thing to remember is that you haven't broken anything beyond repair ... you've just sort of thrown yourself in the deep end. Feel free to downsize your xorg.conf, if you see pointless crap in it that's just confusing you. That way, you'll be back in working order before you know it :-)

---

### Post by pluisje on 2006-10-21
hi Kidders.

Thanks for the quick reply.

I had a look in my Xorg.0.log and the most errors were Wacom related and a font path that wasn't there.

I tried to reconfigure Xconf but that also ended up with errors.
After that I had a look into my Xorg.conf.backup and the one I'm running now. I saw lot's of different things between those files :-k :mrgreen: 

Maybe this has been caused by the fact that I was running Gnome first and changed that to KDE after. Also fiddling around with XGL didn't do any good I think :rolleyes: 

So the best thing todo is to reinstall the system I believe.
I have seen this last month more as a trial period. I know what I can do now and what not!

But i like it so far and I will give it a go again :D

---

### Post by kidders on 2006-10-21
Eeeek no ... don't re-install for the sake of one or two lines in a single file!!

---

### Post by davec64 on 2006-10-21
SECONDED!!
 
Don't reinstall!

At this point it has got to be worth trying to fix it. 

Believe me it's the best way to learn, just wait awhile and you'll probably get lots of sugestions on how to fix it.

You never know one might work!

This is certainly the place for help!

---

