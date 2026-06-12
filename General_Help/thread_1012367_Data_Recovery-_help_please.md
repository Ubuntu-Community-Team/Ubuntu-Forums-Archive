---
title: "Data Recovery- help please"
date: 2008-12-15
forum: General Help
---

### Post by spencercarran on 2008-12-15
I'm running a tri-boot of Ubuntu 8.10, Mac OSX Leopard, and Vista Ultimate on my Macbook 3,1.

So, the other day I was playing around, installing some new software, and in typical n00bish style, did not pay enough attention while installing a program called calibre ([http://calibre.kovidgoyal.net/download_binary]("http://calibre.kovidgoyal.net/download_binary")) and mistakenly allowed it to overwrite my Documents folder. Lessen learned: read carefully before entering stuff in the command prompt. This contains not only the past semester's worth of school assignments, but also some other miscellany that I just dump there. So, I am now in search of some way of un-deleting everything I had in the folder. Any tips on how to do so? There were a variety of file types stored there; several variants of .doc and .odt as well as .iso's and some other random downloads.

I am no longer working in my Ubuntu partition for now in order to (hopefully) avoid making the data unrecoverable.

Any help would be greatly appreciated.

---

### Post by lensman3 on 2008-12-15
Maybe just Maybe it deleted your files and put them in the trash.  My trash can is in the ".local/share/trash/files".  You might navigate to that folder and see if anything is there.  Usually under all Unix's a delete is really a delete and is gone forever. 

Navigate to that folder and see if the files are there.  If they are move  them someplace  safe.  Usually, a "rm" just makes them go away, unless you have aliased rm to a copy/move to trash and then delete.

Sorry I don't have much hope.

---

### Post by spencercarran on 2008-12-15
It was not moved to my Trash folder.

---

### Post by jerome1232 on 2008-12-15
As far as I know the only route to go is file carving.

This is a decent how-to for several different methods of file recovery [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

You need another drive to write the recovered files too (Usually the drive needs to be as big as the drive your recovering from) I've personally used foremost and photorec, and like both of them (foremost sorts the files in an easier to sort through way while photorec has a nice interface).

Feel free to ask more questions if you not sure how to proceed with the information I've given.

---

### Post by spencercarran on 2008-12-15
> **jerome1232 said:**
> You need another drive to write the recovered files too (Usually the drive needs to be as big as the drive your recovering from)
You mean like an external HD? And it has to be the size of my entire Ubuntu partition? That's about 50GB... is there a way to use those recovery tools on just a certain directory (ie my user folder)? They should be able to run from livecd right?

---

### Post by jerome1232 on 2008-12-15
There is nothing I know of that can do that, these programs scan through entire partitions. On this site it looks like Carl Wood wrote a program that can undelete files on an ext3 file system.

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

It doesn't look easy to use at all though, and it requires you to be writing the recovered files to another partition as well. Unfortunately that's the most help I can be. In the future it's a very good idea to keep backup's of your personal files, they are priceless at times like these.

---

