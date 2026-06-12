---
title: "Horrible problem. I messed up."
date: 2009-03-15
forum: General Help
---

### Post by houseonfire on 2009-03-15
I was trying to install a program, and it told me to type in the directory where i want it to install. I didn't finish the path and accidently had it in my /usr/share folder.
I canceled the install before it finished because it said it was going to delete everything in the folder.
But now my system is messed up. I can't right click anything and theres no top menu bar on any windows.
I'm using nautilus, and heres a screenshot of what it looks like.

[http://i39.tinypic.com/211nfyb.jpg](http://i39.tinypic.com/211nfyb.jpg)

Add/remove programs does not open, and synaptic doesn't have any check boxes.

---

### Post by houseonfire on 2009-03-15
bump

---

### Post by houseonfire on 2009-03-15
bump

---

### Post by alexwilsonphoto on 2009-03-15
Unless you have a backup, you are probably in trouble.

Maybe boot a live-CD, mount your drive and copy the CD's /usr/share to yours?

---

### Post by houseonfire on 2009-03-15
Hm. I'll have to try that.
Is there any way to do a repair type thing?

---

### Post by perlluver on 2009-03-15
It is not polite to bump a thread more than once every 24 hours.  We are all volunteers and don't just sit around waiting to answer questions.  As far as the restore option, other than what was suggested, not really.

---

### Post by orlox on 2009-03-15
Probably if youre missing functionality, something was deleted, and so it couldt be restored so easily. But perhaps something stranger is at work wich has a possible fix. Maybe if you say what were you triyng to install, and if there is a way to see what files that installs, you could manually delete them and see what happens (dont rise your hopes though)

---

### Post by orlox on 2009-03-15
By the way, what are those gmail, weather, feed reader, and mounted devices things on your desktop???? Where did you got those??

---

### Post by perlluver on 2009-03-15
> **orlox said:**
> By the way, what are those gmail, weather, feed reader, and mounted devices things on your desktop???? Where did you got those??

Those are screenlets.  Go to Add/Remove and install screenlets and select the ones you want once it is installed.

---

### Post by houseonfire on 2009-03-16
I booted up into my live disk, and moved all the /usr/share into my usr/share/.
A lot of "could not transfer" errors came up (I was using sudo mv).

I now can right click. And I'm missing my themes, and my checkboxes in symantic don't work still.
Is there a way to "upgrade" my verion to 8.10 (i'm using 8.10) and let it replace all my files, except the files that I created? (Like a system repair type thing)

I tried to install this
[http://lifehacker.com/5169425/calibre-manages-your-e+book-collection](http://lifehacker.com/5169425/calibre-manages-your-e+book-collection)

---

