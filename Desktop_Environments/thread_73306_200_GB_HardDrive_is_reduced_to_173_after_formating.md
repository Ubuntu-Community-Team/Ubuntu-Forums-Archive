---
title: "200 GB HardDrive is reduced to 173 after formating."
date: 2005-10-08
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2005-10-08
Hello everybody.
There is something intriguing me a lot. I've just bought a new 200 GB hard drive and when I make it works as one partition (formated as ext3 with qtparted) the final result is merely 173 GB of free disk space. The qtparted indeed shows me that the total capacity of the disk is 183 GB but with 9,5 GB been used. 
Who the heck is using my disk? There is just a lost+found folder, but it is empty.
I know this must be an easy question to solve, but I don't have a clue.

Thanks!

---

### Post by zerhacke on 2005-10-08
The filesystem itself has overhead.  What I mean is that the act of partitioning and formatting takes some space for various reasons.

---

### Post by madjo on 2005-10-08
to what filesystem was it formatted? some filesystems are less conservative with their file allocation tables (the place where the metadata of your files (filesize, date of creation, owner etc.) are stored).

---

### Post by Marcos.Rufino on 2005-10-08
[QUOTE=madjo]to what filesystem was it formatted? some filesystems are less conservative with their file allocation tables (the place where the metadata of your files (filesize, date of creation, owner etc.) are stored).[/QUOTE]

ext3

Is there a better file system as far as a better use of space?

---

### Post by madjo on 2005-10-08
hmmm ext3 is normally a very suitable filesystem for large partitions, but it could very much be, that 200gb in a single partition might just be too large.

I think it would be much better (also performance-wise) to make a few shorter partitions.

---

### Post by Marcos.Rufino on 2005-10-08
Thank you guys for the help!

---

### Post by matthew on 2005-10-08
Another factor is this: manufacturers refer to hard drive size in gigabytes, which is 1,000,000,000 bytes. A computer addresses the space using gibibytes (no, I didn't make that up) which are 1,073,741,824 bytes. When hard drives were smaller the difference was so nominal people didn't notice. Now that the hard drive sizes are larger it becomes noticable and causes questions like yours to arise. Confusing? Yes.

So all your space is there, it's just being reported in a fashion that makes it look like less or more depending on the perspective you look from.

Here's a link for more information:  [http://www.computerhope.com/help/hdd.htm]("http://www.computerhope.com/help/hdd.htm")

---

### Post by madjo on 2005-10-08
hmm never heard the term gibibytes before (And I'm supposed to be an IT professional).. but you are right that manufacturers like to round up the numbers in GB. indeed... they use the 1000MB or 1,000,000,000 bytes for a GB, while a computer uses 1024MB (1024x1024x1024 in bytes) for a GB.

---

### Post by matthew on 2005-10-08
[quote=madjo]hmm never heard the term gibibytes before (And I'm supposed to be an IT professional).. but you are right that manufacturers like to round up the numbers in GB. indeed... they use the 1000MB or 1,000,000,000 bytes for a GB, while a computer uses 1024MB (1024x1024x1024 in bytes) for a GB.[/quote]
I have never heard anyone use it, so I don't know precisely how it would be pronounced. I have seen it in print two or three places, though. You expressed the idea well, though...better than I did originally. :) Clear and succinct.

---

### Post by kafton on 2005-10-09
> There is something intriguing me a lot. I've just bought a new 200 GB hard drive and when I make it works as one partition (formated as ext3 with qtparted) the final result is merely 173 GB of free disk space. The qtparted indeed shows me that the total capacity of the disk is 183 GB but with 9,5 GB been used.

ext3 is a journalling file system and uses space for the journal. Your 9.5 Gb is that journal, I think.

---

### Post by mcduck on 2005-10-09
[QUOTE=matthew]I have never heard anyone use it, so I don't know precisely how it would be pronounced. I have seen it in print two or three places, though. You expressed the idea well, though...better than I did originally. :) Clear and succinct.[/QUOTE]I've been using computers for 18 years now, and I've never heard that term until recently. To me, Kilobyte has always been 1024 bytes, and megabyte 1024 Kilos etc. In the beginning HDDs used the same sizes also, so I think that terms like MiB and GiB are just HDD manufacturer's way to make people think that they are the ones using right sizes and computers just work with wrong ones.. ;) Personally, I refuse to use these terms at all. :D

---

### Post by matthew on 2005-10-09
[quote=mcduck]I've been using computers for 18 years now, and I've never heard that term until recently. To me, Kilobyte has always been 1024 bytes, and megabyte 1024 Kilos etc. In the beginning HDDs used the same sizes also, so I think that terms like MiB and GiB are just HDD manufacturer's way to make people think that they are the ones using right sizes and computers just work with wrong ones.. ;) Personally, I refuse to use these terms at all. :D[/quote]
That's okay, no one else uses them either--myself included.

---

### Post by madjo on 2005-10-09
@matthew, 
heh, I just noticed your sig ;)

> AOpen 1557GLS laptop, Pentium M 745 (1.8 GHz), 1 **Gb** ram, 80 **Gb** hdd, ATI MobRad 9700 128 mb @ 1400x1050, Intel ipw2200b/g
1 Gigabit ram? 80 Gigabit harddrive? :)
I was told that the smaller b in Gb and Kb stands for bit and the capital B stands for byte. I just thought it was funny.

just fooling around a little :) (btw thank you for the compliment you made earlier).

@mcduck, interesting theory indeed that GiB was made up by the harddisk mft's. I think you are correct. :)

---

### Post by kaaven on 2006-04-02
In 1998 the International Electrotechnical Commission (IEC) changed the name from gigabyte (GB) to gibibyte (GiB) for use with the binary system. You can read one of many articles about the subject [here]("http://www.romulus2.com/articles/guides/misc/bitsbytes.shtml").

---

