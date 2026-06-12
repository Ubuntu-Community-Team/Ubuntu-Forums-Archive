---
title: "Cannot unmount volume"
date: 2007-07-23
forum: Desktop Environments
---

### Post by MacDuff on 2007-07-23
When I try to un-mount an external USB hard drive  (Feisty using Nautilus) an error message pops up saying it Cannot unmount volume  or Cannot eject volume.

It sometimes occurs using a USB thumb drive as well but every time I use a USB hard drive.

I have been looking for some settings that may effect it but have found nothing. Is this a bug or am I missing something?

---

### Post by madmetal on 2007-07-24
> **MacDuff said:**
> When I try to un-mount an external USB hard drive  (Feisty using Nautilus) an error message pops up saying it Cannot unmount volume  or Cannot eject volume.

It sometimes occurs using a USB thumb drive as well but every time I use a USB hard drive.

I have been looking for some settings that may effect it but have found nothing. Is this a bug or am I missing something?

external usb storage is kinda buggy in feisty (as far as i know..)
try to close all applications that have used the disk and then try to unmount it from terminal with sudo..

---

### Post by MacDuff on 2007-07-24
Hi Madmetal:

Actually I tried that.  When it first happened I did a search on this problem and one of the things I found in an old posting was your suggestion.   

When I tried umount it came back with a message that the device was not found.  It still appeared on the Gnome desktop and it still offered me the option to unmount it but each time I tried it gave me the message that it could not unmount the volume.  (The wording may not be accurate. I have not tried it lately so I have forgotten the exact message).

---

