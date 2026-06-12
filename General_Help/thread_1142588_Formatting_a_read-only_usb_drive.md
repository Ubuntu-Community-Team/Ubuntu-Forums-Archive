---
title: "Formatting a read-only usb drive"
date: 2009-04-29
forum: General Help
---

### Post by Ginswich on 2009-04-29
Hello, I have a problem with my usb drive. This morning I went to my faculty's reprographics to print some files I had stored in my usb, and the guy said I had a virus (it's almost impossible, as I only use it in Ubuntu), and after a while he said he fixed it (he didn't tell me how, i suppose with the antivirus he had). After, when I arrived home, I tried to copy some files into the usb and I couldn't because now it is with read-only permissions. I've tried formatting it with mkfs and GParted, and both fail because they don't have permissions to format the drive... i've tried it in Windows with the same result...

Any idea?

---

### Post by evilaim on 2009-04-29
Good morning, that is weird.  Make sure there are no little switches on the drive to make it read-only.

Can you write to the drive if you do sudo?

---

### Post by Ginswich on 2009-04-29
There is no switch, and everything I've tried is with sudo...

I forgot saying that _now_ it is possible there is a virus in the usb, because after the guy of the reprographics assured me I had a virus, he said they DO have one the day before, and I suppose it is possible that they passed me the virus... ¬¬

---

### Post by Ginswich on 2009-04-29
Sorry, I didn't answer your last observation. No, I can't write it with sudo. It sais the disk is mounted as "read only"...

---

