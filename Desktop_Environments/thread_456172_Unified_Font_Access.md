---
title: "Unified Font Access"
date: 2007-05-27
forum: Desktop Environments
---

### Post by jwiggs on 2007-05-27
Hello,

   I just recently did an installation of Feisty on an Athlon box.  The installation has generally
gone pretty smoothly, and overall I'm very impressed with the distribution after having used
RedHat, Debian, and Gentoo over the years.  It still seems to suffer from some of the same
"discombobulation" on the fonts front as every other distro I've ever used.

   After installation, I found that there was a whole mess of non-english fonts that were put
on the box as part of the default install, despite the fact that US English was the only locale
I enabled during the install.  Any ideas why this should be the case?  More than half of the
fonts in my Gnome font browser are fonts that I'll never use, and they clog up the works.
Does the font installation not pay any attention to the languages/locales requested?

   But the worst problem is one I've seen in every other distribution: access to fonts is *NOT*
unified.  I found the list of "300+ Free Fonts for Ubuntu" and decided to try installing a few of
them.  The first font I installed was the Gentium font:

sudo apt-get install ttf-gentium

   This worked perfectly.  The font shows up in the Gnome Font Browser, it's available in the
font selectors in gedit, OpenOffice, firefox, and even gnome terminal.

   I then installed the "Dustimo" fonts:

sudo apt-get install ttf-dustin

   These did *not* work perfectly.  You can find all of the .ttf files in the normal directory
structure, the were properly cached with fs-cache, etc., but they do *not* show up in the
Gnome Font Browser, or firefox, or the gnome terminal, but the *do* show up in both gedit
and OpenOffice.  WTH?  Can anyone suggest *why* this could be the case?  How is the
Gnome Font Manager determining what to display when you go to "font:///"?  Is it not using
the cache information being maintained by defoma?  Same for firefox!

   Again, I've seen this on every distro I've ever used.  The access to the fonts just doesn't
seem to be consistent across the platform and all applications on it.  Why has this issue
never been dealt with?  What are the technical obstacles preventing it from happening?  Is
there a workaround or global script/command I can run to get things "synced up"?  Any
help would be greatly appreciated.  A pointer to some sort of FAQ or tutorial would be
great, especially since I haven't been able to find one after a *lot* of googling.

best,
Jim

---

### Post by merlinus on 2007-05-27
I agree totally, and thanks for posting this.

You can, however, get rid of all uneeded "other" language fonts by using Synaptic.  Ener "ttf" in the search box, and then mark the ones you do not want (there are 10 or so) for complete removal.

-merlin

---

