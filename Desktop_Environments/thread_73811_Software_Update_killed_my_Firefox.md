---
title: "Software Update killed my Firefox"
date: 2005-10-10
forum: Desktop Environments
---

### Post by Andreas.k on 2005-10-10
Hi everybody,

I installed Ubuntu a few month ago, and everything worked out nicely. I 
perfomed regular updates. Now software update always wants to update
'mozilla-firefox' and 'mozilla-firefox-gnome-support' and fails.
Error message below.
So the result is, I cannot start firefox anymore since I get this warning:
(firefox-bin:22465): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:22465): Gdk-WARNING **: cannot set locale modifiers

afterwards there is only silence.

And I also cannot just remove firefox and reinstall it, since synaptic suggest then to remove the whole desktop which I actually fear to do.

Anybody any smart ideas?

Cheers
Andreas




Preconfiguring packages ...
(Reading database ... 143028 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb

---

### Post by treris on 2005-10-10
In my synaptic list I only have the firefox package installed and not the mozilla-firefox package, i do remember however that I had slightly the same problems when I tried to upgrade from 1.0.6 to 1.0.7
I also had to completely uninstall 1.0.6 and then install 1.0.7 from scratch, but it didn't ask me to if I wanted to uninstall my desktop, then again I'm using kubuntu so that might account for some of the differences.
anyway are you sure that the desktop package its trying to uninstall isnt a dummy package?
I think it might have something to do with the gnome-support package you have installed, can you uninstall that seperately from firefox, then uninstall firefox and then install firefox 1.0.7 and then the gnome-support package again?

I know its a little of a roundabout way, but maybe it'll help you out

---

### Post by jdong on 2005-10-10
Uninstall your firefox and reinstall it. This is a known issue, stemming from a conflict between the unofficial Backports tree and the Ubuntu doc team. It's been sorted out at the source code level, but due to developers frantically working towards Breezy's release, the necessary changes have yet to be migrated to the official Backports tree.


If you need additional info solving this issue, just search up the error, and you'll see plenty of threads about it.

---

### Post by Andreas.k on 2005-10-10
Well ok, just removing and reinstalling worked thanks a lot. So the synaptic problem is solved. Still 'firefox' really doesn't like to start instead complains that it cannot set the local modifiers (see first message). Any Ideas with that?

Cheers
A.

---

