---
title: "XGL/Compiz - Screensaver starts while video playing"
date: 2006-06-11
forum: Desktop Environments
---

### Post by reuben on 2006-06-11
I searched the forums for similar, but found only answerless threads, e.g.
[http://ubuntuforums.org/showthread.php?t=178568&highlight=compiz+screensaver](http://ubuntuforums.org/showthread.php?t=178568&highlight=compiz+screensaver)

Basically even while playing videos the screensaver still comes on (actually it is a screenblanker, so everything just goes black) every 20 mins or so. I don't see the setting for the screensaver in the gnome settings, and I have it turned off in KDE settings.

I'm running XGL/Compiz using my .xsession.

Video player is mplayer; the only CLI option I use is -fs ...is there something else I should add to tell it to prevent the screensaver from kicking in?

Thanks

---

### Post by Fafnir on 2006-06-11
[QUOTE=reuben]I searched the forums for similar, but found only answerless threads, e.g.
[http://ubuntuforums.org/showthread.php?t=178568&highlight=compiz+screensaver](http://ubuntuforums.org/showthread.php?t=178568&highlight=compiz+screensaver)

Basically even while playing videos the screensaver still comes on (actually it is a screenblanker, so everything just goes black) every 20 mins or so. I don't see the setting for the screensaver in the gnome settings, and I have it turned off in KDE settings.

I'm running XGL/Compiz using my .xsession.

Video player is mplayer; the only CLI option I use is -fs ...is there something else I should add to tell it to prevent the screensaver from kicking in?

Thanks[/QUOTE]

There should be a hidden folder in your home folder called .mplayer. If there isn't, create it. In the folder, there should be a file called config - you need to add this line to it (create config if it doesn't exist already):

```
stop-xscreensaver=yes
```

Hope that helps!

---

### Post by reuben on 2006-06-12
Thanks for the tip. Unfortunately in this case it didn't help. I'm not sure that it's xscreensaver that's kicking in, as I have that configured to random (and, turned off). The screen just goes blank. Is this something built into XGL? KDE?

---

### Post by reuben on 2006-06-13
*bump*

Anyone? Thanks

---

### Post by schambee on 2006-06-14
i don´t think its the screensaver.
sounds to me like power saving issue........

---

### Post by reuben on 2006-06-14
Yeah, that's what I'm guessing now too (although, the monitor does *not* turn off...it just goes blank). But, in KDE I have power saving turned off. What else might be invoking the power saving? XGL?

---

### Post by lamnk on 2007-09-29
Bump ...

No solution for this problem ? It's quite frustating when i watch a movie and the screensaver jumps out every 15min although i turned it off in gnome.

---

### Post by rg_stephens on 2007-10-01
I've been having the same problem on my HP laptop. The screen would turn off after a few minutes even after I turned this feature off. This is very annoying.  I completely disabled gnome-power-manager only to find out that I could no longer suspend or hibernate :(

I think I finally resolved  the problem. I used the Configuration Editor (gconf-editor from the command prompt) and it lets you tweak a lot of settings. Check the settings under:

/apps/gnome-screensaver/idle_delay

Set this value to zero, or set it to a very high value. 

This will prevent your computer from being considered idle. 

RS

---

### Post by craig_j on 2007-10-02
I don't know if this will work, tis an old "fix" from when I had a similar problem under Fedora.  Try typing:

```
xset s off
```

at a terminal prompt and see if that helps.

Regards,

CJ

---

### Post by rg_stephens on 2007-10-21
This must be a bug in Ubuntu. I can disable screen-saver and screen shutdown, and it stays off for awhile, and then later it comes back again, usually after I bring it back from 'suspend' mode. The screen will power itself down after 10 or 15 minutes of inactivity. 

I hope they fix this. I suppose I could shut down Gnome Power Manager when I watch a movie....

---

### Post by cartisdm on 2007-12-20
> I think I finally resolved the problem. I used the Configuration Editor (gconf-editor from the command prompt) and it lets you tweak a lot of settings. Check the settings under:

/apps/gnome-screensaver/idle_delay

Set this value to zero, or set it to a very high value.

Hopefully this fixes my problem too.  I just did that so I'm going to go back to watching The Office:)

---

### Post by cartisdm on 2007-12-21
Unfortunately that didn't solve my problem:(.  I'm open for suggestions...

---

