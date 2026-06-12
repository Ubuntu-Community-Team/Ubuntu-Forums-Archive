---
title: "Problem with Gnome / Desktop"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Bonez56 on 2006-07-19
I think I broke Gnome!

I installed xubuntu-desktop and then changed my mind, so loaded back into gnome and removed the xfce packages via synaptic.

Ever since, all of my icons have dispappeared from my gnome desktop. I used to have icons for 2 fat32 partitions, as well as some samba share (shortcuts), as well as a few other bits and pieces.

They have now all gone. Also, when I try to right click on the desktop to bring up the menu which lets you change desktop background, arrange icons etc, this menu does not pop up at all.

GDesklets seems to be working fine, my desklets are still happily sitting on the desktop.

Anyone know how I can fix this? Thanks!

---

### Post by almahtar on 2006-07-19
Try start->system->preferences->sessions

click the "startup programs" tab, and click "add"
type "nautilus" in the box, and hit hit "ok", then hit "close".

Log out and log back in, and you should be ok.

---

### Post by Bonez56 on 2006-07-19
ok, well that explains a lot.

I removed nautilus earlier and decided i'd install thunar. I didn't realise natilus was entirely part of gnome and that my desktop would go away if I didn't have it installed :)

That leads me to my next question,

How can I have nautilus installed but make Thunar my default file manager? ie, when I click the "Places" menu and choose "Home directory" it opens up in Thunar instead of Nautilus?

Thanks for the quick reply!

---

### Post by almahtar on 2006-07-19
I know this doesn't entirely answer your question (and you're welcome for the quick reply), but nautilus does a few really handy things for you in gnome:

1.  Draws your desktop

2.  Auto mounts things like USB flash drives, media cards, your CD/DVDROM, other hard drive partitions, etc.

3.  Displays shortcuts to everything in /home/username/Desktop (obviously insert your user name for "username")

It can also burn CDs for you, sychronize files to a remote server for you, and many others, so in the long run if you need that functionality, check nautilus.

As far as using another file browser, I wish I had an answer for you.  I don't :-\  I use rox-filer, but I just create a custom shortcut for it on my panel.

---

### Post by Bonez56 on 2006-07-19
That info is great. Thanks again. I realise now that nautilus is a rather important part of gnome, so i'll do what you suggested and leave it installed, as well as creating a customer launcher for Thunar.

Cheers
Bonez

---

### Post by almahtar on 2006-07-19
One more thing: If you're going to use nautilus for your desktop, you may as well use it for your file browser:  it uses up a certain amount of memory to be your desktop, and lots of that memory could be shared with itsself if it was your file manager, but likely won't be shared with a different file manager.  If you want nautilus as your desktop background it'd probably be most efficient to use it as your file manager.  Feel free to test if that works for you for yourself, though: everyone does things differently.

---

### Post by almahtar on 2006-07-19
> **Bonez56 said:**
> That info is great. Thanks again. I realise now that nautilus is a rather important part of gnome, so i'll do what you suggested and leave it installed, as well as creating a customer launcher for Thunar.

Cheers
Bonez

Thank you :-) Never heard of thunar: I'll have to see what it's like now.

---

