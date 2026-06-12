---
title: "lost home folder since partial upgrade"
date: 2011-11-21
forum: Desktop Environments
---

### Post by wonkyhonky on 2011-11-21
Hello everyone, (or anyone)

apologetic preamble: I'm new, green and usually confused: it comes with being an artist not a tekkie :D so I'm sorry if I make you despair with bad etiquette and stoopit statements. But i learn fast... 

The problem: Not entirely sure as my knowledge of the system isn't up to much yet.

I know I run 64 bit Ubuntu 11.04

I accidentally clicked yes to a partial upgrade yesterday, and now my desk top is sort of screwed. The launch bar on the only shows the basic fresh install software. I know the rest is still there as it comes up and can be run when I go via the super key.

External devices aren't being recognised properly. I have an avant window navigator and external drives appear in that, but when I click, they don't launch or open.

All the 'places' fail to launch when clicked ie Home, desktop, trash etc. 

Right click on desktop no longer works.

It gives the appearance of having lost all my files and folders (which really scared me for a bit!) but when I opened up thunderbird email to attach a file, everything was listed: all my files, folders, documents etc. The dozens of files that had vanished from my desktop were still accessible if I wanted to send them as attachments. So somehow they must still be there...somewhere.

I delved into the terminal (I've only just learned ls,  -l and cd...like I said 'green') and found all the contents from the desktop still existed even though I don't know where they have gone. 
the entries were like this:
drwxr-xr-x  5 sdh sdh   4096 2011-11-18 11:06 WEBSITES

So I'm confused. I've found similar posts, but nothing that seems to match this, and I can't seem to say what the problem is exactly other than my folder have gone, and my places are inaccessible. 

I really hope someone can help, as like every other idiot out there, I was always meaning to back up stuff properly but always too busy to actually do it. Lesson learnt. 

In desperation...
Dave ](*,)

---

### Post by LinuxFan999 on 2011-11-21
Try booting from the Live CD, then try finding the Home folder. If you can find it, back up your files. When you are done (or if you can't find the home folder and your files), you will need to reinstall Ubuntu. When you are finished, restore your backup (if you found your files and backed them up).

---

### Post by wonkyhonky on 2011-11-21
Thanks Linux Fan! :D

Ok, so I have got myself a live CD, and when I booted from it, I couldn't see where I would look for my home folder. The menu just asked if I wanted to try or install ubuntu. 

There was a rescue Mix on the 11.10 live disk, but that took me to text-only terminal interface, and that's scary, as I don't know how to come back from the darkness!
So, how do I do this? How can I make the live CD do what I need it to?

Next step, obi wan?

best and thanks,
Dave

---

### Post by LinuxFan999 on 2011-11-22
> **wonkyhonky said:**
> Thanks Linux Fan! :D

Ok, so I have got myself a live CD, and when I booted from it, I couldn't see where I would look for my home folder. The menu just asked if I wanted to try or install ubuntu. 
When 
There was a rescue Mix on the 11.10 live disk, but that took me to text-only terminal interface, and that's scary, as I don't know how to come back from the darkness!
So, how do I do this? How can I make the live CD do what I need it to?

Next step, obi wan?

best and thanks,
Dave
When you boot the CD, select "Try Ubuntu", then the desktop will be loaded. Once you are at the desktop, open nautilus and look for the home folder on the hard drive. Then you can look for your files and back them up.
Once you are finished backing up your files, you can reinstall Ubuntu.
You can back up to a USB stick or an external hard drive.

---

### Post by wonkyhonky on 2011-11-23
Thanks ever so much for your continued help!

I tried looking for the home folder, but it all seemed rather empty...

Having said that, what you said mad me think!

You mentioned accessing files, and backing up, then copying to external drives.

I downloaded deja-dup, and as suspected my home folder, desk top, and all other goodies appeared in the back-up browser menu. From there, as instructed, I backed them all up to a new file on my external hard drive, then restored them to another new file on the hard drive.

I now have ALL my info back, fully intact, and have been able to upgrade to 11.10 fully, transferring all my lost files back to where they belong! 

Hoorah! We may all drink wine now.

:popcorn:

---

