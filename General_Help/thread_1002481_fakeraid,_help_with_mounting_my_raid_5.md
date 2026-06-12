---
title: "fakeraid, help with mounting my raid 5 ?"
date: 2008-12-05
forum: General Help
---

### Post by Sullr on 2008-12-05
Hello,

I am having some issues mounting my raid 5 in ubuntu 8.10, here are some details

Computer
MB: Asus Commando ( raid controller is jmicron I think )
Hard drives: fakeraid 3x500gb Seagate

I set up the raid after installing ubuntu, dmraid is installed!

If I open up GParted I see the raid, /dev/mapper/isw_dgccigiegb_RAID5 when trying to partition ext3 I get the error "apparently in use by the system; will not make a filesystem here!", but I can partition reiserfs!

The problem I am having is I cannot seem to mount this raid, 
I use this command to try and mound "/sudo mount /dev/mapper/isw_dgccigiegb_RAID5 /media/RAID"

I then get the message already mounted or /media/RAID busy

Maybe someone could point me in the right direction as to what I am doing wrong.

Thanks

PS. I have searched around and have tried different things, but nothing seems to work. I just want to setup my fakeraid :p

---

