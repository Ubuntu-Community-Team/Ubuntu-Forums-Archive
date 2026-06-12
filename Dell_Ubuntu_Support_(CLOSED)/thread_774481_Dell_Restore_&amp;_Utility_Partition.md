---
title: "Dell Restore &amp; Utility Partition"
date: 2008-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nico0020 on 2008-04-29
Okay so I have been using Ubuntu for about two years on my laptop.  When setting up my partitions I always notice there are two dell related ones.  I have wanted to just format them and add them to another partition, but I never understood what they were for or what they did.  Mind you my system was not preinstalled with ubuntu.  One is called "Dell Restore" and the other is "Dell Utility".  Does anyone know what they are for or what they do.  I still have a very small windows partition, if that makes any difference.  I just want to know what i'm messing around with before I format it.

---

### Post by notwen on 2008-04-29
Very likely that the first contains the boot sector and Media Direct(if your system has it) while the second and larger partition is likely the restore image.  At least this was the case for my Inspiron 1420n.  =]

If you have the install media for both Windows and Ubuntu I see no reason w/ needing these two partitions.  Hope this helps.  =]

---

### Post by essexboyracer on 2008-04-29
merge both the utility and restore partition into one, do a fresh install of ubuntu on your main partition then use sysrescuecd (which includes partimage) and create an image of the newly installed ubuntu onto the newly created dell partition for future. If you ever need to restore your Ubuntu install to the same when it left the factory :) just use sysrescuecd to restore the partimage!

---

### Post by Nico0020 on 2008-04-29
cool, thanks alot

---

