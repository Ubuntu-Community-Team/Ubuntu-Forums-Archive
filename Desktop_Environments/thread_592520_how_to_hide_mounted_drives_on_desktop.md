---
title: "how to hide mounted drives on desktop"
date: 2007-10-26
forum: Desktop Environments
---

### Post by anantgowerdhan on 2007-10-26
Hi,

I switched to Ubuntu 7.10 from Kubuntu and I found it better except it shows mounted drive on desktop. Instead I want to see My Computer and Home icon. I followed some of the threads and did following

[COLOR="Red"]gconf-editor

Then go to apps > nautilus > desktop and unclick volumes_visible[/COLOR]

but it still shows all the partitions. One thread, which is very old, suggested that if I mount it in some other location than /media, it wont be visible. I mounted these drives in /mnt but still these drives are there.

Please let me know whether its a bug of 7.10 or do i need to do some more changes

Regards,
Anant

---

### Post by mayonaise15 on 2007-10-26
I just tried the gconf-editor method that you described and it worked for me after I logged out and back in again.  The problem is, that method hides all drives from the desktop and I want to see my usb flash drives, my iPod, and my mounted CDs on the desktop when I plug them in.  Anybody have an idea how to accomplish this?

---

### Post by cwgannon on 2007-11-01
I'm looking to accomplish the same thing you are.  Thus far, I've only found all-or-nothing solutions: Either all my mounted partitions show up or none of them do.

Here's hoping somebody devises a solution, eh.

It seems like the guy in [this post]("http://ubuntuforums.org/showthread.php?t=592906&highlight=desktop+icon+mount") is onto something.

---

### Post by 5735guy on 2008-04-01
Many Thanks worked great :):):)

---

