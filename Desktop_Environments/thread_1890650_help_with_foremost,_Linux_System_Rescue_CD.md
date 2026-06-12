---
title: "help with foremost, Linux System Rescue CD"
date: 2011-12-04
forum: Desktop Environments
---

### Post by blompy on 2011-12-04
I have made an image file with DDrescue and I'm trying to extract files from it using Foremost on the Linux System Rescue CD.
 
The ddrescue image file is stored on an ext4 partition. The partition that I'm trying to extract the files to is also an ext4 partition.
 
Here is what I do. First I create a directory to mount the drive for the output and then I mount the drive:
 
mkdir /mnt/sdb3
 
mount /dev/sdb3 /mnt/sdb3
 
The partition that the image file is store on is sdb2. So when I run foremost I type:
 
foremost /dev/sdb2/image.img /mnt/sdb3
 
 
Then I get this error: 
 
Error: /root/output is not empty Please Specify another directory or run with -T
 
 
I try creating another directory for the Foremost output by typing: mkdir /mnt/sdb3/output
 
Then I type:
 
foremost /dev/sdb2/image.img /mnt/sdb3/output
 
and it gives me the same error. Next I try it with -T and all I get is:
 
"Processing Stdin" (that's all it does...It just sits there and says that)
 
I used Foremost on in a regular Ubuntu desktop installation (not a rescue cd) and it doesn't give me this trouble.
 
Could someone toss me a bone please. thanks

---

### Post by jaimeaux on 2011-12-04
Which System Rescue cd is it? Personally I prefer to use Partimage/Partimaged if that helps at all. Not sure if it does.

---

### Post by fdrake on 2011-12-04
> **blompy said:**
> I have made an image file with DDrescue and I'm trying to extract files from it using Foremost on the Linux System Rescue CD.
 
The ddrescue image file is stored on an ext4 partition. The partition that I'm trying to extract the files to is also an ext4 partition.
 
Here is what I do. First I create a directory to mount the drive for the output and then I mount the drive:
 
mkdir /mnt/sdb3
 
mount /dev/sdb3 /mnt/sdb3
 
The partition that the image file is store on is sdb2. So when I run foremost I type:
 
foremost /dev/sdb2/image.img /mnt/sdb3
 
 
Then I get this error: 
 
Error: /root/output is not empty Please Specify another directory or run with -T
 
 
I try creating another directory for the Foremost output by typing: mkdir /mnt/sdb3/output
 
Then I type:
 
foremost /dev/sdb2/image.img /mnt/sdb3/output
 
and it gives me the same error. Next I try it with -T and all I get is:
 
"Processing Stdin" (that's all it does...It just sits there and says that)
 
I used Foremost on in a regular Ubuntu desktop installation (not a rescue cd) and it doesn't give me this trouble.
 
Could someone toss me a bone please. thanks

did you check the manual? i think it should be like this:
"man foremost"
```

foremost -i /dev/sdb2/image.img -o /mnt/sdb3/output

```

---

### Post by blompy on 2011-12-04
ah shoot, I tried the way you suggested before I read your reply and I got the "Processing stdin ..."  output
 
That means it working because I checked the output directory after it started and I'm seeing activity. That's the output I got from some of the other ways I tried.  I think where I went wrong is that when I use foremost before is would display a bunch of code and gibberish moving down the screen as it extracted files, butt in this instance it's not doing that, so I assumed it wasn't working.#-o
 
Anyway, I went ahead and just started the extraction the way you said and it's working now.
 
thanks

---

### Post by jaimeaux on 2011-12-04
So, can this be marked as [Solved]?

---

### Post by fdrake on 2011-12-04
> **blompy said:**
>  when I use foremost before is would display a bunch of code and gibberish moving down the screen as it extracted files

you are looking for the verbose option:

```

foremost -v -i /dev/sdb2/image.img -o /mnt/sdb3/output

```

---

### Post by blompy on 2011-12-05
Looks like I'm still in the hole. Foremost created the output directories for the extracted files but after running all night I looked in the directories and there's nothing in them. :confused:
 
Here's the situation. The hard drive had that I made the image of had Windows Vista installed and a bunch of jpeg and .m4a music files on it. I used Windows Easy Transfer to back up the data and then I reinstalled Windows. When I attempted the migration it failed because apparently the SaveData.img (Easy Transfer file) is corrupted. I was able to recover some of the files from the SaveData.img file using MigRecover, but most of the files are corrupted.
 
I'm thinking that even though Windows was installed and possibly written over the hard drive sectors with the music and jpeg files are, they may possibly be there still, or at least some of them.
 
When I try it with verbose mode enabled it shows that foremost started but it doesn't show any activity... In other words, no gibberish or code floating down the screen.
 
 
any more ideas ? thanks

---

### Post by fdrake on 2011-12-05
when you run the command does it show any error mesgs? you can try with no error detection and see if it brings something out.
```

foremost -av -i /dev/sdb2/image.img -o /mnt/sdb3/output

```

beside that if the image is corrupted thereisn't much you can do, maybe someone else has a better idea..

---

### Post by blompy on 2011-12-05
I got it working.  I can see data being extacted.  For some reason foremost is having a problem reading or writing to ext4 files systems, so I put the image file on an NTFS partition and formated the output partition to ext3, which worked.
 
But now there's another problem.  After running for a few mintues, I get an error telling me there's no more room on the output partition.  I don't get that because the image file is approx. 100 gigabytes and the output partition is approx. 1 Terabyte.
 
:confused:

---

### Post by blompy on 2011-12-06
Found a solution to the lastest problem.
 
I mounted both the input and output directories, then:
 
foremost -T /mnt/sdb1/image.img -o /mnt/sdb2/recover
 
 
gee wiz...   :P

---

