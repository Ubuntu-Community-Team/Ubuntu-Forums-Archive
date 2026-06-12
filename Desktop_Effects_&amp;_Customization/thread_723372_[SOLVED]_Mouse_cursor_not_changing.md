---
title: "[SOLVED] Mouse cursor not changing"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by DXM31 on 2008-03-13
I downloaded from [http://www.gnome-look.org/](http://www.gnome-look.org/)
Unpacked the file to my desktop
added it to my themes
it shows up in my xcursor selector  system>preferences>cursor selection
but when I select it nothing
I can't even change to any other cursor either
What's up?

---

### Post by rune0077 on 2008-03-13
You also need to tell Compiz that you're using a new cursor (I'm assuming here that you're using Compiz, otherwise ignore this post). Open CCSM and go to General Options. In the first tab there should be something called "Cursor theme", so write the name of your theme here, exactly as it appears in Gnome-appearances. 

This should immediately yield some results. For the change to take full effect, however, you need to log out and back in again (restart X). That ought to do it.

---

### Post by DXM31 on 2008-03-13
> **rune0077 said:**
> You also need to tell Compiz that you're using a new cursor (I'm assuming here that you're using Compiz, otherwise ignore this post). Open CCSM and go to General Options. In the first tab there should be something called "Cursor theme", so write the name of your theme here, exactly as it appears in Gnome-appearances. 

This should immediately yield some results. For the change to take full effect, however, you need to log out and back in again (restart X). That ought to do it.

I keyed it in CCSM but the name doesn't apear in Gnome-apprearance.
It is in Cursor selection.
:confused:

---

### Post by rune0077 on 2008-03-13
In Systen > Preferences, do you not have something called Appearances? f you do, then hit the "Customize" button and you'll find the cursor themes under the "Pointer" tab. Select your theme from here, and make sure that the entry in CCSM is called exactly the same as that (case sensitive).

---

### Post by DXM31 on 2008-03-13
When I rebooted it started working sort of.
When the cursor was over firefox it was the old one.
When outside firefox it was the new one.
I went and changed appreances>custom>pointers and marked it there too
It seems to be working.
Thanks
I will mark this thread closed.

---

