---
title: "GRUB is not there anymore"
date: 2009-05-08
forum: General Help
---

### Post by jhonyrod on 2009-05-08
Well, after connect (just connect!!!!) a "new" hd to my pc, grub is not there anymore, my pc says nothing when I try to boot from the hd where is installed ubuntu, the disk is gpt and is patritioned like this:

4   GB  Linux Swap  Swap
15  GB  EXT4        Ubuntu Root
30~ GB  NTFS        Win Data
100 GB  ReiserFS    Ubuntu Data

I tried the grub command way, and even when it looks like work it doesn't make any change to my problem

And it is not dual boot, at least on the same HD, win is on another hd (also I tried to install it on the same hd, but since it is gpt I cant figure out how can I install it, if anyone knows, please tell me)

PS. Sorry for my bad english.

---

### Post by MysticalRiotCandy on 2009-05-08
It sounds like the BIOS is prioritizing your new HDD to boot up instead of your older one.
Have you tried taking out the secondary HDD, and then booting up from the first HDD where Ubuntu was originally installed?

If GRUB still isn't there, you might have to reinstall it by using a LiveCD using [this]("http://ubuntuforums.org/showthread.php?t=224351") method.

---

### Post by jhonyrod on 2009-05-08
Yes, I've already took off the hd, and the bios say that is booting from the old one (where I had installed kubuntu)

Also I've already tried reinstalling GRUB too (grub, find /boot/grub/stage1 ...) and it doesn't fix my problem

PS. Thanks you for your fast answer

---

### Post by caljohnsmith on 2009-05-08
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Miljet on 2009-05-08
Ya think maybe he knows how to do it now?

---

### Post by jhonyrod on 2009-05-08
Ok, I'm downloading a copy of SysRescCD, cause I lost my cd and I cant access to my files to burn it again, i'll post it later

Thanks again for the quick answering

[SIZE="1"]PS (as usual): please guys, I'm not so noob[/SIZE]

EDIT: I'll attach the out of that script...

---

### Post by caljohnsmith on 2009-05-08
So why are you using a GPT on your Ubuntu drive instead of a standard MS-DOS partition table? You don't have an excessively large HDD nor a lot of partitions, so I don't see the justification for using GPT. I only have a little experience using Grub with a GPT HDD, but how about posting the output of the following commands:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```

---

### Post by vahnx on 2009-05-08
You might wanna replace the stage1 with stage2 in the above commands because I think Ubuntu started using stage2 a few Ubuntu's back but I'm not 100% sure, or if the stage1 is not found. The above should find your grub partition, then if you cannot get grub installed, you can download different grub versions until you find one that works.

---

### Post by jhonyrod on 2009-05-08
I use gpt cause before I had a couple more partitions and I kept few of these

And I tried those commands, using stage1 and 2, seems like it work but when I restart nothing happens

EDIT: I've just ran those commands again, both ways point me to the same disk and partition, (hd1,1)

Also I ran root and setup, this is the output, seems normal
```

grub> find /boot/grub/stage1
 (hd1,1)

grub> find /boot/grub/stage2
 (hd1,1)

grub> root (hd1,1)   
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd1,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,1) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

Nothing happens after restart

---

### Post by caljohnsmith on 2009-05-09
OK, how about instead doing:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
Reboot, make sure you set your BIOS to boot the 160 GB sdb Ubuntu drive first, and if all goes well you should get a Grub menu. Let me know how that goes or if you run into problems.

John

---

### Post by jhonyrod on 2009-05-09
Ok, here's the output
```
grub> find /boot/grub/stage2 
 (hd1,1)

grub> root (hd1,1) 
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1) /boot/grub/stage2 p /boot/grub/menu.l
st "... succeeded
Done.

```
I wasn't sure if that command works on gpt disks, that's why i didn't do that

Also, i'm also setecting my HD explicitly on the boot device select menu, so that's no my problem

I'll post if it works later

EDIT: 
It worked!, tank you guys, i can't figure out that fixing it was that simple

One more thing, anyone knows that if i copy the win partition into my ubuntu hd i can make a dual boot?

---

### Post by jhonyrod on 2009-05-09
Double post, sorry

---

### Post by vahnx on 2009-05-10
You might wanna install this program for easy grub configuration:
```
sudo apt-get install startupmanager
```

I'm looking at it right now and I don't see a way to add grub entries by partition and automation (thought there was) but it's a good start. To manually add Windows to grub, run:
```
sudo gedit /boot/grub/menu.lst
```

My Windows entry looks like:
```

title Windows 7
rootnoverify (hd0,0)
makeactive
chainloader +1

```

I forget how to determine the hd#,# of the partition but it should be easy to find out.

---

### Post by jhonyrod on 2009-05-10
Does it also work on gpt disks???

---

### Post by vahnx on 2009-05-12
No clue what a gpt disk is and by research I am unsure, sorry :)
You could always backup and try it ;D

---

### Post by jhonyrod on 2009-05-12
GPT (GUID Partition Table (Globally Unique IDentifier)
And I asked cause it is supposed that windows cant install on gpt disks unless the pc has UEFI	
[According to wikipedia]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

---

