---
title: "Can't remove Kubuntu without errors."
date: 2009-04-08
forum: General Help
---

### Post by AmenX on 2009-04-08
Hello, I've been trying to uninstall Kubuntu for the past few days.
Last night, someone told me to use the built in windows vista partition manager thing.
I removed some part of the partition I Made for Kubuntu, but it wouldn't let me delete the main part of it ((If that makes sense.))
THis morning when I tried to turn on the computer, I got a grub error 17, and now my Vista won't come up because of that.
At the moment I'm on the Kubuntu live disk.

Once getting on this, someome told me to try out 'gparted'

I tried deleting and changed stuff around, but now I get a grub error 15.

I have no idea how to merge the partitions to vista, which I'm guessing would fix all this?


Could someone please help me? I don't want to have to reformat my whole computer.


I realise all of this might not of made sense, so if you have any questions, please feel free to ask.

---

### Post by milton1 on 2009-04-08
If you are done with linux completely, use a partition editor to delete the linux partition (parted magic will do the trick), then you can grow the windows partition to use that space. You will need to use your windows install disk to delete grub and reset the master boot record to the default windows system. Google something like "windows repair MBR". You should find lots of posts on the issue.

---

### Post by AmenX on 2009-04-08
> **milton1 said:**
> If you are done with linux completely, use a partition editor to delete the linux partition (parted magic will do the trick), then you can grow the windows partition to use that space. You will need to use your windows install disk to delete grub and reset the master boot record to the default windows system. Google something like "windows repair MBR". You should find lots of posts on the issue.

I've looked through the contents of my windows disk a few times, but I can't find anything that can delete stuff.


Edit: It won't let me merge both partitions.

---

