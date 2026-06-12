---
title: "change icon alignment on desktop"
date: 2006-06-19
forum: Desktop Environments
---

### Post by hezral on 2006-06-19
hi is it possible to change the icon alignment on the desktop? to the right hand side? i've been googling too..havent found yet

---

### Post by Luke771 on 2006-06-19
I like having my icons on the right side too. You can drag them where you want them, I always did it that way. 
That was when I used to have desktop icons.
I've found out that if you edit /etc/fstab to mount your file systems wherever *but* in the /media directory, they won't show up on the desktop, giving a more neat appearence to the interface.

I Added a file browser launcher in the panel and I use that instead of the Computer icon 
add to panel /custom launcher; at the 'command line' field type: nautilus (I also have one with the command 'gksudo nautilus' so I get write accesso to everything)

If I put a CD/DVD in the tray it will still show up in the upper-left corner of my desktop, I guess I could disable that by editing fstab again and mounting hdc and hdd somewhere else instead than in /media/cdrom (/cdrom only would do) but I have a tendency to forget CDs in the tray so it's actually useful to see them on the desktop... problem is, I drag the Icon to the right, and next time it will show up on the left hand side again (I now, that's what you were talking about) I'm sorry I can't do nothing about that, I hope someone can, but in the meantime, having no icons is kind of 'less bad' than having them somewhere else than where you want. It is like that for me, anyway.

---

### Post by CatKiller on 2006-06-19
I've got the cd icon on the right hand side - no others, mind - and it's always stayed there. I just dragged it there, and it stayed. It's never wanted to go back.

---

### Post by Luke771 on 2006-06-19
Hey!
It worked!
I never actually tried that before, because I was used to Breezy. With Breezy, the CD icon always popped up in the upper left corner no matter where it was last time, but with Dapper it will appear in the same place you left it. Nice.

---

### Post by hezral on 2006-06-19
well yeah i know that works.. but i was thinking maybe there is a way to permanently change so that everything that gets mounted will be on the right hand side.  thanks anyway.

---

### Post by strabes on 2007-10-08
I'd like to know if this is possible yet. I can't find any options in gconf-editor or anything.

---

### Post by strabes on 2007-12-18
Bump

---

### Post by strabes on 2008-05-27
bump

---

