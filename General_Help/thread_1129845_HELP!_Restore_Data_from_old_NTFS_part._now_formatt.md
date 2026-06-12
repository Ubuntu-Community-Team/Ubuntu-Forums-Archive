---
title: "HELP! Restore Data from old NTFS part. now formatted with ext3"
date: 2009-04-19
forum: General Help
---

### Post by chnorth on 2009-04-19
Hello!
I hope this is the right place to post this. Please excuse my first post being a cry for help already but I messed up quite a bit.

I had Windows running on a NTFS partition. When trying to install a ubuntu server to an external usb drive, I must have made a mistake and installed it over my ntfs windows partition instead!

So the original NTFS partition is ext3 now and the first 1.7GB of the total 18GB are overwriten.

Do you know of any possibility to restore parts of my NTFS data that was on the drive previously?

(Unfourtunately I find so much dubious software on google. And I dont't want to mess up more.)


Thank you! This is a great help!

chnorth

---

### Post by StuartN on 2009-04-19
Did parted shrink NTFS or overwrite it? If it was shrunk then there will be a readable NTFS partition (which you can mount in Nautilus and check the contents), but if the start of it was overwritten then it will appear unformatted.

Once the partition tables in NTFS have been overwritten it is impossible to locate the files in the remainder of the partition, so recovering any data will be very, very difficult. There are forensic tools that examine the bytes to reassemble file fragments and recover data, but nothing easy to use as far as I know. I think your NTFS data is effectively gone.

---

### Post by benerivo on 2009-04-19
Check what Doug11 has said in this post...

[http://ubuntuforums.org/showthread.php?t=1093440](http://ubuntuforums.org/showthread.php?t=1093440)

---

### Post by louieb on 2009-04-19
Two programs that can help recover data from a formated partition:   testdisk and photorec. 
Both can be found on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by theozzlives on 2009-04-19
Hence, the reason why you backup often. I've lost data more times than I can count. It's a bummer.

---

### Post by HavocXphere on 2009-04-19
Yeah, you'll get some data back..but not all of it.

I'd recommend GetDataBack (NTFS version). It's not free and it needs to run off windows, so you'll probably need to put the disk in another PC. Oh and it takes long. Probably a couple of hours for 18gb. I've had good luck with it saving data off harddrives that were damaged and(!) formatted.

---

### Post by chnorth on 2009-04-19
Thank you all for the help so far!

I have been able to get back a few important text and pdf files with photorec. 
Still I need to find a few files, that photorec does not support.

(By the way: I have a feeling photorec finds *.docx files as archives. And probably finds my Mindmap-files *.mm as xml files.) What a mess!

I will give GetDataBack a try but as you say, I will first have to install Windows again.

Does anybody know a Linux/Ubuntu alternative for GetDataBack?

Thanks!

P.s. The directory structure has probably gone completely, has it?

---

### Post by chnorth on 2009-04-20
So - the problem seems to be solved:

I managed to get most of my data back and even got the right folder structure.

I had to use GetDataBack in combination with a Windows PE cd. (Hieren's Boot CD)

Just have to think of a secure new setup now which runs windows and ubuntu and has sufficient backup functions.

Thanks again

---

