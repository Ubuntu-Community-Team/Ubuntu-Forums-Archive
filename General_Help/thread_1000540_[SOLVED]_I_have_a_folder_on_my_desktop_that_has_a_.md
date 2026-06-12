---
title: "[SOLVED] I have a folder on my desktop that has a mini lock on it and wont let me del"
date: 2008-12-03
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-03
I have a folder sitting on my desktop that has a mini lock on it and wont let me delete it.

How do I go about deleting it and off my desktop?

---

### Post by sstusick on 2008-12-03
You could try removing it via command line: "sudo rmdir <dir>."

For example: > sudo rmdir /home/steve/Desktop/'untitled folder'


---

### Post by PocketDog on 2008-12-03
Have you copied it there from an external drive or disc? If so, it's normal. Right-click it, go to permissions and allow your user account read/write access. You only have read access by default

---

### Post by PsychedelicWonders on 2008-12-03
psychedelicwonders@JohnnyScience:~$ sudo rmdir /home/steve/Desktop/favorites
[sudo] password for psychedelicwonders: 
rmdir: failed to remove `/home/steve/Desktop/favorites': No such file or directory
psychedelicwonders@JohnnyScience:~$ 

got that when I ran the code.

I changed it 4 times under permissions>file access>read and write

Then I hit Apply permissions to Enclosed files, but it doesnt save, the mini lock is still there and wont let me delete it?

---

### Post by sstusick on 2008-12-03
Ok, you need to replace "steve" with YOUR user name, which, I am assuming is psychedelicwonders.

So it would be: > sudo rmdir /home/psychedelicwonders/Desktop/favorites

And remember, Linux is a case sensitive OS. "**F**avorites" and "**f**avorites" are two different file names.

---

### Post by PsychedelicWonders on 2008-12-03
hahah im retarded.  I ended up getting it via permissions.

thanks guys.

---

### Post by sstusick on 2008-12-03
You're welcome. Just be sure to mark this thread as SOLVED under THREAD TOOLS.

---

