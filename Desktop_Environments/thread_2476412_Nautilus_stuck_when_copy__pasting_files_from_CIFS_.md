---
title: "Nautilus stuck when copy / pasting files from CIFS mount"
date: 2022-06-25
forum: Desktop Environments
---

### Post by louthrax on 2022-06-25
Hi everyone,

I have a network drive attached to my internet provider box (a recent "Livebox6"). 

I mount it using CIFS. Everything works fine when issuing command line operations (rsync, cp, etc...), but when copy / pasting files from my network drive to my local drive, Nautilus hangs after copying the very first file. I'm not talking about huge file transfers here, I'm just trying to copy 8 bash scripts files for a total amount of 37Kb.

Nautilus always hangs after copying the first file.

Copy / pasting the same files from a USB mounted drive works fine.

I already tried the following things:
[LIST]
[*]Changing CIFS mount options (nohandlecache,cache,noblocksend,nostrictsync,rsize,wsize...).
[*]Switching different display servers (Wayland, Xorg, Gnome classic, Ubuntu...). I had some doubts about the display server because Wayland prevents me from drag'n'droping files from archive manager...
[*]Try on a different computer (also on Jammy Jellifish) but using Wifi instead of wire connection.
[/LIST]

I don't know where to start investigations on the problem as no errors are reported (Nautilus just hangs forever).

Does anybody have any idea on the cause of the problem? As I mentionned above, everything works fine when copying files from command line, so the problem really seems linked to Nautilus and CIFS, not the kernel itself.


Thanks in advance !

Louthrax

---

### Post by louthrax on 2022-06-25
As my PC is dual-boot configured, I just tried to copy / pasting the same files on Windows 10, and it worked flawlessly.

Also, I just tried to connect to my network drive without mounting, browsing to it through Nautilus "+ Other locations" tab. And this way, copy paste is working without problems :) !

So now, I'd like to replicate the way the drive is mounted here to my /etc/fstab.

The "mount point" seems to be "/run/user/1000/gvfs/smb-share:server=livebox,share=databackupnas", but this location does not appear if I issue a "mount" command...

A solution could be to "mount" automatically that "/run/user/1000/gvfs/smb-share:server=livebox,share=databackupnas", but how to do that ?

---

### Post by louthrax on 2022-06-25
OK, after some more investigations, it appears that Nautilus is stuck on copying files only if they are smaller than 4096 bytes !

---

### Post by louthrax on 2022-06-26
Problem solved here by adding "cache=loose" in the CIFS mount options (but there might still be a real problem in Glib ?).

---

