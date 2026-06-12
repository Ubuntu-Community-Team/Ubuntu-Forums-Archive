---
title: "Xubuntu/Digital Picture Frame"
date: 2008-10-13
forum: Desktop Environments
---

### Post by thecolorifix on 2008-10-13
I'm trying to take an old laptop that I put Xubuntu on, and turn it into a digital picture frame.

Why is this so amazingly hard to do?

I'm no linux expert so I would be happy if the damn screensaver just turned on, but in Xubuntu it doesnt!

I'm at the end of my rope, I must have looked at every google result for every combination of "xubuntu digital picture frame" 5 times now!

Is there any way to get this to work with less than 15 steps?

 Or can anyone link me to a tutorial that isn't ridiculously complicated?

I'm very frusturated cause I was under  assumption that the screensaver would work in Xubuntu and all I'd have to do for a simple slideshow is leave the computer idle.

Thank you so much for any help, I'm pulling my hair out here.

---

### Post by denham2010 on 2008-10-14
Hi,

XFCE does not come with a default screensaver like Gnome or KDE. You need to install xscreensaver from synaptic.

Cheers.

---

### Post by rmoody on 2008-10-29
This can be done very easily.  First, install feh (it's in the repos) it's a slideshow program.  What I do is have feh run on startup and totally disable the screensaver and power management.  To handle turning the frame off at night, I setup a cron job to force the dpms off: xset dpms force off, later when you want it back on, xset dpms force on.  PM me and I will send you my instructions on how I setup Ubuntu.  I have been working on adapting it for Xubuntu, but it's just not as easy.

---

### Post by thecolorifix on 2008-11-14
I got so frusturated that I gave up for a shile, but in the next few days I'll be back to tackling this and looking for advice.

---

