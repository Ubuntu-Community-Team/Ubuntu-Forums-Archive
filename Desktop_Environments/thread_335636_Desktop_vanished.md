---
title: "Desktop vanished"
date: 2007-01-10
forum: Desktop Environments
---

### Post by nhaughton on 2007-01-10
I have somehow lost the 'link' to my Gnome desktop. I'm running 6.06, and I upgraded beagle from 0.2.6 to 0.2.9 from the 6.10 repository (main). In so doing I seem to have removed a whole lot of stuff, and as a consequence my desktop has disappeared. The ~/Desktop folder is intact, but the displayed desktop is the usual background with no icons displayed. If I click on say Places/Desktop I get a message box with the message:

Could not open the location file:///home/<name>/Desktop
Details: there is no default application action with this location

I've tried dragging files from a file manager to the 'desktop' but they are refused.

Curiously if I use KDE for my session, the desktop works normally. It's a Gnome thing, it seems.

Can anyone explain what has gone wrong, and what to do to fix it?

TIA

Neil

---

### Post by floke on 2007-01-10
Sounds like your gnome session files are corrupt.
To solve the problem you just need to delete them and Gnome will set you up with new ones when you boot back into it. You'll lose all your old settings, but they've gone now anyway!

The files are in your home folder - I can't remember what they are all called so I'd have a look around the web for repairing gnome sessions - but they include (I think) the files called...

.gconf
.gconfd
.gonme  

etc (basically I think it was just everything listed under .gnome----)

This happened to me once before, with exactly the same symptoms. I deleted the files and all was well. 

Hope this helps

---

### Post by nhaughton on 2007-01-11
Thanks for that - but I can't find those files in my ~.gnome or ~.gnome2 folders. I've googled all over the place but I can't find this kind of information for the current Gnome version, so I'm stumped.

---

### Post by floke on 2007-01-13
Ok,

You can try this:

[http://www.gnome.org/learn/admin-guide/latest/gconf-28.html](http://www.gnome.org/learn/admin-guide/latest/gconf-28.html)

If that doesn't work, then you need to delete the files as above.
They are in your home/[yourname] directory.

The ones to delete are any file that starts with .gnome or .gconf

My home/[me] directory, for instance, has these

.gnome
.gnome2
.gnome2_private
.gconfd
.gconf

so deleting them and logout/login should cause gnome to set them up again from scratch.

This 'should' work!

---

