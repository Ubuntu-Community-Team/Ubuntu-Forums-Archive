---
title: "'awn-applets-core-bzr'"
date: 2009-02-10
forum: Desktop Environments
---

### Post by Prium on 2009-02-10
I read this article and decided to try it:
[http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html](http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html)

Now AWN has disappeared from my menu! 

I tried 'sudo apt-get remove awn-applets-core-bzr' and this removed the offending software, but despite this I still cannot reinstall AWN. I get this error message:

[B]Cannot install 'avant-window-navigator'

This application conflicts with other installed software. To install 'avant-window-navigator' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/B]

OMG....
What have I done???? 

AWN was pretty cool and now it is gone.....

Plz help!!

---

### Post by kaivalagi on 2009-02-10
A good place to look for help is here: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

Just use intrepid rather than hardy in the sources.list repo settings, e.g.:

```
deb http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu intrepid main
```

---

