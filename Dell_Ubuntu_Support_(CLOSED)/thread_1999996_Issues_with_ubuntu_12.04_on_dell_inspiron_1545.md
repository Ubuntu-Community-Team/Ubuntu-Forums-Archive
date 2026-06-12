---
title: "Issues with ubuntu 12.04 on dell inspiron 1545"
date: 2012-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by phi19 on 2012-06-08
Hey all, I'm new here :P
I've got two computers with a fresh install of Ubuntu 12.04:
- Acer Aspire One D270 netbook, Intel Atom processor, 2 gb ram
- Dell Inspiron 1545 notebook, Intel Core 2 duo processor, 3 gb ram

And I've got the EXACT same issues on both:
- every minute or so, the screen freezes for 3 or 4 seconds. I'm not able to do anything, and everything on the screen stays still. I'm only able to move the cursor, but nothing happens when I click on things.
- booting takes a long time compared to the times when I had ubuntu 10.10
- firefox freezes very randomly, the screen turns grey for a couple of seconds and then comes back to normal. It's very annoying, this didn't happen with 10.10

Any ideas? I don't have a clue :(

Thanks!

[COLOR=Red]EDIT: I've got WUBI on both computers[/COLOR]

---

### Post by SThom27 on 2012-08-29
I realize this is a bit late, but I've got a Dell Inspiron 1545 with the same specs.  Your problem is WUBI.  If you're not just testing out Ubuntu, then never use WUBI.

Best idea?  Partition 50-100 gb for Windows and Ubuntu.  That's 50-100 gb a piece.  Then partition the rest off for shared storage.  You can even handle it from within Windows without needing to reinstall.

After that, everything works perfectly.

---

### Post by gerrman97 on 2012-10-22
or reinstall from a liveCD/download a iso file and use unetbootin to put it on a flash drive. doesnt always work with unetbootin so be careful

---

