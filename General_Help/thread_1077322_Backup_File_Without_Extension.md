---
title: "Backup File Without Extension"
date: 2009-02-22
forum: General Help
---

### Post by kmac on 2009-02-22
Hey guys, sorry for not posting for a while, I've been out and about in R.L. However, I have run into a bit of trouble. I, in all my geniousness, decided it was a good time to remove my girlfriend's windows backup from her laptop to free room on her hardrive. I had the pleasure of typing "sudo rm -r /windows" and it felt great. However, my wonderful better half had unknowingly copied all of her music and pictures (loaded with sentimental value ...ugh) into the backup partition. 

So, I went ahead and looked into photorec and didn't have much luck. The files were all recovered with new filenames and unsorted, plus she ran out of disk space on the other partition to be able to recover all of her cherished files. Now, I have a backup of her old Windows Vista install on my external HD. The problem is this: I have no memory whatsoever of what the backup program was, much less how to figure out what it was, as the backup file has no extension. 

So what this all comes down to is if anyone has heard of a way to universally open backup files, or even to determine which program wrote the file.

Any help is appreciated, and I swear that when I get more time, I'll start answering questions again.

---

### Post by geirha on 2009-02-22
Run file on it.
```
file backupfile
```

File will look for certain patterns in the file's content, and may figure out what type of file it is.

---

### Post by kmac on 2009-02-22
> **geirha said:**
> Run file on it.
```
file backupfile
```

File will look for certain patterns in the file's content, and may figure out what type of file it is.

Just says that it's data, nothing special...

---

### Post by geirha on 2009-02-22
Then it was not a filetype that file knows about. Another approach might be to run strings on it, which will print out any ascii strings it may find. They may or may not provide a clue.
```
strings backupfile | less
```

---

### Post by kmac on 2009-02-22
Nothing comprehendable, sorry...

It looked like something out of CounterStrike server full of 13 year olds, each with their own dialect of 1337

---

### Post by geirha on 2009-02-22
Out of ideas then I'm afraid. Your best option is probably to try opening the file in every backup solution you can remember having tried and hope for the best :/

---

### Post by kmac on 2009-02-22
> **geirha said:**
> Out of ideas then I'm afraid. Your best option is probably to try opening the file in every backup solution you can remember having tried and hope for the best :/

That's what I was afraid of...

---

### Post by kmac on 2009-02-22
Ok, I've determined it to be a Windows Vista simple backup and restore file. I checked my Google search history and found that I followed a tutorial on the program. Now, I've tried opening the file with Windows Bu&R, but to no avail, as the program doesn't recognize the file. So, is there any way to decompress (more specifically now) a Vista backup file in ubuntu?

If not, is anyone Windows savvy enough to have any advice?

---

