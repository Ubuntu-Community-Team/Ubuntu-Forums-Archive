---
title: "cannot delete duplicate system file on seperate partition"
date: 2009-06-03
forum: General Help
---

### Post by decomp on 2009-06-03
Hello all! First of I'm new to the forum, thanks for all the great info I've found in my ~ 1 1/2 months reading. So far ubuntu is awesome.

My problem:
I have file on a second partition that I am unable to delete even as root.

Sorry this is a bit lengthy but I don't know how else to explain.

I will note that this is a repost from absolute beginner help, and I apologize, but obviously I had placed this post in the wrong section.
(in the future, should I request an admin move it for me or what?)
the original post is viewable here: 
[http://ubuntuforums.org/showthread.php?t=1172555](http://ubuntuforums.org/showthread.php?t=1172555)
but I have copied all relevant info.

I have my computer set up with a partition for ubuntu system and a second partition for my home directory. I mucked up my ubuntu install when I didn't have a live cd to reinstall from, so I tried to reinstall using unetbootin from my second partition (normally my home partition.) That didn't work (got stuck in some kind of loop at the partitioning stage) so once I got around to getting an install cd again I reinstalled ubuntu from that. Problem was that if I tried to use my second partition as my home directory again, after install ubuntu would just boot into a blank screen. So I deleted all personalized home directory files except for my music & documents, which I placed in a seperate folder. reinstalled again, to no avail. I discovered the file extlinux.sys, which I believe is left over from the failed unetbootin install, lingering on this second partition. I tried to delete it but even as root i get:

```

decomp@decomp-laptop:/media/disk$ sudo rm extlinux.sys
[sudo] password for decomp: 
rm: cannot remove `extlinux.sys': Operation not permitted

```
I would really like to change my home directory back to this partition, but while this file is lingering I know I will always be booting into a blank screen. Can anyone help me?

Please let me know if theres any information you would like about my system.

basic info: ubuntu jaunty 9.04 on a sony vaio pcg-v505 laptop.

troubleshooting steps already tried:
1) 
deleting with sudo rm -f extlinux.sys (suggested by Paqman) with the results:
```

decomp@decomp-laptop:/media/disk$ sudo rm -f extlinux.sys
[sudo] password for decomp: 
rm: cannot remove `extlinux.sys': Operation not permitted

```

2) deleting the file graphically with gksudo nautilus with the results:
Error deleting file.
There was an error deleting extlinux.sys.
Error removing file: Operation not permitted.

3) deleting from live cd - same results (suggested by michy99)
4) run a file system check - came out fine (suggested by mikechant)
5) 'delete by inode number' which is described here: [http://www.cyberciti.biz/tips/delete...de-number.html](http://www.cyberciti.biz/tips/delete...de-number.html) (suggested by mikechant) with the following results:

```

decomp@decomp-laptop:/media/disk$ stat extlinux.sys
  File: `extlinux.sys'
  Size: 13312     	Blocks: 32         IO Block: 4096   regular file
Device: 803h/2051d	Inode: 269911      Links: 1
Access: (0444/-r--r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-05-29 16:42:19.000000000 -0600
Modify: 2009-05-22 16:51:52.000000000 -0600
Change: 2009-05-22 16:51:52.000000000 -0600
decomp@decomp-laptop:/media/disk$ sudo find . -inum 269911 -exec rm -i {} \;
rm: remove regular file `./extlinux.sys'? y
rm: cannot remove `./extlinux.sys': Operation not permitted

```

further info: checked extended attribute set with getfacl extlinux.sys
(suggested by The Cog) with the results:
```

decomp@decomp-laptop:/media/disk$ getfacl extlinux.sys
# file: extlinux.sys
# owner: root
# group: root
user::r--
group::r--
other::r--

```
Thank's for reading!

D

---

### Post by decomp on 2009-06-03
Oh and I've also tried to change the owner of the file with chown:

```

decomp@decomp-laptop:/media/disk$ sudo chown -R decomp extlinux.sys
chown: changing ownership of `extlinux.sys': Operation not permitted

```

---

### Post by michy99 on 2009-06-03
The file is read-only. Try```
sudo chmod 777 extlinux.sys
sudo rm extlinux.sys
```

---

### Post by decomp on 2009-06-03
> **michy99 said:**
> The file is read-only. Try```
sudo chmod 777 extlinux.sys
sudo rm extlinux.sys
```

Hi michy99,

tried that with results:

```

decomp@decomp-laptop:/media/disk$ sudo chmod 777 extlinux.sys
chmod: changing permissions of `extlinux.sys': Operation not permitted

```

---

### Post by michy99 on 2009-06-03
This is a real stumper. I would be tempted to reformat the whole partition just to get rid of it.

---

### Post by decomp on 2009-06-03
> **michy99 said:**
> This is a real stumper. I would be tempted to reformat the whole partition just to get rid of it.

michy99,

I would too except i don't have an external hard drive, no money to buy one, and i have nowhere to move all my personal files too :(

---

### Post by michy99 on 2009-06-03
I may have the answer!```
sudo chattr -i extlinux.sys
sudo chmod 777 extlinux.sys
sudo rm extlinux.sys
```

---

### Post by decomp on 2009-06-03
> **michy99 said:**
> I may have the answer!```
sudo chattr -i extlinux.sys
sudo chmod 777 extlinux.sys
sudo rm extlinux.sys
```

michy99 your a genius! Success!

```

decomp@decomp-laptop:/media/disk$ sudo chattr -i extlinux.sys
[sudo] password for decomp: 
decomp@decomp-laptop:/media/disk$ sudo chmod 777 extlinux.sys
decomp@decomp-laptop:/media/disk$ sudo rm extlinux.sys
decomp@decomp-laptop:/media/disk$ ls
dylansstuff  lost+found

```

It's gone! Thanks for your help!

---

### Post by michy99 on 2009-06-03
I wish I could take credit, but I found the answer here:

[http://ubuntuforums.org/archive/index.php/t-1091230.html](http://ubuntuforums.org/archive/index.php/t-1091230.html)

---

