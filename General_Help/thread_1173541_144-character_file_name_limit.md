---
title: "144-character file name limit?"
date: 2009-05-29
forum: General Help
---

### Post by gtmarks on 2009-05-29
I have just installed Ubuntu 9.04, with the ext4 filesystem on my root partition.  In the terminal I seem to be unable to use file names longer than 144 ASCII characters:

91$touch xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

92$touch xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
touch: cannot touch `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx': File name too long

(Note: there are no spaces in these strings of x's; spaces seem to be inserted when I preview this post.)

This is a major problem for me since I have a huge tar file containing the "Documents" directory from my old computer, but I cannot extract the files on my new computer since tar exits with error 2 as soon as it hits one of my files with a name longer than 144 characters.  (As a temporary solution I tried adding the --exclude flag with 145 .'s followed by * but tar still aborts when it gets to the big file name.)

Does Ubuntu not use the posix standard maximum file name length of 256 characters???  What is wrong here and how do I fix it?

---

### Post by fcheslack on 2009-11-01
just ran into this limitation in Karmic.
Cannot create a file anywhere in the file system with >143 character filename.
Fresh install of Karmic 64bit with ext4

Edit: scratch that. This is a case of eCrypt making the filename too long.

---

### Post by nyhm on 2009-12-08
Confirmed: Encrypted home dir with ecryptfs (as provided by 9.10) causes a file length error for me, too. I thought it was tar (because I was extracting an archive), but I can extract to /tmp. Moving the file to my encrypted home dir causes the same error message.

Is there any way around this? Can ecryptfs be configured differently?

This might force me to forego home dir encryption ([as being discussed on this other thread]("http://ubuntuforums.org/showthread.php?t=1258294")).

---

