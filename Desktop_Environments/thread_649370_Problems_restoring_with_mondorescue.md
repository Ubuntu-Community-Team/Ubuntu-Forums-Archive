---
title: "Problems restoring with mondorescue"
date: 2007-12-24
forum: Desktop Environments
---

### Post by hardskinone on 2007-12-24
Hi,
after a fresh gutsy installation I trying to restore my /home directory from a mondorescue backup. I full mondoarchived my old system (Fedora 7) in a ISOs set on an external usb disk.

After selected "hard disk" in mondorestore menu the software ask me the full path where ISOs lives then the software correctly shows me the archive's file list. I select my /home directory, I choose where files will be restore. mondorestore try to read from cd then the software simple exit

```
Execution run ended; result=0
Type 'less /tmp/mondorestore.log' to see the output log
```

Anybody out there?
Thanks

---

### Post by sciencewhiz on 2007-12-26
can you post the mondorestore.log

---

### Post by G0rt3k on 2008-02-17
m8,

I got exactly the same problem... I solved making a downgrade of the mondo package.

First remove it:

```
dpkg -P mondo
```

Then I got this version (2.2.5):

```
wget http://mondorescue.muskokamug.org/ubuntu/7.10/special/mondo_2.2.5_i386.deb
```

And, install it...

```
dpkg -i mondo_2.2.5_i386.deb
```

Finally restore what you want!!
Hope that works 4all !!

---

### Post by yanik on 2008-03-18
that post just saved my ***.

thanks G0rt3k.


A backup is useless if you can't restore!

---

### Post by martinlall on 2008-04-11
I have also problems with mondorestore. 
First of all i also downgraded mondo. Then i got rid of the "result=0" problem. But..

..i got 2 4,5GB isos from backing up my drive. And when i try to restore it everything goes smooth until 42%. From there it keeps asking me the #2 iso, but I already gave the right directory at the beginning. And it perfectly loads and restores 100408-1.iso. Iso names are 100408-1.iso and 100408-2.iso. They are on my desktop and backup copys are on my other hard drive. I haven't edited their names or anything.

Why doesn't mondo undrestand where is the "100408-2.iso"?
The reason why i cant boot from dvd is - iso is too big for dvd, although iso files are 4,4gig in ubuntu and in microsoft mashines 3,99gigs. And dvd's are like always, 4,7. 

Have tried '/home/lall/Desktop' location ehere are those isos and '/media/Disk' where are the same isos. No luck so far.

Any clue?

M

---

