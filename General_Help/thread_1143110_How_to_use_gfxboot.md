---
title: "How to use gfxboot?"
date: 2009-04-29
forum: General Help
---

### Post by camper365 on 2009-04-29
I just used Synaptic to install gfxboot, and the ubuntu gfxboot theme.
But how do I configure GRUB to use that?

---

### Post by camper365 on 2009-04-29
anyone?

---

### Post by aniruddha on 2009-04-29
You could try following the instructions here:

[http://guide.ubuntuforums.org/showthread.php?t=481957](http://guide.ubuntuforums.org/showthread.php?t=481957)

64bit may cause some problems with themes though. Some of the ones on gnome/kde look may not work. Best luck...

---

### Post by camper365 on 2009-04-29
What I did was use Synaptic. I have tried to do the stuff that is in that tutorial, but it always breaks my GRUB.
Where do I edit my menu.lst to allow the use of gfxboot.
I have noticed that the gfxboot tutorials are always vague as to where the line of code goes in the menu.lst.

I do not have a 64 bit processor or OS

---

### Post by aniruddha on 2009-04-30
Umm. I haven't used gfxboot since hardy, but I do remember putting the gfxboot command right at the top for menu.lst (I don't know if it makes a difference where you put in the file, does it?). Do remember to follow the instructions for re-installing grub (the root, setup commands). Are your message files in the proper folder and named correctly in menu.lst?

---

### Post by camper365 on 2009-04-30
That didn't work.
I looked at the tutorial, but when I tried to put GRUB back on the MBR, I would always get
```

grub> find /boot/grub/stage1

Error 15: File Not Found

grub>

```

---

### Post by aniruddha on 2009-05-01
Not sure about that, have never gotten that error myself. Maybe one of the other gfxboot threads will be able to help? You could try installing grub-common, it seems to have helped some people here:

[http://guide.ubuntuforums.org/showthread.php?t=208855&highlight=error+15&page=72](http://guide.ubuntuforums.org/showthread.php?t=208855&highlight=error+15&page=72)

---

### Post by krzys59 on 2009-05-10
> **camper365 said:**
> That didn't work.

grub> find /boot/grub/stage1
Error 15: File Not Found
grub>


If you have partition BOOT as separately partition, use:
grub> find /grub/stage1



Sorry about my English

---

### Post by camper365 on 2009-05-27
I think my problem is that I use ext4 and GRUB doesn't support ext4 yet.

---

