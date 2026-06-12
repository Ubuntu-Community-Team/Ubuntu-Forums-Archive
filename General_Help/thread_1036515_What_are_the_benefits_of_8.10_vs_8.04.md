---
title: "What are the benefits of 8.10 vs 8.04?"
date: 2009-01-10
forum: General Help
---

### Post by lsutiger on 2009-01-10
I received my 8.10 cd a few weeks back, tried an install, and stuff was just batty (mainly desktop effects).
 
Here is my setup on the hard drive. I have the / and the /home folders on different partitions, so I get to do an install and keep all of my program settings in the /home folder. I am guessing some of the configurations in the my home folder were conflicting with some updates with the new system.

Anyway, back to the main question. What are the benefits of .10 vs .04?
If I have a perfectly good system working with .04, is it worth the hassle to upgrade?

Thanx for any input!

---

### Post by domoso on 2009-01-10
I don't know what the benefits would be to you. But, for me, on an old PIII laptop there were noticeable performance gains. I was so impressed I just installed it on my main desktop. I would have to say that there are definite performance improvements between 8.06 and 8.10. At least when it came to my old laptop.  

As for weird issues: I have noticed problems when upgrading from 8.06 to 8.10. The upgrade may run into problems late in the process but it was nothing an apt-get upgrade -f or apt-get dist-upgrade -f didn't fix.

I did notice on my desktop, presumably because I have an additional IDE controller installed that grub total screwed the pooch when it was installed pointing to the wrong harddrive for my installed OS's. That was not so easily corrected by removing the controller and installing grub using the liveCD. Then I reinstalled the controller and everything was fine.

---

### Post by tuxxy on 2009-01-10
> **lsutiger said:**
> I received my 8.10 cd a few weeks back, tried an install, and stuff was just batty (mainly desktop effects).
 
Here is my setup on the hard drive. I have the / and the /home folders on different partitions, so I get to do an install and keep all of my program settings in the /home folder. I am guessing some of the configurations in the my home folder were conflicting with some updates with the new system.

Anyway, back to the main question. What are the benefits of .10 vs .04?
If I have a perfectly good system working with .04, is it worth the hassle to upgrade?

Thanx for any input!

I can think of many pros for 8.10 over 8.04 Ill lsit some below;

_**Pros**_

Much quicker bootup/down times;
Better hardware support;
Better wireless and new network manager;
New xorg, GNOME;
Encrypted /home feature;
Guest session.

---

### Post by lsutiger on 2009-01-10
Well, since I have a separate /home partition, where a lot of settings for programs are located, could that be causing my problems?

---

### Post by tuxxy on 2009-01-11
> **lsutiger said:**
> Well, since I have a separate /home partition, where a lot of settings for programs are located, could that be causing my problems?

If you mean your compiz effects/animations were not functioning correctly you may have a conflict but its easily solved.  Open compiz settings manager then select preferences on the left, now create a new profile and it should work fine.

---

