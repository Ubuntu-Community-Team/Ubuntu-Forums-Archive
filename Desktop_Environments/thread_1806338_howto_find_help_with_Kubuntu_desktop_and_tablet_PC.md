---
title: "howto find help with Kubuntu desktop and tablet PC"
date: 2011-07-17
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-07-17
I have a Tablet PC with Kubuntu 11.04 installed. I'm need to tinker my X11 and XORG settings, but find little discussion of these efforts in a Kubuntu environment.

What am I supposed to do?
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-08-13
Someone out there must be able to talk with me about XORG configuration files. Please help.

Does it matter if I run KDE (Kubuntu) when I'm tinkering with XORG configuratoin?

Thanks in advance,
~~~ 0;-Dan

---

### Post by Ozymandias_117 on 2011-08-13
It partly depends on your graphics card, what drivers you're using and if you want to mess with a config file or use a GUI program.  If you're not using proprietary drivers and want to use a GUI, go to System Settings -> Display and Monitor -> Size and Orientation

---

### Post by SaintDanBert on 2011-08-14
Thanks for this reply.

I need to do more detailed tinkering.  I read posts that say "... add these lines
to XORG.CONF ..." or similar.  That looks like old-school approach.  I believe that I make edits to files somewhere else that get read and processed during the automatic processing that X11 does when it wakes up. (blush) That is the extent of my understanding and knowledge.

Where is the somewhere that I place files that affect X11's automatic config?

Which files to I place there?

What do the file contents look like?

Where are the file and contents and X11 automatic config documented for mere mortals?

Cheers,
~~~ 0;-Dan

---

### Post by Favux on 2011-08-14
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by SaintDanBert on 2011-08-22
After more reading and searching, I now have numerous X11 and Xorg questions. Where does one go to ask these questions?  Are there forums specific to X11 issues?

There are lots of X11 details that have not changed in years [decades?] and I find numerous items that discuss these dusty details. I continue to wander in a desert where all-things-X11 are concerned.
```

prompt$  Xorg -version

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux mumbles 2.6.32-34-generic-pae #74-Ubuntu SMP Thu Aug 18 19:14:12 UTC 2011 i686

```

Thanks in advance,
~~~ 0;-Dan

---

