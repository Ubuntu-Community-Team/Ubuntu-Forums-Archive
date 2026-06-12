---
title: "Why are the graphics so slow?"
date: 2008-12-24
forum: General Help
---

### Post by Arukas on 2008-12-24
I have an nvidia 8800 GTS, I have restricted drivers enabled and I have been told to download envy and use that.

My desktop is still slow and crummy, and my computer should be able to handle a desktop environment.  

I've even told the effects off, and its still slow.  What's the deal with this?

---

### Post by LoneWolfJack on 2008-12-24
did you recently install some updates? an update broke my gutsy in the same way a few weeks back and no-one had a fix so I had to... well, you guess it... reinstall...

---

### Post by Orange Kingdom on 2008-12-24
Ubuntu and all other distro's (with Gnome) are slower than Windows because
the basic graphic system is seperated ,client-server model, therefore there is always a lag between them.
Major advantage with this system is you can run X local and apps remote.

---

### Post by Arukas on 2008-12-24
Its wasn't an update that made it slow.  Just normal operations.  Thanks for the info.

---

### Post by Arukas on 2008-12-25
I had some thoughts.

If the Desktop is sluggish by nature what's the point of all those desktop effects?  They'll just slow it down further?

---

### Post by Howitzer777 on 2008-12-25
its not sluggish at all....hmmmm are you sure you have the restricted graphics on? Try envy off.

---

### Post by Arukas on 2008-12-25
Yes, I've done all of that, and yesterday, I seen a Ubuntu video where it ran faster than mine with all the dumb special effects.

---

### Post by Zorael on 2008-12-25
> **Orange Kingdom said:**
> Ubuntu and all other distro's (with Gnome) are slower than Windows because
the basic graphic system is seperated ,client-server model, therefore there is always a lag between them.
Major advantage with this system is you can run X local and apps remote.Ah, but that's what we have [DRI](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure) for. :3

---

### Post by Arukas on 2008-12-25
I've installed Ubuntu 8.10.  I can't tell if its the same or not.  I think its better, but there was a different driver set up for the video card.  So, I'll have to play around a bit to see if its the same or not.

---

### Post by jespdj on 2008-12-25
> **Orange Kingdom said:**
> Ubuntu and all other distro's (with Gnome) are slower than Windows because
the basic graphic system is seperated ,client-server model, therefore there is always a lag between them.
Major advantage with this system is you can run X local and apps remote.
This is misinformation. X Windows is not inherently slower because of the client-server model (it's smart enough to see that the client and server are running on the same computer).

The graphics on Ubuntu and any other Linux distribution should not be noticeably sluggish, and it isn't for most users. If you notice that it's sluggish, especially if you have a fast graphics card such as the nVidia 8800, then there's something wrong in the setup of the software.

---

### Post by Arukas on 2008-12-25
Which software?

---

### Post by igknighted on 2008-12-25
The only inherent slowness I would worry about is GTK.  But that shouldn't be noticeable enough to warrant starting a thread.  So if it is that noticeable, then there must be something else.  Have you tried the very latest Nvidia drivers (the 180 series)?  They have gotten rave reviews so far.  Get them here (32bit): [http://www.nvidia.com/object/linux_display_ia32_180.17.html](http://www.nvidia.com/object/linux_display_ia32_180.17.html).

---

### Post by solwic on 2008-12-25
Zorael...the link in your sig, to the post supposedly by Linus Torvalds...is that real?

Just curious.  :P

---

### Post by Arukas on 2008-12-26
The drivers I have installed are thraought the restricted driver thing and I've tried the envy.

If its hasn't to do with those drivers, I don't know how to install.  Even when I have ask how to do it, all people have said is envy or to use the restricted drivers thingy.

---

### Post by Colt45 on 2008-12-26
Please see this thread for a potential solution.

[http://ubuntuforums.org/showthread.php?t=1021773](http://ubuntuforums.org/showthread.php?t=1021773)

---

### Post by Colt45 on 2008-12-26
Duplicate post, please delete

---

### Post by Colt45 on 2008-12-26
Duplicate post, please delete

---

