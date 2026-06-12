---
title: "P2p"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Gadgeteer on 2006-08-02
I installed Amule awhile ago and it was working fine until I did something..(can't really remember what) afterwards it just started...blinking?..It goes between a dark color and a light one every second and I can't do anything, it's frozen. So, I uninstall it completely and re-install it. As soon as I load it up same thing. I give up and install Frostwire having had experience with Limewire when I used windows. It would be perfect but it slowly freezes when I use it. It works fine at first then it gets slower and solwer till it completely freezes. During this whole time everything else works, until it freezes completely then everything else gets buggy to. I thought it might be out of band searching so I disabled it...same problem. Complete uninstall/re-install. Same thing. Any ideas on either client? or maybe an awesome new one?

---

### Post by tzulberti on 2006-08-02
You could try bittorrent

---

### Post by stoft on 2006-08-02
A shot in the dark, have you tried removing your aMule settings? Move ~/.aMule to e.g. ~/aMule_backup and see what happens when you startup aMule. Your settings will be the default but if it's not blinking anymore you've narrowed down the problem to your own personal settings.

Other p2p (do an "apt-cache search <word>" to find specific clients):
 - direct connect
 - gnunet
 - gnutella (same as limewire/frostwire but there are more clients out there)
 - torrent (already mentioned)

Do a search on "p2p" at wikipedia as well, should turn up som alternatives.

---

### Post by Gadgeteer on 2006-08-03
Not a fan of bittorent...if it has what I want theres usually no one seeding or leeching it...


and thanks I'll try that out.

---

### Post by Gadgeteer on 2006-08-03
I can't find the aMule files](*,) ...and I installed MLDonkey and a couple of other programs...but there not showing up under Applications.

---

### Post by stoft on 2006-08-04
> **Gadgeteer said:**
> I can't find the aMule files](*,) ...and I installed MLDonkey and a couple of other programs...but there not showing up under Applications.

A '.' (dot/period) before a directory means it's hidden, have you taken that into account? After the install of MLDonkey etc. have you restarted your GUI/x-server. Sometimes a restart of the desktop is needed for apps to show up in the menus.

---

### Post by Gadgeteer on 2006-08-04
I restarted completely.

---

### Post by darrenm on 2006-08-04
mv ~/.aMule ~/.aMule_backup

then sudo apt-get remove amule && sudo apt-get install amule

see what happens.

---

### Post by stoft on 2006-08-04
> **darrenm said:**
> mv ~/.aMule ~/.aMule_backup

then sudo apt-get remove amule && sudo apt-get install amule

see what happens.

I'd probably do "sudo apt-get remove --purge amule" even.

---

### Post by Gadgeteer on 2006-08-04
alright I got it working...but nothing ever downloads....it just sits idly...](*,) alright w/e I don't like aMule anyways...anyone know how to fix Frostwire...or an easy way to install Limewire

---

### Post by darrenm on 2006-08-05
> **Gadgeteer said:**
> alright I got it working...but nothing ever downloads....it just sits idly...](*,) alright w/e I don't like aMule anyways...anyone know how to fix Frostwire...or an easy way to install Limewire


Are you connecting with highid's? I find *mule great.

---

### Post by Gadgeteer on 2006-08-05
I'm using the standard stuff that came with it...don't like it so why work on it...

---

### Post by s1mple_M4N on 2006-09-20
Hi Gadgeteer,

I found this thread when I was lookng for ways to install Limewire

[http://www.ubuntuforums.org/showthread.php?t=241284&highlight=.rpm+files](http://www.ubuntuforums.org/showthread.php?t=241284&highlight=.rpm+files)

Hope it helps

---

