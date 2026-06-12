---
title: "Saving the configuration of my computer"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by Protagonistics on 2007-07-01
Let's say I just bought a new desktop and wanted to move, verbatim, my entire OS, files, settings-- everything-- onto the new machine from my aging laptop. How can this be done? I don't want to reinstall everything. I want to migrate it- but can it be done without making everything buggy like I'm afraid it might do?

---

### Post by neptho on 2007-07-01
Long story short:  It's not going to happen.  You can backup and copy your documents, but your custom modules will have to be reset, X11 configuration, et al.  There's no real direct support for moving applications between systems for any OS.

There are utilities for Windows that attempt to do so, and they're very hit or miss.  If you partition your hard disk and copy everything from your old laptop to this new partition, you can have Ubuntu copy your preferences, but it's not going to get you all of your programs and data 100% intact.

---

### Post by khedron on 2007-07-01
You can copy your files and personal settings quite easily, though - just copy the whole of your /home/<user> directory to the new partition once you have installed the operating system.

For example, I would copy the whole of my /home/john folder to the new machine.

The actual replacement of the existing /home/<user> might be a bit tricky, since when you are logged in your programs will be using some of the files you want to replace.

I would boot a Live CD and copy the old folder contents over to the new installation (after you have booted the new installation and set up a user). Of course, if you have put your /home backup on a CD and you only have one CD drive, you'll need a little more creativity. 

System settings are a bit harder - they are stored in the /etc directory, but I'm not sure how much of it is computer-specific. I would probably let the installation create a new /etc directory in the new installation.

---

