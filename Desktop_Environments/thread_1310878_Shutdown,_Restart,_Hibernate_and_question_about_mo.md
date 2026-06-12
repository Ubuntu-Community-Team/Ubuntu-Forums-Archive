---
title: "Shutdown, Restart, Hibernate and question about modprobe"
date: 2009-11-02
forum: Desktop Environments
---

### Post by DarkDarkness on 2009-11-02
Hey everyone :)
I have installed 9.04 few days ago on my laptop (through wubi), and upgraded it to 9.10 lately.
I have found two annoying problems:
1. shutdown, restart and hibernate through the gnome GUI just doesn't work.
It's logged off, the screen turned off, and then the computer just get stucked.
If I'm trying to shut the pc down or restart with "shutdown -h now" or "reboot", it is done successfuly.
Why? What can I do? How can I make the hibernate work?
2. To get my bluetooth working, i need to load a module, and i do it with modprobe.
But every time I reboot my pc, I need to load this module again.
Is there anyway to make it load the module automaticly?
Thanks, and sorry for my English.

---

### Post by DarkDarkness on 2009-11-02
:popcorn:

---

### Post by DarkDarkness on 2009-11-05
Updates:
1. Restarting the pc works. Shutdown and hibernate doesn't. even `sudo shutdown -h now` makes the pc stuck.
2. Solved using /etc/modules file.
Help?

---

### Post by DarkDarkness on 2009-11-06
Update: 
I have just noticed that the problematic stage is "Deactivating Swap", and there the pc get stuck.
Any ideas?

---

### Post by Weazel on 2009-12-02
Already posted this, but I really want to get this solved so I'll re-post it in this thread, cause its sounds the same issue.

I have the same problem..

I think its since I've installed Bootup-Manager.

a few things changed:

1. I no longer see timeout during grub boot menu, so unless I choose an OS from my dual boot, It'll idle grub forever.

2. Every time I open the laptop I have to do "sudo /etc/init.d/vboxdrv start" if I want to open my virtual box

3. I need to Open Samba and go to Server Settings>Security and Re-choose "Share" from Authentication Mode.

4. and of course, as said before, When I want to shutdown, It'll get stuck in "Deactivating Swap" until I manually shutdown from the power button.


I'm kinda noob in these things, but I would really love some help.


thanks in advanced.

Weazel.

---

