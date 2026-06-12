---
title: "partitioning for dual boot help"
date: 2009-05-22
forum: General Help
---

### Post by chulamami on 2009-05-22
Hello!
Let me start by saying this is my first time in trying Linux and the whole dual booting thing (= NOOB). Before I actually do the real installation, I wanna ask for your opinions about my partitioning scheme. I want to dual boot the pre-installed Vista in my laptop (Dell Inspiron 13) and Ubuntu or Linux Mint 6. I have a 320 GB hard drive with 4GB of memory, running Vista home premium 64-bit OS.
 
Checking the disk partitions through Vista, this is what I get:
[http://i37.photobucket.com/albums/e60/askalle/vistapartition.jpg](http://i37.photobucket.com/albums/e60/askalle/vistapartition.jpg)
I'm confused. Does that mean I have 2 partitions or 3? I'm confused about that 39 MB Healthy part.
 
Anyway, if I had 2 partitions, I had 2 plans in mind, with some help from some other guy's partition scheme and psychocat's guide. Feel free to correct the order of my partitions, I'm sure I got that wrong.
A)
1- Primary Vista NTFS 50 GB
2- Primary / (root) ext3 20 GB
3- Primary extended
4- logical /home ext3 20 GB
5- logical swap 6 GB
6- logical shared data (ntfs or ext3?) the rest of GB
4- Primary(?) Recovery (pre-installed Dell thing)
 
B) this one I like more but I'm not sure what to do about the Recovery partition :(
1-Primary Vista NTFS 50 GB
2- Primary File storage and/or /home (NTFS or ext3?) the rest of GB
3- Primary / (root) ext3 20 GB
4- Swap 6 GB
So if I do go with plan B, should 2 (File sotrage and /home) be NTFS or ext3? If I go with ext3, I'm just gonna install FS-driver in Windows so I could read and write into that partition from both OS (following psychocat's partition guide). Would you recommend this?
Also if I do use FS-driver, when do I install it? Before or after partitioning? or before or after the Linux installation?
 
Replies would be appreciated. Thank you! :)

---

