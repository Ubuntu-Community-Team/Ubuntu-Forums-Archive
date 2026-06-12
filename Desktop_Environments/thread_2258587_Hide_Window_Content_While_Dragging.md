---
title: "Hide Window Content While Dragging"
date: 2014-12-28
forum: Desktop Environments
---

### Post by lukebenes on 2014-12-28
I recently switched from Mint Mate to Lubuntu. Everything feels snappier   except window operations. My ancient video card struggles when I move   windows around. I had setup Mate to only show the outline when  dragging. How can I do this in LXDE?

---

### Post by vasa1 on 2014-12-29
I'm not aware of any means to do what you want :(

I hope someone else has some idea.

[http://comments.gmane.org/gmane.linux.ubuntu.lubuntu.user/13](http://comments.gmane.org/gmane.linux.ubuntu.lubuntu.user/13)
[https://bugzilla.icculus.org/show_bug.cgi?id=3342](https://bugzilla.icculus.org/show_bug.cgi?id=3342)

Also: [Outline resizing/moving windows]("http://crunchbang.org/forums/viewtopic.php?pid=313394#p313394")> I have done some searching, and I don't think this is implemented in Openbox. If you need it you may have to switch to JWM or Fluxbox.

You may want to follow the progress of [ToriOS]("https://lists.launchpad.net/torios/maillist.html"). This yet to be stably released OS will have JWM as the WM.

---

### Post by vasa1 on 2014-12-29
Here's a short review of JWM: [http://crunchbang.org/forums/viewtopic.php?pid=196652#p196652](http://crunchbang.org/forums/viewtopic.php?pid=196652#p196652)> It's especially useful for old slow machines with crummy graphics, especially if you change the window move mode from opaque to outline:

<MoveMode>outline</MoveMode>

Then jwm doesn't redraw the window until you're done moving it. 

---

### Post by lukebenes on 2015-01-04
Joe's Window Manager does the job. Thanks for the help!

---

### Post by mörgæs on 2015-01-04
Please mark the thread 'solved'.

---

