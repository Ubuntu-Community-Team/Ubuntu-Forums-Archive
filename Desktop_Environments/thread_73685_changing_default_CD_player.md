---
title: "changing default CD player"
date: 2005-10-09
forum: Desktop Environments
---

### Post by chipr on 2005-10-09
How do I change the default CD player under KDE?

When I insert a CD, the system launches Konqueror and KsCD.  I don't want it to do that.  I want to launch KAudioCreator (CD ripper) instead.

I've tried going into "Configure Konqueror" -> "File Associations" and changed the media/audiocd setting.  That doesn't seen to affect this.

Any ideas?

---

### Post by mlomker on 2005-10-09
Are you running Breezy?  Breezy has something new in it called ivman.  If you look at /etc/ivman/IvmConfigActions.xml you'll see where it loads kscd.

The problem is that it uses XML configuration files and could be a little tricky to customize.  Here's a [wiki page]("http://ivman.sourceforge.net/") for it.

You could always remove the **ivman** package and go back to how it was in Hoary--no autoplay.

---

### Post by chipr on 2005-10-09
[QUOTE=mlomker]Are you running Breezy?  Breezy has something new in it called ivman.  If you look at /etc/ivman/IvmConfigActions.xml you'll see where it loads kscd.[/QUOTE]

Yes I am, and thanks, this seems to be what just I'm looking for.

---

