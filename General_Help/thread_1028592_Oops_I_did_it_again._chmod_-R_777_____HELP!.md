---
title: "Oops I did it again. chmod -R 777 /    HELP!"
date: 2009-01-02
forum: General Help
---

### Post by linuxisevolution on 2009-01-02
I was going to change a file's permission on my server, but I was tired, and forgot to login via ssh onto my server, and I fogot to type more than just / :P So... Did I just make my whole filesystem read-write? It's ambaressing for someone like me to make a mistake like this. . . . I guess everyone makes mistakes. Will this harm my system at all?



What I learned:

Don't read, eat soup, drink vodca, and try to chmod something at the same time :D


EDIT: Now sudo won't work.

> winrid@winrid-desktop ~ $ sudo apt-get install something
sudo: must be setuid root


Thanks!

---

### Post by linuxisevolution on 2009-01-02
I accidentally ran chmod -R 777 /  . Refer to this thread as to why in the hell I did that...

[http://ubuntuforums.org/showthread.php?p=6481169#post6481169](http://ubuntuforums.org/showthread.php?p=6481169#post6481169)


Anyway, now, I can run ANY program that requires root permission, without root permission. Not good. How do I fix this?

I've been looking for a reason to reinstall. . .:(

---

### Post by my_key on 2009-01-02
If you don't have backups, it's best to reinstall.

---

### Post by linuxisevolution on 2009-01-02
> **my_key said:**
> If you don't have backups, it's best to reinstall.

Is there a much harder alternative? I do have LOTS of things in my home directory. 220gb used of 250gb. I don't have room for backups :(

---

### Post by my_key on 2009-01-02
Do you have /home on a different partition? If so it's fine to just reinstall. During partitioning you need to mark something like "don't format" or "keep data".

If you don't have /home on a different partition I would advice buying an external usb harddrive to back it up first. They're not that expensive and it's a good thing to make regular backups anyway. Remember to set permissions to your liking afterwards.

---

### Post by HermanAB on 2009-01-02
Re-install.  It only takes about 30 minutes.

Always make a separate /home partition so you can re-install without wiping your data.

Cheers,

Herman

---

### Post by cdenley on 2009-01-02
You could shrink your existing partition to give you enough room to install ubuntu on the free space, then delete all your files outside of /home, move /home to the root, and use the original, large partition as /home on the new install. Resizing will probably take a long time, though.

---

### Post by jdackle on 2009-01-02
> **cdenley said:**
> You could shrink your existing partition to give you enough room to install ubuntu on the free space, then delete all your files outside of /home, move /home to the root, and use the original, large partition as /home on the new install. Resizing will probably take a long time, though.
That would probably be best, I guess.
But I was going to suggest to reinstall every package already installed on your system (as in go to Synaptics -> State-tab -> Installed , select all packages (CTRL+A), <mouse right-click>, "Renstall".
I guess that would bring all the files from those packages brought back to their original state (not sure about directories though; but you can have a try with whatever one package, before you reinstall everything, and see how it goes).

This should basically do the same as the above method but W/O repartitioning the drive and having a /home partition separated from the rest of /.

Then again, specially if you cannot do frequent backups of everything (or plain workable, "packed" by say date-of-change), having /home separated from the system tree would be VERY WISE.

---

### Post by bodhi.zazen on 2009-01-04
IMO best to have a data partition rather then a separate home partition.

At any rate, the permissions of /home are easy to fix. The rest of the file system will be much much harder and take more time then re-installing.

So back up or move your data and re-install.

---

### Post by bodhi.zazen on 2009-01-04
Threads merged.

linuxisevolution: Please do not start multiple threads on teh same topic is causes confusion and duplication of effort.

Also this is not a security issue so I moved your thread(s) to general help.

---

### Post by linuxisevolution on 2009-01-05
> **bodhi.zazen said:**
> Threads merged.

linuxisevolution: Please do not start multiple threads on teh same topic is causes confusion and duplication of effort.

Also this is not a security issue so I moved your thread(s) to general help.

I don't remember creating another thread for this topic. Did I? I am sorry if I did hehe. Thanks for moving the thread and letting me know it wasn't a security issue. BTW, I'm using my other Ubuntu partition ( I have 4 partitions with distros on them ) so I will be good until I have the time to reinstall on the other one.. I copied all the files over from that install anyway, and that partition was having buffer I/O errors...

---

### Post by bodhi.zazen on 2009-01-05
No problem, lol

---

