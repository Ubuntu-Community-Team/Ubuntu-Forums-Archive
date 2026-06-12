---
title: "Gnome CD/DVD burner won't burn 4.3GB of data to a 4.7GB DVD in Gutsy"
date: 2007-12-13
forum: Desktop Environments
---

### Post by vemon on 2007-12-13
Hi!

I tried to burn a directory full of files (4.3GB) with the Gnome CD/DVD burner that can be accessed through Nautilus. It says that the there's not enough space to burn the data even though the DVD should be able to hold 4.7GB. I've successfully burnt CD's with that drive before but I think I haven't tried to burn DVD's before in Gutsy (in Feisty I have successfully burnt DVD's).

Have I just done something wrong or is this normal behaviour for the Gnome CD/DVD burner?

- Jaakko

PS. I'm sure the disc is empty since I just unwrapped it :)

---

### Post by danwood76 on 2007-12-13
You are obviously falling into the good old trap that memory manufacturers create.

4.7GB on a DVD (or a hard disk) is 4,700,000,000 bytes where as 4.7GB is actually 5,046,586,572 bytes.

The difference is because the CD/Hard Drive manufacturers use the decimal counting system for bytes whereas in computers its the binary system.

For example in binary system 1024 bytes make a kilobyte in decimal its 1000.
The only reason for this I can see is that it makes their disk sizes sound bigger but it just messes a lot of people up!

4.3GB is the maximum you can fit onto a DVD-R, try reducing the file size by a few hundered megs and see if it works! ;)

---

### Post by tech9 on 2007-12-13
> **danwood76 said:**
> You are obviously falling into the good old trap that memory manufacturers create.

4.7GB on a DVD (or a hard disk) is 4,700,000,000 bytes where as 4.7GB is actually 5,046,586,572 bytes.

The difference is because the CD/Hard Drive manufacturers use the decimal counting system for bytes whereas in computers its the binary system.

For example in binary system 1024 bytes make a kilobyte in decimal its 1000.
The only reason for this I can see is that it makes their disk sizes sound bigger but it just messes a lot of people up!

4.3GB is the maximum you can fit onto a DVD-R, try reducing the file size by a few hundered megs and see if it works! ;)

+1

good advice danwood76

---

### Post by vemon on 2007-12-14
OK, so to get the accurate figures one would have to do:

(4,7*1000^3) / (1024^3) = ~4,377GB

Funny how that's never crossed my mind. I don't remember having this problem with CD's before. But thanks for the explanation :) I'll try to reduce the amount my data before burning the DVD.

---

### Post by Lostincyberspace on 2007-12-14
The difference isn't as big in cds.

---

### Post by danwood76 on 2007-12-14
> **vemon said:**
> 
(4,7*1000^3) / (1024^3) = ~4,377GB


To put it more conventionally:

4.7x10^9 / 2^30 = 4.377GB

I just thought I'd re-iterate with the correct bases to give more of an impression.
Hope it helps.

---

