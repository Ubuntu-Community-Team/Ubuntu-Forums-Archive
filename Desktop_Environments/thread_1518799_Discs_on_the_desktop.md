---
title: "Discs on the desktop"
date: 2010-06-27
forum: Desktop Environments
---

### Post by slimtonio on 2010-06-27
Hi,

I have a question regarding the ridsk appearing on the desktop.

When i go in Places -> computer in order to see the HD and then click on them, they appear on the desktop.
So my question is the following:

what can i do to make them stop appearing like this?
once they have appeared, how can i make them disappear?

Precision: I am working on ubuntu 10.04, but there is a partiion with windows 7, and a third one with nothing, just for sharing flies between windows and ubuntu

thank you!!

---

### Post by ajgreeny on 2010-06-27
Use Alt+F2 to get a run dialog and open **gconf-editor**, navigate to apps-nautilus-desktop and remove the selection from "volumes_visible".

No disk volumes will then show on the desktop, including usb disks, which can be a nuisance, as you will not be able to right click to unmount.  You can, however, use the disk mounter applet in your panel for that, if you miss the function on the desktop.

---

### Post by slimtonio on 2010-06-27
thank you !

---

### Post by slimtonio on 2010-06-27
Actually i now have another problem:

I would like to put all my music on this partition (not the one with ubuntu, the one only for files)
But the problem is that as long as the disc is not mounted, the music won't appear in rythmbox.

What could be the solution please?
Make the disc always mount when ubuntu start?
find another program for plyaing my music?
find a way for rythmbox to recognize the music even if the disc is not mounted?

---

### Post by ajgreeny on 2010-06-27
You will have to mount the extra partition to be able to use it and play music in rhythmbox or any other player.

Going back to your original question, you could have any disks except usb mount at /mnt at boot time by editing your /etc/fstab file.  Disks mounted in /mnt will not show on the desktop, so if you still want usb disks to show that is one way out of that problem.

If your music files are on another partition you will probaqbly find it easiest to make links from the music files to your  /home/username/Music folder, just for ease of using the files.

Come back again if that is all a bit overwhelming to you.  It is not as difficult as it sounds.

---

### Post by slimtonio on 2010-06-27
Thank you very much for your answer!!

But actually i don't know how to do these 2 things
can you explain please?

---

### Post by dondiego2 on 2010-06-27
> **ajgreeny said:**
> Use Alt+F2 to get a run dialog and open **gconf-editor**, navigate to apps-nautilus-desktop and remove the selection from "volumes_visible".

No disk volumes will then show on the desktop, including usb disks, which can be a nuisance, as you will not be able to right click to unmount.  You can, however, use the disk mounter applet in your panel for that, if you miss the function on the desktop.


Thanks.  Ever since I upgraded to Lucid I lost this.  I want the mounted disks on my desktop.  It's much easier to unmount my iPod with the icon there.

---

