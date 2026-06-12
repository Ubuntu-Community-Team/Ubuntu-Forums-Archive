---
title: "Hard drive free space problem"
date: 2009-03-10
forum: General Help
---

### Post by geckoguykc on 2009-03-10
I shrunk my windows partition, and then I booted to the ubuntu livecd to grow the ubuntu partition. The partition grow copied files to the left side of the free space after resizing. This reported an error and quit. I booted back into ubuntu and it works fine with no sign of hard drive corruption. I ran fsck and everything. I decided to open up gparted and check out the partition table, and the ubuntu partition is reporting more used space than the original partition took up. It makes no sense. The parition is now around 200 Gigs with like 160 used. The disk usage analyzer is reporting a total file system size of 37Gb and about 30Gb free. Everything is contradictory.......Everything runs fine without error though. I'm just missing hundreds of gigabytes of free space. When go to filesystem properties It says 30Gb free space and hundreds of Gb used. The thing is it says some of the used space is filled with unreadable content. I'm guessing I need a way to delete that stuff?

---

### Post by geckoguykc on 2009-03-11
bump

---

