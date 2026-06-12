---
title: "Folder Recovery"
date: 2009-06-01
forum: General Help
---

### Post by Antispaceman on 2009-06-01
Is there any way to recover a folder that has been deleted completely.
(i can do this easily on windows with recuva)
I just deleted my documents folder by accident (i did'nt even realise I had)
then automatically emptied my deleted items (still not realising my document folder had gone)

my last back was about a week ago so i am screwed if I can't get it back

please help

---

### Post by michy99 on 2009-06-01
First you should immediately shut down the computer and boot from a Live CD. You can probably recover most of your documents with photorec, which is included in the testdisk package.

---

### Post by fermulator on 2009-06-01
I've had great success using TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)).

It's open source, and free.  Fairly simple to use.

Make sure you read carefully the documentation though so that you're comfortable with what you're *about* to do.

Indeed though, you should boot ASAP into a Live Ubuntu CD.

---

### Post by Antispaceman on 2009-06-01
Cheers I tried it but I think I will have to accept my loss, the documents I so wanted to recover are revision notes (most of the other stuff I have a backup for) (I should know their content anyway). Photorec just came up with 56000 odd txt files plus about 3 zips (and a few hundred other files file types) and with exams in 3 days I don't have time to go searching
Of course now I have a backup program set to do backup everyday (it seems I had to learn the hard way, because I have read thousands of people suggesting keeping regular backups is a good thing but never took any notice)

---

### Post by michy99 on 2009-06-01
One more thing before you give up. Try ext3grep. It's in the repositories for Jaunty. If you are using Intrepid,or earlier, you will have to compile it yourself. I have used it with success in the past.

---

