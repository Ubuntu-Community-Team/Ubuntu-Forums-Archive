---
title: "transfering bookmarks from windows FF to ubuntu FF"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Rippy on 2006-09-05
Is this possible? I mean, it's firefox on both machines, so I'm wondering if the bookmarks are compatible and if so, where I can find the file to copy over. Thanks!

---

### Post by croak77 on 2006-09-05
Go to Bookmarks -> Manage Bookmarks -> File -> Export. It will export to a html file.

---

### Post by ciscosurfer on 2006-09-05
Yes, the files are compatible (they are simply html documents...well, actually they're xml based, but html files nonetheless)...to find your bookmarks under windows, check this page: [http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile) 

You can then simply copy the bookmarks.html file to a floppy or cdrom or if you have shared networking, drag it to a shared folder or Samba share.  Then, under Ubuntu, in a terminal or nautilus, go to your [COLOR=Red]~/.mozilla[/COLOR] directory, open the firefox directory, then open the next directory (the one with a whole bunch of letters and/or numbers, and copy in your saved bookmarks.html file
I can't tell you how many times I've done this (well, it's a whole bunch) so if you need any further help with this, just let no, I'm happy to help in any way I can!

This page might be helpful as well: [http://mozilla.gunnars.net/firefox_bookmarks_tutorial.html](http://mozilla.gunnars.net/firefox_bookmarks_tutorial.html)

---

### Post by ciscosurfer on 2006-09-05
croak77's suggestion is completely sound and is probably the easiest....just  remember where you save your file when you go to import it!

---

