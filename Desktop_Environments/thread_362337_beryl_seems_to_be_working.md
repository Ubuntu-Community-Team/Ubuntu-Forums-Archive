---
title: "beryl seems to be working"
date: 2007-02-15
forum: Desktop Environments
---

### Post by panti19 on 2007-02-15
i've just installed beryl using this tutorial:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

when i boot into XGL , a white background is shown and the mouse pointer.
the thing is i know beryl is working because if i do the :
ctrl+alt+left(right) ,it switches desktops (still white) in a 3d mode.
how do i fix the whitness?
also, i disabled beryl form being opened at startup, eneterd xgl session adn added the splash screen option.
i started beryl and the splash screen showed up with all its glory, then it switched to the the white i was talking about.

---

### Post by mssever on 2007-02-15
> **panti19 said:**
> i've just installed beryl using this tutorial:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

when i boot into XGL , a white background is shown and the mouse pointer.
the thing is i know beryl is working because if i do the :
ctrl+alt+left(right) ,it switches desktops (still white) in a 3d mode.
how do i fix the whitness?
also, i disabled beryl form being opened at startup, eneterd xgl session adn added the splash screen option.
i started beryl and the splash screen showed up with all its glory, then it switched to the the white i was talking about.

I have had better success with AIGLX instead of XGL. See [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by tronica on 2007-02-15
as mssever said aiglx is better, but if you want to fix the whiteness, run this command


> beryl --use-copy

or

> beryl-xgl --use-copy

to start beryl instead

---

### Post by OHardBodyO on 2007-02-15
That's the same tutorial I used to get my beryl working.  The other tutorial I used didn't work for me at all.

---

