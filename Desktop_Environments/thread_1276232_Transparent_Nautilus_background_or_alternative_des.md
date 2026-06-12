---
title: "Transparent Nautilus background or alternative desktop icons?"
date: 2009-09-26
forum: Desktop Environments
---

### Post by valros on 2009-09-26
In the quest for compiz 'wallpapering', Nautilus refuses to cooperate. Without Nautilus drawing the desktop the background is lost, but icons are also lost.

From what I could gather Nautilus must always draw a background colour and will not take to transparency. This of couse overwrites the wallpaper plugin for compiz.

This page [http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199) gives a solution by reinstalling a patched Nautilus but links to non-existent patches.


Right now I'm using just the gnome panels including the file-browser applet, is there any way to restore some...semblance of interactivity with the desktop without Nautilus, some launchers or applets not bound to a gnome panel?

---

### Post by Psyphre on 2009-09-28
i usually prefer my desktop to be empty, so it wouldnt bother me. 

What do you mean by 'interactivity' with the desktop? 

If you mean the files you leave on the desktop, can you not do so via the nautilus file manager?

If you mean shortcuts to applications, you could try installing a dock to hold all those shortcuts for you (if you havent already).

---

### Post by undecim on 2009-09-28
Yes, in order to use Compiz or xscreensaver to draw your background (animated 3d backgrounds can be awesome if your video card will handle it!) you need to give up your desktop icons. There is also the hidden annoyance that if you are copying files while using this setup, you need to keep at least 1 file broswer open or the file transfer will quit.

If you really want your dekstop iconss, you could try an alternate file manager to draw your desktop icons (I think pcmanfm will work for what you need, though I could be wrong...)

EDIT: Yup, I was wrong... pcmanfm has the same problem

---

### Post by undecim on 2009-09-28
After trying out several different desktop icon apps, i've found desktoplaunc, which seems that it will do what you need, with a few caveats:

You can only put launchers on the desktop, not files. (though you can have a launcher to open nautilus to see your home directory)
You need to write the .desklaunchrc file in your home directory to get your icons
You will need to use CCSM to make the desklauncher window both "sticky" and "hidden"

I would give you more information, but its time for me to go to class -- I don't have time to type, lol

I hope that's a good start to what you are looking to do

---

### Post by valros on 2010-01-24
Bump, wondering if there has been any progress or new finds in:

1. Giving Nautilus a transparent background(keeping the icons)

2. An alternative method of displaying files or icons on the desktop that does not require drawing a background(over compiz' background)

---

### Post by wintercorn on 2010-01-28
Yes, there is a way to display icons on the desktop while letting compiz draw the wallpaper. 

You can use the folderview screenlet, which mimics KDE4s folderview plasmoid.
The screenlet displays the content of selected folders on the desktop and you can make the background completely transparent. It isn't a complete nautilus replacement as drag and drop, right click action support etc is only basic but it delivers what you are looking for, including things like thumb previews.

Screenlets are in the repositories, the folderview add-on you can get from [gnome-look]("http://gnome-look.org/content/show.php/Folderview+Screenlet?content=102890").

---

### Post by talora on 2011-08-12
Hi!

About a year and a half later, I'm wondering if there were any changes on this topic. I'm using LinuxMint 11 and really would like to get my desktop icons back - but keep different wallpaper for each virtual desktop.

Thanks!

---

### Post by Bobhuber on 2011-08-13
> **valros said:**
> In the quest for compiz 'wallpapering', Nautilus refuses to cooperate. Without Nautilus drawing the desktop the background is lost, but icons are also lost.

From what I could gather Nautilus must always draw a background colour and will not take to transparency. This of couse overwrites the wallpaper plugin for compiz.

This page [http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199) gives a solution by reinstalling a patched Nautilus but links to non-existent patches.


Right now I'm using just the gnome panels including the file-browser applet, is there any way to restore some...semblance of interactivity with the desktop without Nautilus, some launchers or applets not bound to a gnome panel?
Cairo-Dock along with Screenlets

---

