---
title: "USB drive mounted in a folder appearing twice"
date: 2009-03-07
forum: Desktop Environments
---

### Post by politenessman on 2009-03-07
I might be doing something that I'm not supposed to do, but here goes. I have the following set up:
EeePC 900 - 4G/16G SSD - 2G RAM - SSD Card - Eeebuntu Standard 2.0

The Eeebuntu is an Eeepc specific variant of Ubuntu, current version based on intrepid.

I have a large external USB drive that has all of my multimedia content - music, movies, ebook library etc, and I want it mounted in a folder off my desktop, rather than just appearing as a drive, labelled drive.

I've modified the fstab file by adding the following:
/dev/sde1 /home/tonyp/Desktop/media_drive ext2 defaults 0 0

and this gives me what I want. Unfortunatly I also get the drive appearing on the desktop, so in effect it is there twice - I don't want that.

Any ideas on how to prevent the drive from appearing twice?

---

### Post by taurus on 2009-03-07
If you mount it to ~/Desktop, you will get an icon on your desktop.  If you don't want icons on your desktop, run gconf-editor and remove the check mark for volumes_visible in apps -> nautilus -> desktop.

Applications -> Accessories -> Terminal
```
gconf-editor
```

---

### Post by ijustwantyourhalf on 2009-03-09
Hi Politenessman,

I just found out the answer to this very question. If you simply uncheck volumes_visible then any flash drive or camera you plug in won't show up on your desktop and that is no good.

What is really going on is that any drive mounted to any location under your /home/~ will automatically show up on the desktop (and in nautilus sidebars and "Places" menu). If you mount the drive somewhere else though it wont do this.

I made a "music" folder in /opt and mount my drive there.

This is enough if you just want to have your music player look there to build a collection or something (like amarok does)

If you still want to access those files from a folder in your home folder just do a symlink 

> ln -s /opt/music /home/~

Hope that helps.

Don

---

### Post by politenessman on 2009-03-10
That is exactly the info I was looking for, thanks!

---

