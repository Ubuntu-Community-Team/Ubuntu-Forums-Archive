---
title: "Plz help!"
date: 2009-01-19
forum: General Help
---

### Post by Colinrcasto on 2009-01-19
so i have had ubuntu 8.04 for about a week and i decided it's just not the OS for me. The only applications i really use are Guitarpro(i could not get the Linux alternative to work) FLstudio(LMMS was downloaded but i can find no way to open it) MTGO (it barely works with wine unless your willing to wrestle with it and even then it's slow and unsatisfactory) And iTunes (doesn't work with wine, period).

But when i attempt to reinstall windows XP the installer doesn't recognize my hard drive so i can't even set up a new partition.

I would really appreciate any help someone is willing to offer me!


Thank you, Colin

---

### Post by taurus on 2009-01-19
Boot your machine with the LiveCD and use gparted (System -> Administration) to delete all the partitions.  Then, format your harddrive to ntfs filesystem.  Shutdown and insert windows CD to boot from it.

---

### Post by Colinrcasto on 2009-01-19
When i right click to format the drive NTFS is greyed out

---

### Post by taurus on 2009-01-19
You have already deleted the Ubuntu partitions, right?

Can you post a screenshot of the gparted window, Applications -> Accessories -> Take Screenshot.

---

### Post by hyper_ch on 2009-01-19
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by ju2wheels on 2009-01-19
> **Colinrcasto said:**
> When i right click to format the drive NTFS is greyed out

Pop in the LiveCD, install ntfs-progs from the repository (you may need to enable one of the repositories in the software sources) and try again with gparted.

---

### Post by Colinrcasto on 2009-01-20
file:///home/colin/Desktop/Screenshot.png

theres my gparted window

---

### Post by ju2wheels on 2009-01-20
Your image didnt upload, that link is relative to your computer only. Upload the pic to a website like tinypic.com and then use "Insert Image" button on the message text box.

[IMG]http://i42.tinypic.com/2qv8eb6.png[/IMG]

Also be sure that when you unmount the partition you are trying to modify. You should be able to right click it in gparted and unmount it.

---

### Post by mcduck on 2009-01-20
> **ju2wheels said:**
> Pop in the LiveCD, install ntfs-progs from the repository (you may need to enable one of the repositories in the software sources) and try again with gparted.

Actually there's no need to format the partition to anything, or even create one at all.

Just remove all partitions from the disk and then start the computer with the Windows install CD. Windows has no problems creating its own partition on empty, unpartitioned hard disk.

---

