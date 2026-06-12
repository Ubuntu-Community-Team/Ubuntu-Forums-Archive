---
title: "nautilus sent for a spin by a simple jpeg..."
date: 2006-11-12
forum: Desktop Environments
---

### Post by stbub on 2006-11-12
All right, looks like things are going from bad to worst.

I disabled gnome-video-thumbnailer entirely (which is bad enough that I have to do this to keep the system usable), but nautilus is also a problem...

The attached jpeg, if visible on the desktop, causes nautilus to use 16% (according to top, and running on a Core 2 Duo!)

If I move the jpeg into a sub-folder such that it no longer is on the desktop, nautilus goes back to sleep.  If I open the sub-folder containing the jpeg, then nautilus wakes up and resume wasting cpu cycles...

:-(

---

### Post by DaveBorealis on 2006-11-12
Where's the attached jpg?  Am I misunderstanding something?

Dave

---

### Post by stbub on 2006-11-12
Actually, the file's too big to be upladed :-(  so much for that...

Maybe its too much for nautilus to deal with a file that is 5013x1813pixels.

Maybe I'll upgrade to a Core 2 quad :-/ that might help with gnome-video-thumbnailer and nautilus going for a spin and never getting anything done...

6.10 rules - not!

---

### Post by DaveBorealis on 2006-11-12
> **stbub said:**
> Maybe its too much for nautilus to deal with a file that is 5013x1813pixels.

That would be my guess.  How large is the file?  It's probably in the megabytes!

---

### Post by stbub on 2006-11-12
Found the problem.  It's a nautilus bug.

Doing the following:

cd ~
rm -rf .thumbnails
ln -s /non/existant/dir .thumbnails

Then open a folder with various videos/images, and watch your CPU usage getting wasted.

It seems that nautilus should not waste time generating thumbnails if it can't write the thumbnails.

(I got in that predicament because I like to keep the thumbnails out of my home directory, so I normally link to a temp area outside of my home directory.  In the process of setting up my new system, I forgot to mkdir the temp area, so the symlink was dead)

---

