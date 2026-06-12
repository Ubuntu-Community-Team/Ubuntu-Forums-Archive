---
title: "Dophin takes a long time to move to trash..."
date: 2009-02-10
forum: Desktop Environments
---

### Post by mister_doctor on 2009-02-10
This is more of an annoyance then a problem, and maybe I'm just an oblivious noob, but here goes:

I've got a media centre (kind of) with a 1TB NTFS formatted drive containing a metric buttload of various media. The machine runs smoothly for the most part, but I've noticed that when I try to delete files through Dolphin's move to trash, it takes a very long time to do, like a couple of minutes for a 700MB file versus instantaneous on my Vista x64 machine at work. Running the rm command at the terminal is instant, even for a folder full of crap.

Does anyone have any idea why this might be happening? Better still, is it preventable?

I haven't tried konqueror, yet.

-Kubuntu 8.04
-1TB Seagate 1TB drive, NTFS formatted (used to live in a windows computer)
-if there's some specific output from somewhere desired, I can't do it until I get home from work.

---

### Post by boom2k1 on 2009-05-07
I am running Kubuntu 9.04, and I can't even delete files from the home directory in Dolphin (using move files to trash)! A notification icon appears on the panel showing the progress, but it never moves the file to the trash!


Does anybody know how to fix it?

---

### Post by hoarder on 2009-05-15
I'm seeing the same thing here, anyone have any ideas on what may be causing this? It is very annoying. I'm using the latest 9.04 Ubuntu. I only started using Dolphin in this version.

---

### Post by richard_nl on 2009-05-30
Is there anyone with a solution to this? Somehow dolphin refuses to remove files and directories now

I found a solution to my problem at least. The trash was full but it didn't gave me any notice or error. Instead It only showed a progressbar that wasn't moving. I solved it by doing the following.

(from the dolpin menu)
Settings->Configure Dolphin->Trash
then check "delete files older then: #num# days"

---

