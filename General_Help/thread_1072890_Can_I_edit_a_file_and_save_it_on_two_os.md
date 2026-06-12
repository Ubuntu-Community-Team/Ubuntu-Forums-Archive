---
title: "Can I edit a file and save it on two o/s?"
date: 2009-02-17
forum: General Help
---

### Post by ozguitarplayer on 2009-02-17
I don't even know if this is possible....
I am currently using one hard drive with two partitions, one running Intrepid Ibex and the other Hardy Heron.

I work with files a lot mostly just text documents and mp3's. 
I need to keep the files up to date on both o/s.

Is it possible, and if so how do I set it up so that if I am using one system and I edit and save a file it is automatically saved in the files on the other o/s?

---

### Post by lilbill on 2009-02-17
No problem there.  Can you describe how you have your partitions set up?  

If you have separate /root partitions but a shared /home partition where the documents and whatnot are stored then each OS would simply read and write the files.

Otherwise you will need to come up with another approach...but we'll look into that later after we see how your disk is set up.

P.S. now that Ubuntu supports NTFS reading and writing you could also read and write files on a windows disk/partition!

---

### Post by ozguitarplayer on 2009-02-17
I'm a novice at this so here goes...this is what GParted says...
   
/dev/sda1      ext3      (Intrepid Ibex-installed first)  
/dev/sda2      extended  (and listed with this one with the drop down arrow)
   /dev/sda6   ext3      (Hardy Heron-installed second)
   /dev/sda7   linux-swap
   /dev/sda5   linux swap

Each ext3 is about 230Gig

you mention a home partition that both could read from, that sounds like a good option...

and I do have windows XP on a seperate HDD, if it's simple to configure that also
I will but the main issue is the two Ubuntu systems

---

### Post by handy on 2009-02-17
You may grow to love this site: :-)

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*

---

### Post by ozguitarplayer on 2009-02-18
thanks for that....haven't read it yet, but will tonight...and yeh it's a great site

---

### Post by heindsight on 2009-02-18
It's probably not the best idea to share your home directory between two different ubuntu versions. different different versions of some programs may expect their configuration files/directories in your home to look slightly different or (more likely) a newer version of a program may put options in the config file that break the older version.

You'd be better off creating a separate data partition and then sharing that between the two installations. For example, you could make a big partition and mount it at /home/yourusername/data, then create Documents Music etc directories on the new partition and replace the Documents Music etc. directories in your home dir with symlinks to the directories on the data partition.

btw. I notice you have 2 swap partitions. You only need one, because you definitely can share a swap partition between the two installs.

---

### Post by ozguitarplayer on 2009-02-18
thanks heindsight, there is more to it than I thought
...what if I had the files on only one partition and o/s and could edit the files with that o/s as well as the o/s on the other partition, or is that going to pose the same problems as you mentioned in your reply?

---

### Post by heindsight on 2009-02-18
> **ozguitarplayer said:**
> thanks heindsight, there is more to it than I thought
...what if I had the files on only one partition and o/s and could edit the files with that o/s as well as the o/s on the other partition, or is that going to pose the same problems as you mentioned in your reply?

It shouldn't cause a problem. When you're running Intrepid, you could mount the partition on which you installed Hardy at say /media/hardy and then access any files from your hardy install there (and the other way round).

I think it would be easier though to just create a data partition on which you save all the files that you want to be accessible from both Hardy and Intrepid and mount that somewhere under your home directory. That way, you can access the files in the same manner in the same place in both installations.

---

### Post by ozguitarplayer on 2009-02-18
OK I'll do that, it does sound best, thanks for you help heindsight...much appreciated

---

### Post by binbash on 2009-02-18
getdropbox.com ;)

---

