---
title: "Humongo headache"
date: 2009-05-13
forum: General Help
---

### Post by Messyhair42 on 2009-05-13
I've been having a series of problems for a couple of weeks now and it's finally hit "i dont know what to do" time.
My Jaunty installation didn't start out bad, not great, but it left more to be desired. then i started getting disk latency problems and eventually i could boot into Jaunty and within 20-30 seconds it would lock up or give me a black screen of death. so i started booting into Intrepid on another physical hard drive, i decided to downgrade jaunty to hardy and tried rescuing my documents from my jaunty drive. eventually that proved to be a huge task b/c i can access the drive just once and just right after i boot into Intrepid, hardly enough to copy any files.
so i bypassed that finally and tried to overwrite my jaunty install with hardy, i put in the livecd and when i get to the partition editor i get nothing at all, not even my intrepid drive. in my bios boot options i have two hard drives, an optical drive and one other entry i dont recognize, both hard drives show up ONLY if it boots from an actual POWER OFF not just a restart, i tried the livecd again and still nothing, i havent played around with disconnecting the drives yet. so for now i can still use intrepid but i'm at a dead end. it works but it's not what i want. do i contact my drive's mfgr (seagate)? i know it's not bricked yet, accessing it is a pain, a hit and miss, even from Intrepid but i can still take actions from it, just not reliably. like i said i've reached a dead end and i need help.

---

### Post by petrus4 on 2009-05-13
MessyHair, I can offer you some suggestions, but you may or may not find them straightforward.  I had problems with Ubuntu detecting my partitions as well, but I was able to fix it.

The geometry of my partition table was non-standard, and Ubuntu seems to have trouble when partitions are not listed in drive order.  I had a program called Acronis Disk Director in Windows, and I was able to use that to delete one partition, and set the other partition to primary.

You can't have, from memory, more than a certain number of primary (boot capable, depending on if there's an OS on them) partitions at a time, as well.  So if you've got two Windows partitions, your C drive and a data drive, and the data drive is marked primary, you will have to convert that to an extended partition before Ubuntu can recognise it.

---

### Post by Messyhair42 on 2009-05-14
thanks, my jaunty setup was setting /, /usr, /tmp, /var, and /home as separate partitions, / is primary and i'm not sure about the others. i was doing fine for the first two weeks with jaunty, and i could access it in Intrepid with no problems. i could try and partition part of a drive and install windows, just not sure how i'm going to. my top priorities are getting my big HD w/Jaunty working and saving the contents of my /home partition if possible, i've got backups of almost everything, just nothing since jaunty, nothing critical, just a bunch of downloads.

---

### Post by Messyhair42 on 2009-05-14
after several more tries, none of the LiveCD's i have recognize my hard drives at all.
i had another idea, i can see all my partitions i made when installing jaunty from intrepid, is it possible to change jaunty's files with terminal commands to try and make it more stable?

---

### Post by Messyhair42 on 2009-05-15
i had limited luck in rescuing two folders from the affected drive ~12GB of data saved. i'd still like some help in getting jaunty overwritten.

---

### Post by Messyhair42 on 2009-05-16
i played around with the drives, disconnected each in turn and nothing changed with the liveCDs.

---

### Post by Messyhair42 on 2009-05-18
I've had limited success with a brute force attempt (and constant rebooting) but i dont think it's the right tactic to recover functionality. my main concern is overwriting Jaunty and getting things running again

---

### Post by Messyhair42 on 2009-05-21
one more bump, with the statement that when the dl completes i will try Knoppix on my computer in hopes something happens.

---

