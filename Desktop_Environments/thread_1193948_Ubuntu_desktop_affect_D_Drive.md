---
title: "Ubuntu desktop affect D Drive?"
date: 2009-06-22
forum: Desktop Environments
---

### Post by jaysonkys on 2009-06-22
I am new for linux, Currently i am using window XP with 2 partition C and D, Window XP is at my C drive and D drive is my personal document and other thing.

I got a question here which is, if i format the Window XP and replace it with linux ubuntu, will it affect my D drive and make me can't view my document at D drive?

---

### Post by lisati on 2009-06-22
With a little care, you should be able to reformat C: to use Ubuntu, and leave D: untouched.

---

### Post by jaysonkys on 2009-06-22
Thanks!!, if like that then tonight i will format it, wahahah.
long awaiting my linux Ubuntu.

---

### Post by dazman19 on 2009-06-22
yes. :D its great. 

I would use the ubuntu live cd to format it, just run the installation for ubuntu and you will come to the disk manager. You will notice the D drive and C drive when you use the disk manager. 

Take note of what ubuntu thinks your c drive is. usually something like /hda0.. (it may not be this).

After you have formatted and installed ubuntu you can edit your /etc/fstab as root to mount the d drive so you can see the files with ubuntu. 

depending on what the disk manager saw your d drive as you may need to change this. But add a line like this to the /etc/fstab and you should get access to your files. Before you do make a folder to mount it in.

mkdir /home/username/d_drive/

sudo gedit /etc/fstab

Add a line like this:
/dev/hda1   /home/username/d_drive   ntfs   defaults   0   0

---

