---
title: "Binding Alt Gr to a new metakey"
date: 2006-06-07
forum: Desktop Environments
---

### Post by toon on 2006-06-07
Hello,

I've been searching a bit around, but haven't quite found the ideal solution to this yet.

First, I'm reading things about how xmodmap is deprecated and that you should use the options in xorg.conf instead. Fair enough, although I'm not sure how in this case. I think I got it acting like the "Alt"-key by adding this in my xorg.conf file: "Option          "XkbOptions" "altwin:meta_alt"".

Next issue (or the real issue:)); My "Alt Gr" button works as it should, generating alternate graphics as it should when held in. However, since I generally have very limited use of it (altgr + 1-9 usually), I'd like to make this work as either "alt + ctrl", as in windows, or as a whole new meta-character similar to alt and ctrl, while AT THE SAME TIME work as "AltGr" if there isn't any other bindings for it. So, let's say if xbindkeys (or the KDE shortcut system, which reports it as a single-key ISO_Level3_Shift now) didn't intercept it, it can work as AltGr. This would be perfect, and I am hoping someone here has the solution for it.. :)

By the way, using said Option in xorg.conf, effectively removes my abilities to type in brackets etc (altgr+1-9), which is not what I want..

Thank you for your time.

---

