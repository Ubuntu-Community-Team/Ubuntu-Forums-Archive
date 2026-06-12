---
title: "Is it possible to change ~/Desktop?"
date: 2008-03-16
forum: Desktop Environments
---

### Post by tsaylor on 2008-03-16
I want to change the location of my desktop directory from ~/Desktop to ~/.Desktop so it won't clutter up my home directory.  How would I do this?  I tried searching but "ubuntu Desktop" doesn't return very meaningful results.  Thanks!

---

### Post by Zimmer on 2008-03-16
Well, the Desktop folder contents are what you see on your 'Desktop'... surprise...

You can (which I do) display the contents of your /home  folder as the 'Desktop' by launching the Configuration editor and  Apps>nautilus>preferences and ticking the box 
desktop_is_home_dir

So I guess if you try altering the Desktop folder you might end up in a world of pain...   

only a guess, though


[http://pythonide.blogspot.com/2007/11/how-to-change-or-recreate-your-desktop.html](http://pythonide.blogspot.com/2007/11/how-to-change-or-recreate-your-desktop.html)

[http://www.instructables.com/id/SDFYJ86F9056Z43/](http://www.instructables.com/id/SDFYJ86F9056Z43/)

These blogs seem to think you can...

and some arguments why you should not..
[https://wiki.ubuntu.com/HomeAsDesktop](https://wiki.ubuntu.com/HomeAsDesktop)

---

### Post by kid-pro-quo on 2008-03-17
If you don't want the desktop folder to show up in your home directory create a file ".hidden" in your home directory (if it's not there already) with the contents "Desktop".

This will hide the ~/Desktop folder from nautilus and a fair few other programs (a few ignore it).

I hope that helps.

---

