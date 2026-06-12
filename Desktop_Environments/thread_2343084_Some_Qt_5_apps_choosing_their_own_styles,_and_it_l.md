---
title: "Some Qt 5 apps choosing their own styles, and it looks awful."
date: 2016-11-13
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2016-11-13
Way back when I first joined this forum, I had set up a 16.04 VM with qt5ct and Oxygen style.  Every Qt 5 app used Oxygen, just as configured.

Lately I've noticed that some Qt 5 apps have started choosing their own style.  For example, Konsole now uses Fusion but with a strange yellowish-gray color scheme.  And KUser, when run as root, uses some other weird style.

Other Qt 5 apps, such as Ark and 2048-qt, always use Oxygen style as expected.  And when KUser is run **without** root privileges, it too uses Oxygen style.

Interestingly, KUser does use Oxygen style if it's run like this -
```
sudo kuser
```
But **not** when it's run with [FONT=Courier New]sudo -H[/FONT].


Tried everything I can think of, including [this lot]("https://ubuntuforums.org/showthread.php?t=2327444&p=13503720&viewfull=1#post13503720").  Also commented out the Qt 5 settings override from [FONT=Courier New]56xubuntu-session[/FONT] and stuck the qt5ct setup in [FONT=Courier New]/etc/environment[/FONT].  None of that made any difference here.

This is a Xubuntu machine with XFCE, so access to KDE settings is very limited.  Also, there is no hardware acceleration in the VM.

How to make the qt5ct styling universal again?

---

### Post by T.J. on 2016-11-13
Have you tried using qtconfig for Qt4/Qt5 to force a style? Not all apps are necessarily QT5 yet. Personally, I set them for GTK+ so that XFCE has a unified theme regardless of where the app came from.

---

### Post by &amp;KyT$0P# on 2016-11-13
qtconfig is also set to Oxygen style.  How do I use qtconfig to force a style on Qt 5 apps?

---

### Post by &amp;KyT$0P# on 2016-11-13
It gets weirder.  If I remove qt5ct from the equation, Konsole still uses Fusion style, but the fonts are larger.  Which means it's correctly using my font size settings from qt5ct.

If run -
```
QT_STYLE_OVERRIDE=oxygen konsole
```
then Konsole does use Oxygen style...but the weird color scheme is still there.

KUser is not affected by any of this - in fact, its deciding to use Oxygen style would appear to have nothing whatsoever to do with my settings.

---

### Post by &amp;KyT$0P# on 2016-11-13
Ok so the problem with KUser is that it has become a Qt 4 app.  And root doesn't have my Qt 4 settings.  Fix -
```
sudo cp -v ~/.config/Trolltech.conf /root/.config
```

Now how to get qt5ct to style Konsole properly?

---

### Post by &amp;KyT$0P# on 2016-11-26
bump

Created another VM.  Did a fresh install of Xubuntu 16.04, **not** upgrade the packages.  Added qt5ct, installed konsole, went through all the qt5ct setup... same weird result.

So it appears not to be specific to my VM, nor does it look like the issue was caused by some Ubuntu software update.  What I have not ruled out is an issue with qt5ct itself.

I use the qt5ct from [this PPA]("https://launchpad.net/~hda-me/+archive/ubuntu/qt5ct").  How can I get older/previous versions of that qt5ct?

---

### Post by &amp;KyT$0P# on 2016-11-26
> **halogen2 said:**
> I use the qt5ct from [this PPA]("https://launchpad.net/~hda-me/+archive/ubuntu/qt5ct").  How can I get older/previous versions of that qt5ct?
Still couldn't find that, but I did find source code tarballs of old versions of qt5ct [here]("https://sourceforge.net/projects/qt5ct/files/").  Got it to build after a lot of fiddling about, installing this and that qt5 dev package.  And qt5ct version 0.25 does not have this problem! :D

Thus, my solution will be to remove the PPA and manually install qt5ct version 0.25.

However, I'd like to keep it as a .deb package.  And that PPA used to have a version 0.25 of qt5ct for xenial.

**So how to get the PPA's qt5ct version 0.25?**

If that is not possible, I'd like to build a .deb package myself.  But how would I generate the control files and such, when I don't know the dependencies?

---

### Post by &amp;KyT$0P# on 2016-12-04
bump

---

### Post by &amp;KyT$0P# on 2016-12-09
> **halogen2 said:**
> that PPA used to have a version 0.25 of qt5ct for xenial.

**So how to get the PPA's qt5ct version 0.25?**
Not available from the old builds list, not available in the wayback machine, and no response here... guess there really isn't a way to get that PPA's qt5ct version 0.25 package.

> I'd like to build a .deb package myself.  But how would I generate the control files and such, when I don't know the dependencies?
Should I be starting a new thread somewhere in Development & Programming for this part?

---

### Post by slickymaster on 2016-12-15
> **halogen2 said:**
> <---snip--->

Should I be starting a new thread somewhere in Development & Programming for this part?
Yes. I think that's the way to go.

---

### Post by &amp;KyT$0P# on 2016-12-15
Thanks slickymaster.  Marking this Solved then. :KS


* [https://ubuntuforums.org/showthread.php?t=2346506](https://ubuntuforums.org/showthread.php?t=2346506)

---

