---
title: "Nautilus regression"
date: 2006-03-11
forum: Desktop Environments
---

### Post by hobbit1983 on 2006-03-11
Hi All,

I run Breezy and have always been able to burn ISO images using nautilus.  However recently I have tried to burn an ISO.  The ISO in question has burned fine with nautilus before, and still burns fine if I use gnomebaker to burn the disc.  

This seems to be a problem in the way nautilus is "expanding the ISO" as it fails with a "file.iso is not a valid ISO image"

As I said this used to work fine so methinks a regression in nautilus.  Is there anyway I can obtain output trace from Nautilus to either see what is going wrong (and try to fix it) or give to the dev team.

Any help would be appreciated

---

### Post by Yleeyas on 2006-03-12
Hello hobbit1983,

I'm having the exact same problem; " ... not a valid ISO image"
Can't help you with how to troubleshoot  Nautilus, but if your just trying to burn a bootable disk, I found this useful:
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Basically, you just right click on the .iso in your filebrowser window (not the cd creator window!), select 'write to  disk' from the dropdown menu and away you go. Works for me. :) 

Hopes this helps

Yleeyas

edit:
OOPs, just realized your using gnomebaker to create disk, so that's not the problem. Hope you get some more useful advice :oops:

---

### Post by hobbit1983 on 2006-03-13
WOOHOO

Many Thanks Yleeyas, that worked.  I know I could use gnome baker but it's so slicker IMO to use Nautilus.  I've just tried it with burning Dapper flight 5 so I can go away and test it.

Thanks again for the reply.

---

### Post by Yleeyas on 2006-03-13
Hi again hobbit1983,

Glad to be of service :-D 

I don't understand why they include CD/DVD Creator as their default burner s/w, since it can't handle .iso, and doesn't handle multi-sessioning (adding to CD-RW)  :mad: 

Oh well, see you around :) 

Yleeyas

---

