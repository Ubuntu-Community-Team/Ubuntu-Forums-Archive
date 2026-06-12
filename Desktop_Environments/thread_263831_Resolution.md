---
title: "Resolution"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Arandomcow5 on 2006-09-23
My monitor comes with a recommended resolution of 1280x1024, but it will not allow me to use a resolution greater than 1024x768. I tried editing the xorg.conf file to add the resolution, but that doesn't work either (even after i restart). How do i fix this?

---

### Post by sharkcohen on 2006-09-23
We'll need some more info in order to help you out.  Do:

lspci | grep -i vga

and post the results here.  Then, post here the contents of your /etc/X11/xorg.conf  Also, post here the contents of your /var/log/Xorg.0.log right after an unsuccessful attempt to run 1280x1024.

---

### Post by Arandomcow5 on 2006-09-23
user@zuzzle:~$ lspci | grep -i vga
0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0092 (rev a1)

---

### Post by zurih on 2006-09-23
had the same problem. changed the monitor in xorg configuration wizard to 1280x1024 and thats solved it.

---

### Post by sharkcohen on 2006-09-23
> **Arandomcow5 said:**
> user@zuzzle:~$ lspci | grep -i vga
0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0092 (rev a1)

Still need:

Contents of /etc/X11/xorg.conf
Contents of /var/log/Xorg.0.log after unsuccessful attempt at 1280x1024

Also need results from:

cat /proc/driver/nvidia/version

It would also be nice to know some details about your monitor, what kind of cable you are using to hook up your monitor (VGA or DVI?), and what nvidia card you have, seeing lspci is returning 'unknown device' (I hate it when it does that).

---

