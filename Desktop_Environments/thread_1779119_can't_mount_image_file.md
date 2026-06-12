---
title: "can't mount image file"
date: 2011-06-10
forum: Desktop Environments
---

### Post by blompy on 2011-06-10
I've got an image file that I made with DDrescue.

I installed Sleuth Kit and when I type:  mmls /mnt/drive/file

it says "cannot determine partition type"

I imaged a different drive and tried to use the same command line and got the same results.


I'm not familiar with working with image files too much, so if someone could toss me a bone I'd appreciate it.

I would like to mount the NTFS partition within the image file.

---

### Post by Elline on 2011-06-10
What is the extension of this file? Is it a dump of a hard drive? Have you tried to mount it with just mount command?

As far as I know there is definitely a way to mount it with "mount" star**t**ing from blocks where your NTFS partition belong to, I can't recall it right now, through. But this is if it's not a special format of one program.

---

### Post by blompy on 2011-06-10
Hi.  I named the image file:  test.img   


I haven't tried to mount it with "mount" yet.

I guess I could look into it, but I don't know what "blocks" to enter into the command line.  That's what I was trying to use mmls for, to obtain that info., but it doesn't work.

---

### Post by nomko on 2011-06-10
Dod you tried a program like furiusisomount? or acetoniso?

---

### Post by syoung27 on 2011-06-10
devede and k3b are the best tools you can have

---

### Post by blompy on 2011-06-10
guys thanks.

Furious ISO mount works perfect.  I'm a new linux user.  Are there equivalent GUI tools for all command line tools in linux ?

---

### Post by Elline on 2011-06-11
For all programs no.
But certainly for some of them. There is many GUI programs which uses small utilities as it's back-ends, like GParted do. This is as I understand is UNIX way.

---

### Post by blompy on 2011-06-12
I can't figure out what happened.  Before when I used Furious ISO Mount, it mounted to the desktop no problem.  Now when I click "mount", it mount at: /home/testuser/image_img

And there's nothing in the folder.

---

### Post by blompy on 2011-06-12
nevermind..

---

