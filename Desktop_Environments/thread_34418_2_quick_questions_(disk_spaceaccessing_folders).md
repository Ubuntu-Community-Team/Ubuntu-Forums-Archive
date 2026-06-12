---
title: "2 quick questions (disk space/accessing folders)"
date: 2005-05-14
forum: Desktop Environments
---

### Post by Euphoric Nightmare on 2005-05-14
Okay, like i said in the title, I have two questions.

The first one perplexed me for hours this morning:

I created a partition (4 GB), and mounted it as /packages.  This was to be used basically as a package mirror as I don't have internet.  If I navigate to this folder using nautilus, it tells me that there is 800 MB (or so) free, but that its a 4GB media volume.  Even as root, it won't let me copy all of my packages in there because it runs out of space.  there is only 2.15 Gigs worth of packages.  The only thing that is in there is the lost+found dir.  it does not occupy much space, even according to nautilus.  Where is all my disk space?

The second one is not as big of a deal..but:

I prefer to browse around in the terminal emulator.  But, if I have a directory or file name that is more than one word, it doesn't appear to let me navigate there, it gives me ">" on a new line implying that I haven't finished my command yet.  I know there is a way to do this...but I don't know how.  How can I get to these directories?

I would appreciate any suggestions as always.  Thank you in advance.

---

### Post by nad on 2005-05-14
I've read and replied to other posts trying to answer the disk space issue. You are correct that root should be able to max out the volume. Out of curiosity, what is the total available space on this drive?

As far as working with spaces and other characters in file names, single quotes will cover the space problem. You will need double quotes for file names with characters such as single quotes.

---

### Post by Ali_Baba on 2005-05-14
For your second question, [http://www.ubuntuforums.org/showthread.php?t=34401](http://www.ubuntuforums.org/showthread.php?t=34401)
here are some good help for browsing files.

---

### Post by Euphoric Nightmare on 2005-05-14
Why wouldn't root be able to max out this partition?  I just don't get it...why can't I use even 25% of this partition?

EDIT:  Okay, i have the "ls" situation understood...but i'm still wondering about the /packages partition.  I can put everything on ~/, and /root...but not /packages.

---

### Post by void_false on 2005-05-15
Maybe you should try resize2fs. I think you created partition of 4G and filesystem of  800M.

---

### Post by Euphoric Nightmare on 2005-05-15
[QUOTE=void_false]Maybe you should try resize2fs. I think you created partition of 4G and filesystem of  800M.[/QUOTE]

is it possible that I deleted the partition, and created a new one, and didn't create a filesystem?

If that is the case then this should work, correct?:
mke2fs -j /dev/sda8

---

