---
title: "ksysguard applet problem"
date: 2005-07-21
forum: Desktop Environments
---

### Post by chaumurky on 2005-07-21
I don't recall doing anything to cause this but my ksysguard applet now shows nothing but has a little lighning symbol on it and the sensors say 'error'. When I boot up (or try to re-add the panel applet) I get a "Connect Host - KDE Panel" dialogue but I don't know what to put there. Selecting 'daemon' doesn't work. Running the ksysguard application from the kmenu works fine. Can someone give a suggestion as to what might be wrong?

---

### Post by chaumurky on 2005-07-22
hmm, doing :

**rm -f ~/.kde/share/config/ksysguardrc**

and
[B]
rm -r ~/.kde/share/apps/ksysguard[/B]

seemed to fix it. Oh well...  [IMG]http://ubuntuforums.org/images/smilies/eusa_whistle.gif[/IMG]

---

### Post by Trevorius on 2008-05-31
Thanks, this solved my applet issue too!

---

