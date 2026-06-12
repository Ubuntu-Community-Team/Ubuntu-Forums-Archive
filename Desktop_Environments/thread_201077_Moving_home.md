---
title: "Moving home"
date: 2006-06-21
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-06-21
I am trying to move my home directory. When I try and copy what I have in the home dir i get "Operation not permitted" errors on hundreds of files. I tried logging in as root and still got them.

I used this command

find  -depth -print0 | cpio --null --sparse -pvd /mnt/test

I got this from a guide on how to change your home directory to a different partition.

Can anyone help me?

Thanks

Ironfistchamp

---

### Post by linuchsan on 2006-06-21
what was your cp command?

---

### Post by ironfistchamp on 2006-06-21
I used the command posted above. I also tried logging in as root and doing a normal copy of the home di to the new place. I just used cp <from> <to>. I had the same problems. Also as root I tried doing a graphical copy using GNOME but I got the same errors.

---

