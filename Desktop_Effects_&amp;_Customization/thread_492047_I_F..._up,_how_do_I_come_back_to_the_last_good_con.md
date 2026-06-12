---
title: "I F... up, how do I come back to the last good configuration???"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by error404 on 2007-07-04
I have been running ubuntu and beryl for a while with no problems. However a few days ago, when I tried to restart my pc I got this error:

Failed to start the x server (your graphical interface). It's possible that it is not set up correctly.


The only thing that I could think of, is that I installed a a few new beryl themes and some desktop icons.... (which they worked fine and didn't gave me any trouble before shutting down ubuntu)

is there an easy way to come back to the last know good configuration? (I can only access to the non graphical interface )

I HAVE IMPORTANT INFORMATION IN MY COMPUTER :(

thanks!
leo

---

### Post by Bothered on 2007-07-04
I don't know of how to restore a last good configuration, but you could try restoring /etc/X11/xorg.conf from a backup (if you have one). Make sure you backup your current /etc/X11/xorg.conf before overwriting it. If this doesn't work/you don't have a backup, you could try:

1. Back up /etc/X11/xorg.conf: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak"
2. Run "sudo dpkg-reconfigure xserver-xorg"
3. Answer the questions as best you can. If you there is a question you don't know the answer to, go with the default (by tabbing to OK)

Hope this helps!

---

### Post by Bothered on 2007-07-04
If you need to get at your data urgently, you can always boot off the Live CD and access your files from there (e.g. to copy them to another computer).

---

### Post by bapoumba on 2007-07-04
@ error404: thread moved to "Desktop Effects & Customization" as related to Beryl.

It was posted in "Absolute Beginners Talk".

---

### Post by error404 on 2007-07-04
okay, I'm back in ubuntu... feeling much better now.

but now Beryl doesn't run :???: any easy way to re-install it?

---

