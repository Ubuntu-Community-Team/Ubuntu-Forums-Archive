---
title: "AAC and Rhythmbox"
date: 2005-05-10
forum: Desktop Environments
---

### Post by REBELinBLUE on 2005-05-10
Sorry if this has been answered before, I searched the forums and didn't get a definative answer, just "got it working" or "couldn't get it working" style posts.

As detailed in section 7.1 at [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) I have installed gstreamer0.8-faad from HOARY-EXTRAS, but when I add a folder containing AAC files to Rhythmbox it still skips them.

Have I missed something? This is one of the reasons I installed Ubuntu rather than waiting a month for the new release of Fedora Core, because the wiki page said it can play AAC files by installing 1 package where as I've never had any luck in FC. 

I know about Beep, XMMS etc, but I want to use Rhythmbox.

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=REBELinBLUE]Sorry if this has been answered before, I searched the forums and didn't get a definative answer, just "got it working" or "couldn't get it working" style posts.

As detailed in section 7.1 at [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) I have installed gstreamer0.8-faad from HOARY-EXTRAS, but when I add a folder containing AAC files to Rhythmbox it still skips them.

Have I missed something? This is one of the reasons I installed Ubuntu rather than waiting a month for the new release of Fedora Core, because the wiki page said it can play AAC files by installing 1 package where as I've never had any luck in FC. 

I know about Beep, XMMS etc, but I want to use Rhythmbox.[/QUOTE]
 Have you tried running gst-register-0.8 ?
It may be needed to let Rhythmbox know about the new plugins.

---

### Post by REBELinBLUE on 2005-05-11
yeh I've tried that :(

---

### Post by REBELinBLUE on 2005-05-11
Figured it out, stupidly simple I'm almost ashamed to say what the problem was 

I was running gst-register-0.8 as root which updates the global registry, now I would have thought that would work but it doesn't. I had to run gst-register-0.8 as the user to update the user registry

Whats the point of the global registry if the user has to maintain their own?

Glad I have it sorted though

---

