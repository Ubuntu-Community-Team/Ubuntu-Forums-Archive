---
title: "persistent install on a stick, with wubi &amp; queasy quagmire"
date: 2009-06-09
forum: General Help
---

### Post by Duckslammer on 2009-06-09
[http://queasyquagmire.wordpress.com/2009/05/10/my-jackalope-jogs-jauntily-again/](http://queasyquagmire.wordpress.com/2009/05/10/my-jackalope-jogs-jauntily-again/)

I have been trying to make a persistent install on a stick using the directions above.  I have done everything he says to do, exactly as he says to do it.  He does leave out a lot of details that took me a few hours to finger out.

When I boot from the stick, the grub menu has two options, both of them "windows (default)".  When I select the first option, the light on my stick blinks for about 10 secs, the screen remains blank, the system recycles and eventually it goes back to the menu.

The second boot option complains about missing windows files.

I have tried every other persistent install listed on the web and most of them boot but aren't really persistent.  This one seems to have promise.

I would be curious if anyone can tell me what I might have done wrong with grub to where it won't boot?  Would it help to post my menu.lst file here?

---

### Post by Mighty_Joe on 2009-09-10
Why not just install Ubuntu directly to the USB drive, sans Wubi?  If you get tired of it, reformat the drive and it's gone (Wubi's great advantage is that if one tires of it, one deletes the file from Windows, no partitions to deal with).
Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") (which covers every other way to install to USB flash drives) on some pointers about doing a full install.

---

