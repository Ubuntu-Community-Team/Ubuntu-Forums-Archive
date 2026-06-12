---
title: "gtkpod read-only"
date: 2006-02-10
forum: Desktop Environments
---

### Post by hamsaladsandwich on 2006-02-10
Hi - trying to sync mp3's to my ipod using gtkpod, i get the following error:

Error opening '/media/ipod/iPod_Control/Music/F11/gtkpod801903.mp3' for writing (Read-only file system).

The songs appear on my ipod but are 0 seconds long.

I guess I just need write privileges? I'm pretty new to ubuntu but anything you guys could tell me would be great.

---

### Post by dmartin on 2006-02-10
I suspect this is similar to the situation with the mounting a Creative device.  You can see how to fix that issue in this post: [http://www.ubuntuforums.org/showthread.php?p=688254#post688254](http://www.ubuntuforums.org/showthread.php?p=688254#post688254)

Perhaps someone else can give you ipod-specific instructions.

---

### Post by hamsaladsandwich on 2006-02-10
thanks, i'll check it out

---

### Post by angkor on 2006-02-10
try 'sudo gtkpod', that worked for me once.

---

### Post by dmartin on 2006-02-18
So, yeah, you could run as root and avoid the issue.  But that's not really solving it, at least not properly.  The problem is that instead of giving gtkpod access to your iPod, as is ideal, you just gave gtkpod access to your entire system.  This means you are one bug or security issue away from gtkpod whiping your entire system out, or at least causing some damage.  It's a very rare likelihood, but still, I would look for an option like the one I gave.

For things like Synaptic, the developers expect you to run as root.  They run it as root themselves.  So they've extensively tested it running as root, and they do their best to make sure it is bulletproof and completely secure.  But something like gtkpod that isn't supposed to be run as root, the developers are probably set up the correct way, and don't test it running as root.  More danger for you.

The more things you run as root (sudo), the more chances you give yourself to be hurt.

---

### Post by angkor on 2006-02-18
I am well aware of the dangers of running things as root. Since gtkpod is an application I only use on occasions and doesn't have any access to the net on my system I feel secure enough to run it as root once in a while.

Also, if the op is able to read/write is iPod with gtkpod running as root you know what the problem is and it could easily be solved by editing fstab.

---

