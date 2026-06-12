---
title: "Frequent freezes while running Firefox"
date: 2006-08-21
forum: Desktop Environments
---

### Post by edantes on 2006-08-21
I recently moved a Dell Inspiron 8100 from FC5 to Ubuntu 6.06.  Everything seems fine, except ...

Frequently enough to make it a show stopper, the system freezes for ~30sec, and then comes back to normal.  From looking at System Monitor, it looks like Firefox suddenly swamps the CPU during the freeze-ups.

Anyone else experiencing similar behavior? 
Any suggestions of how I could get better diagnostics of the problem?

---

### Post by akshaysrinivasan on 2006-08-21
Can you me more specific about your configuration?

---

### Post by edantes on 2006-08-21
> **akshaysrinivasan said:**
> Can you me more specific about your configuration?

Dell notebook Inspiron 8100 (Pentium III, 512M memory)
Ubuntu 6.06 with all updates (kernel 2.6.15-26-386)
Firefox version 1.5.0.5

It makes a bit complicated that I have a few extensions installed in Firefox: 
AdBlock Plus, Google Toolbar, SessionSaver, Gmail and Yahoo mail notifiers.

---

### Post by edantes on 2006-08-21
Following up my own thread.  I spent some working time without Firefox and the freeze-ups still happened.  This desktop is definitely sick. There are other symptom like the PC-Mouse loss of sync, and some slow-downs with the USB drives.

Any chance a reinstall would do anything?  One of my post-installation steps I am suspicious of was to allow AUtomatix a bunch of updates.  Including some drivers like nvidia.

---

### Post by orb9220 on 2006-08-21
Well the updates like nvidia will not install unless you installed them before. 

As for firefox only install one extension at a time and work with it for awhile before installing another. AdBlock plus and sessionsaver are fine I use them myself. Suspect google toolbar or yahoo and gmail checking at exact same time? Just guessing here.

And yes if other things are going wrong on desktop then a clean install  MAY fix it.

Automatix only installs what you checked to install.

---

### Post by dannyboy79 on 2006-08-21
Firefox is a hungrier Browser than say, Opera or even for sure Dillo. I actually just switched to Opera after Firefox took forever to run on my laptop running Xubuntu. Opera is actually a decent enough browser, theres bookmarks, etc. Don't know about flashplayer etc etc only because my laptop is really only for surfing and mobility, I use my desktop for doing more intense stuff but give opera a try, you can add a repository and then install it thru aptitude or I believe the way I did was to install a .deb package. Good luck, hopefully you don't need a re-install

---

### Post by edantes on 2006-08-22
Thanks for the suggestion guys.

I used Opera for part of my work day and the freeze-ups still happened.  I guess Firefox is not at fault.  The frequency of freezes was down anyway, so it was bearable.

I am still not sure of what exactly I added with Automatix.  I went on a clicking spree and might have selected too many external packages -- Not the scrip's fault.  I am thinking of a fresh reinstall and adding packages more carefully.

My problems are still the freeze-ups, the loss of sync when using a PC mouse (I switched to USB mouse now) and the delays in when using USB disks (related to the freeze-ups, I guess)

---

