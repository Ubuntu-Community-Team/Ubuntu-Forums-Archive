---
title: "Nautilus sidebar changes from 14.04 to 16.04 – Part One"
date: 2016-08-21
forum: Desktop Environments
---

### Post by foberle on 2016-08-21
My computer is set up with separate physical hard drives or partitions for many of the things I "share" across different operating systems, whether two versions of Ubuntu (14.04 and 16.04) or virtual machines (Windows XP or Fedora 21). Examples are Documents, Genealogy research, Music, Development projects and so forth.
 
 
 In Ubuntu, this is accommodated by either:
 1) adding lines to the end of /etc/fstab such as "/mnt/Documents   /home/Me/Documents   auto bind 0 0" in order to make Ubuntu believe my partition is my Documents directory, or
 2) mounting the separate partitions with fstab entries such as "UUID=5c898a6f-b829-4046-9ccd-ae3c6badc558 /mnt/Development ext4 nodev,nosuid,commit=10         0 0"
 
 
 Nautilus now presents this information differently: In Ubuntu 14.04, the sidebar is configured something like this:
 Places
____Recent
____Home
____Desktop
____et cetera, et cetera
 Devices
____Unmounted, but attached, drives  
____Computer
____et cetera, et cetera
 Bookmarks
____Development
____Genealogy
____et cetera, et cetera
 Network
 ____Connect to Server
 
 
 Each section was clearly identified with a header/title, and while I would have liked it arranged differently, it at least appeared to have some reasonable taxonomy (organized by type of attached device &#8211; more about that in the next post).
 
 
 Now, with Ubuntu 16.04, the equivalent Nautilus sidebar looks something like the following:
 Recent
 Home
 Desktop
 et cetera
 - - - - - - - - - - - - - - - - -
 Unmounted, but attached, drives  
 Computer
 &#8230; et cetera, et cetera
 - - - - - - - - - - - - - - - - -
 Development
 Genealogy
 &#8230; et cetera, et cetera
 - - thin divider line
 Connect to Server
 
 
 There are no headers/titles on the sections which now makes them appear to be a random collection of &#8220;places&#8221; to choose from. The taxonomy remains the same, but it isn&#8217;t at all apparent what it is.
 
 
 I searched in vain for some configuration in the menus, config files, and so forth; I tried different themes to see if somehow they might be involved. Is there a way anyone knows of to get the section titles back? If not, does anyone know what the rationale was for this change? Is it a change from the Gnome folks, or did Canonical&#8217;s employees just feel like tinkering with it (it&#8217;s not like there aren&#8217;t a lot of actually broken things in Unity the developers could have worked on).

Can anyone point me in the right direction? Thanks in advance.

---

### Post by mc4man on 2016-08-21
> Is it a change from the Gnome folks, or did Canonical’s employees just feel like tinkering with it
Ubuntu doesn't make such changes with Gnome apps. This is the direction nautilus is taking, will be much worse in nautilus-3.18/20
Whether one could restore,  don't know/care, you'd need to go to the git commits to nautilus & search backwards from 3.14 release to find the causing commits. (- and no guarantee that they could be simply reverted

---

### Post by CantankRus on 2016-08-22
Switch to nemo.

---

