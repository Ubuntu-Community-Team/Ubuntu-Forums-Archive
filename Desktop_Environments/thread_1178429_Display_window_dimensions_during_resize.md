---
title: "Display window dimensions during resize?"
date: 2009-06-04
forum: Desktop Environments
---

### Post by 1clue on 2009-06-04
Hi,

I've searched this forum and the web for this bit of information.

I need to be able to see the size of the window during resize.  Does anyone know how to turn this on in Gnome?  I don't care if it's a separate widget or if it's in the window manager itself, but I need this functionality.

I'm a software developer.  I need to be able to test our applications on various screen resolutions.  The dimensions of the screen used to show up in all the old window managers, FVWM2 for example.

The only bit I found on this is a thread discussing the fact that Gnome's spec says the information should be displayed, and that it doesn't, posted back in March.  I know of nothing more recent.

[http://blogs.gnome.org/metacity/2009/03/06/squib-of-the-day-show-size-during-resizing/](http://blogs.gnome.org/metacity/2009/03/06/squib-of-the-day-show-size-during-resizing/)

Any help you can give would be much appreciated.

---

### Post by zhocchao on 2009-06-04
compiz shows the size of the window during resize

---

### Post by 1clue on 2009-06-04
That's a whole different window manager.  Is there something that plugs into Gnome?

My last install, I bucked the trend on everything.  It was a pain in the rear to maintain.  Now I just need a workstation/developer box that can do what I need, so I'd like to leave the pot largely unstirred, if you know what I mean.

---

### Post by zhocchao on 2009-06-04
the only thing i can think of is resizing the window with a small piece of software if you have a few different resolutions e.g. with a/1..2..3.. starter. would this be right?

---

### Post by 1clue on 2009-06-04
I suppose I could use the -geometry=whatever argument for those things started with command line, but that really doesn't cover all my bases.

I wish the Gnome people would realize that this is a really handy feature.

---

### Post by 1clue on 2009-06-11
FWIW, the entire world seems to be fighting against me on this.

Of the applications which claim to support opening to a specific size, few of them seem to pay any attention to the settings.

firefox -height 768 -width 1024 brings up a window of whatever size you used last.  Gnome's specification is that the window size will show up while resizing, but they have not implemented it.

About the only things I use which actually pay attention to requested geometry are gnome-terminal and rdesktop.

---

### Post by allankelly on 2010-08-06
Hi, I also need this. I threw together this little hack that does it for me. It's just an xwininfo loop - runs once to have you click on the window of interest, then reports Height and Width of that window every 1 second until killed.

Cheers, al.

```

akelly@big-blue:~$ cat ~/bin/xwininfo_loop.sh

```
```

#!  /bin/sh
XWINFO=`xwininfo | perl -ne '/Window id: (0x[\da-z]+)/ and print $1'`
echo "#################################"
echo $XWINFO
while [ 1 ]
do
    date
    xwininfo -id $XWINFO | grep 'Width\|Height'
    sleep 1
done

```

---

