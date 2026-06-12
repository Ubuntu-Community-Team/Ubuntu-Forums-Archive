---
title: "Deleted files not releasing space"
date: 2010-03-28
forum: Desktop Environments
---

### Post by coyoteboy on 2010-03-28
Any ideas as to the cause of this? I'm deleting gigabytes of files and the space is never being released. Nothing stored in lost and found, yet space ever-diminishing?! Soon it'll all grind to a halt!

---

### Post by n0dix on 2010-03-28
Are you empty the trash bin?

---

### Post by jerrrys on 2010-03-28
i like bleachbit

[ATTACH]151731[/ATTACH]

---

### Post by coyoteboy on 2010-03-28
Cheers for the replies guys, yeah I've emptied the trash etc, but this isn't a case of un-necessary files as far as I can tell. I've a very basic desktop setup with a few additional extras (apache,mysql,samba) and a 5gig virtual machine and it's taking 38 gig of a 40 gig drive? It was up to 32 until I copied some files from an external drive, it went to 38 gig. I then transferred them back and was left with no change in empty space even after emptying the trash/lost+found.

---

### Post by n0dix on 2010-03-28
can you post the output of dh -f?
Did you do sudo apt-get clean and sudo apt-get autoclean?

---

