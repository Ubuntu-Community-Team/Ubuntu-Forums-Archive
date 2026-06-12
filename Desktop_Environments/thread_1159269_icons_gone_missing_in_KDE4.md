---
title: "icons gone missing in KDE4"
date: 2009-05-14
forum: Desktop Environments
---

### Post by vblanton on 2009-05-14
Hey folks, I know there have been a number of threads on this topic, but none of them appear to have any real solutions except for a clean reinstall .. so I'm going to give a try at this too.

Very simply, somewhere along the upgrade path (8.04 to 8.10 i believe), I've lost a bunch of icons in kde (they became generic oxygen "?" icons).  with the recent upgrade to 9.04, nothing has changed.  Attached are screenshots of the examples so that it is really clear what I am talking about.

The screenshots are publically available on my picasaweb album with comments as well : 
[http://picasaweb.google.com/vblanton/KDEAlbum?feat=directlink](http://picasaweb.google.com/vblanton/KDEAlbum?feat=directlink)

---

### Post by vblanton on 2009-05-17
bump. anyone?

Another screenshot example.  This one is the weirdest one. This is noticeable in the above shot of the menu, but here is a closeup. The Kmenu icon has become an arrow with a dot:

---

### Post by mechanic on 2009-05-17
What's in the window Appearance -> System Settings -> Icons?

---

### Post by vblanton on 2009-05-17
Wow, can't believe I didn't spot it before.  Instead of Oxygen, I have "Oxygen Icon Theme for KDE3" and no KDE4 oxygen.  Looks like there is an interesting conflict there.. now I just need to figure out how to get rid of the KDE3 one (it wont let me delete it) and re-install the KDE4 one..

how strange that the KDE3 one would overwrite the KDE4 one...

---

### Post by vblanton on 2009-05-17
o.k., so for anyone else out there. i solved the issue.  It took going to:

".kde/share/icons"

and change the folder named "oxygen" to "oxygen_KDE3".  The conflicting folder name caused my KDE4 setup to load the icons from this folder instead of the correct icons from "/usr/share/icons/oxygen"

Now, in System Settings I have either "Oxygen" icons or "Oxygen for KDE3 icons" as seperate choices.

I can't believe I was using those outdates icons for so long .. i've noticed improved versions of the oxygen icons all over the place.

Thanks for pointing me in the right direction mechanic!

---

### Post by me121 on 2009-06-25
I had to install the kde-icons-oxygen package. This seemed to fix it.

---

