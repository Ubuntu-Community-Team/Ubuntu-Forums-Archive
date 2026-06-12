---
title: "Can't install ubuntu due to unspecified root drive"
date: 2011-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Shieldmaster on 2011-05-26
Hello,
     I've recently moved over to Ubuntu on my IBM X-31 and decided to move to Ubuntu on my new Dell insprion 1545. but the problem is when I install Ubuntu to run along with windows, I followed the same directions I used when I installed Ubuntu on my IBM and I booted my computer on ubuntu and it gave me a unspecified root drive and told me to specify in the partition table window. The second problem is I had pre-formated a 50GB NTFS drive but the partition window then tells me it is unusable and my windows partition is usable and its also a NTFS but it olny has about 11GB left. Is there any way to fix any of these? 

Thank you in advanced.

My computer runs in X64 win7,4gb of memory, and has a Pentium dual core

---

### Post by oldfred on 2011-05-27
Welcome to the forums.

Most win7 computers use all 4 primary partitions leaving no space for anything else. Windows uses 2, a (hidden) 100MB boot/recovery partition, the main install. Then the computer vendor uses two - one for the DVDs they did not give you and it is just an image not an install disk and some sort of misc utilities taking a whole partition.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.

Post this to see partitions:

```
sudo fdisk -lu
```

---

### Post by Shieldmaster on 2011-05-27
Thank you for your help. I moved my partitions around and rebooted my computer, but now there is a error where it cant find the required files, and then it tells me that one of my devices were not safely removed. Then it tells me to run the chkdsk /r to fix the problem. I did that and now it always displays the same error.
Is there a fix to this?

Thank you, Sorry of any inconvenience.

---

### Post by oldfred on 2011-05-27
If you moved partitions, so they have different partition numbers then than is an issue.

Post this to see what is where from liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

