---
title: "NFTS Drives Mount to Desktop..Can I make them mount to my Gnome Panel instead?"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by bconverse on 2007-11-06
So, whenever my NTFS drives mount, they show up as icons on the desktop.  I'd like, if at all possible, to get them to show up on the task bar instead of desktop icons.  Any way to do this?

---

### Post by bconverse on 2007-11-06
Or, I guess another way to put this is, when the drives are automatically mounting, like they are supposed to, is there a way to make them just not appear on the desktop. I've always hated icons, I like doing everything from taskbar. Not a major problem, I was just curious.  I just noticed my typo in the title.  Embarrassing.

---

### Post by pjones0404 on 2007-11-07
goto a terminal and run the command gconf-editor. then select apps-nautilus-desktop.there is a checkbox there for the icons.

i would also like to know how to add them to a panel. i would prefer to add them to awn but i dont know of a way to do this. anybody how to mount entire partitions to an icon in awn?

---

### Post by MNICY on 2007-11-07
['quote]i would prefer to add them to awn but i dont know of a way to do this. anybody how to mount entire partitions to an icon in awn?[/quote]
Well, this would not work for making it so when you mount a partition, it appears, but you could do this:
Open AWN Manager
Click "Launchers"
Click "+ADD" button
Type: Application
Name: Partition Name
Command: location of your partition (example: media/sda1)

Restart AWN, and it should be there...
Could even put in your own icon for it :D

---

