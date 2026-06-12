---
title: "Your opinion: Best File Manager for XFCE"
date: 2005-09-15
forum: Desktop Environments
---

### Post by sameat on 2005-09-15
I run a fairly light system with XFCE, and I love it.  Sometimes I miss desktop icons (I didn't like rox pinboards), but I can deal with that.

My only real complaint is the file manager situation.  I have tried Nautilus, Konqueror, rox, and xffm, and none of them do it for me.  I just don't like nautilus, I don't want to install everything that konqueror needs, xffm seems a little rough around the edges, and I don't really like nested context menus and the "set run action" stuff in rox.

I hate to admit it, but I'm looking for something along the lines of windows explorer circa Windows 95.  It should look and feel fairly polished, and have decent rt click options.

Are there any other good options?  What are your experiences/opinions?

Thanks!
Mark

PS:  I run a light system because I want to, not because I have to.  I'm willing to give up a few clock cycles here and there if I can find the right interface.

---

### Post by gogomon on 2005-09-15
I'm the same situation. I have a light system because of need and love xfce4. I try nautilus on my main comp and it works ok, i'm not really satisfied with it. Nautilus was too simple. konqueror was too many stuff on screen often distracting and specially the lappy i have can only goto 800x600. Like you said xffm its roughf. I too am looking for something like explorer style stuff. Don't know if there is anything even out there.

---

### Post by mctavish on 2005-09-15
check out xfe

---

### Post by psychicdragon on 2005-09-16
Right now there is a new file manager for Xfce in development called thunar. I think it's currently on target for Xfce 4.4 which should be released before the end of the year. It looks a lot like the new browser nautilus in breezy but is a lot faster.

Here's the website: [http://thunar.xfce.org/wiki/](http://thunar.xfce.org/wiki/)
The developers blog: [http://xfce-diary.blogspot.com/](http://xfce-diary.blogspot.com/)

If you want to try it out now, you can. It's not quite ready for real use though.

Add this to your /etc/apt/sources.list :
```
deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main
```
In a terminal :
```
sudo apt-get update
sudo apt-get install thunar
```

---

### Post by sameat on 2005-09-16
Xfe doesn't look too bad...it certainly meets my stated requirements.  I'm going to try it for a little while and see how it feels.

I was going to try Thunar, but there were a few dependancy issues, and it's probably not worth it at this point.  I can wait a couple of months (unless somebody wants to has tips for dealing with:

thunar:
  Depends: libexo0.3-0 (>=0.3.1svn+r17285) but 0.3.0-1ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.8.2) but 1.8.1-0ubuntu2 is to be installed
 Depends: libthunar-vfs-1 but it is not going to be installed
  Depends: libxfce4util-1 (>=4.2.2-1) but 4.2.1-1 is to be installed

Thanks for the help!

---

### Post by aveline on 2005-09-16
[QUOTE=sameat]Xfe doesn't look too bad...it certainly meets my stated requirements.  I'm going to try it for a little while and see how it feels.

I was going to try Thunar, but there were a few dependancy issues, and it's probably not worth it at this point.  I can wait a couple of months (unless somebody wants to has tips for dealing with:

thunar:
  Depends: libexo0.3-0 (>=0.3.1svn+r17285) but 0.3.0-1ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.8.2) but 1.8.1-0ubuntu2 is to be installed
 Depends: libthunar-vfs-1 but it is not going to be installed
  Depends: libxfce4util-1 (>=4.2.2-1) but 4.2.1-1 is to be installed

Thanks for the help![/QUOTE]
 try "Gentoo" (the FM not the distro) & Krusader (very win95/98ish) ...

if you miss norton commander, try midnightcommander.

---

### Post by psychicdragon on 2005-09-17
[QUOTE=sameat]Xfe doesn't look too bad...it certainly meets my stated requirements.  I'm going to try it for a little while and see how it feels.

I was going to try Thunar, but there were a few dependancy issues, and it's probably not worth it at this point.  I can wait a couple of months (unless somebody wants to has tips for dealing with:

thunar:
  Depends: libexo0.3-0 (>=0.3.1svn+r17285) but 0.3.0-1ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.8.2) but 1.8.1-0ubuntu2 is to be installed
 Depends: libthunar-vfs-1 but it is not going to be installed
  Depends: libxfce4util-1 (>=4.2.2-1) but 4.2.1-1 is to be installed

Thanks for the help![/QUOTE]
Sorry, I think you may have to be running breezy. I didn't realize.

Xfe is a good choice if you're looking for something like Explorer. It's a little bit on the ugly side unfortunately.

---

### Post by sameat on 2005-09-17
No worries...I am downloading Breezy to play with.

Xfe seems to be doing the trick, but it is a little on the ugly side, and the maximum file/folder size that it will display is 2 GB, even if there is much more.

I'd love to hack the icons and fix this display issue, but I lack the skills.

Thank for all of the feedback.

---

