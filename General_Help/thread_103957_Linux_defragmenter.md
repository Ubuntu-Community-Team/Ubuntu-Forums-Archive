---
title: "Linux defragmenter"
date: 2005-12-15
forum: General Help
---

### Post by katrielalex on 2005-12-15
Hi -

Thanks for the previous help I got on here, by the way - it worked and my computer is up and running.

Another thing I was curious about is whether there is a Linux defragmenter available - I realize that it's not necessary for Linux but I would like to defragment my Windows partition...thanks.

You can reach me at ubuntu at katriel dot co dot uk...thanks.

Kati

---

### Post by zoiks on 2005-12-15
Huh?  That's an odd use for a Linux OS.  Why don't you just defrag in Windows?  If you are talking about an ntfs partition, it's a non-starter anyway.  For fat32, googling yields this gem: (google is your best friend)

[http://forums.suselinuxsupport.de/lofiversion/index.php/t24786.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t24786.html)

---

### Post by Galoot on 2005-12-15
Two words: "Be Careful." Oh, and "Back Up."

Maybe my experience was an unusual one, but the last time I tried to defrag a Windows partition sharing the same drive with Linux, Windows decided it was hungry and ate Linux. It made me sad.

---

### Post by agger on 2005-12-15
[QUOTE=Galoot]Two words: "Be Careful." Oh, and "Back Up."

Maybe my experience was an unusual one, but the last time I tried to defrag a Windows partition sharing the same drive with Linux, Windows decided it was hungry and ate Linux. It made me sad.[/QUOTE]

Wow! That shouldn't be possible because Windows and the defragmenter shouldn't be able to see your Linux file system. Must be some truly hideous bug in the defrag software.

---

### Post by katrielalex on 2005-12-16
Thanks all...I will try the Google link.

I'm not using the Linux OS just to defrag my disk - I've installed it and everything. I just wanted to defrag the disk as I hadn't been keeping on schedule with the Windows defrags...

Kati

---

### Post by DiscoKiller on 2005-12-16
[QUOTE=Galoot]Two words: "Be Careful." Oh, and "Back Up."

Maybe my experience was an unusual one, but the last time I tried to defrag a Windows partition sharing the same drive with Linux, Windows decided it was hungry and ate Linux. It made me sad.[/QUOTE]

I had a hungry windows once, it ate 22gb of music, i could have cried....got it all back though...LAN sharing is a wonderful thing.

---

### Post by Nasso on 2005-12-16
[QUOTE=katrielalex]I realize that it's not necessary for Linux[/QUOTE]

Why is that?

---

### Post by soulestream on 2005-12-16
> I just wanted to defrag the disk as I hadn't been keeping on schedule with the Windows defrags...

old habits die hard. If you have your windows partitions formatted NTFS, you really only need to defrag about every 6 months, unless you are doing some hardcore video editing or install/remove apps constantly.  (I dont at all as I reinstall windows every year). 

my two cents

soule

---

### Post by KermitJr on 2005-12-16
[QUOTE=Nasso]Why is that?[/QUOTE]

The nature of Linux file systems has a very low fragmentation effect.  That is, you don't really need to defrag Linux partitions.  FAT (windows) and NTFS (Despite what they may try to have you believe) need to be defragged constantly.

KJ

---

### Post by psusi on 2005-12-16
Yea, defrag your windows partition in windows.  

As for Linux filesystems, a lot of people spread the lie that they are immune to fragmentation.  Linux filesystems most certainly DO get fragmented.  Maybe not as bad, but it does happen.  

Unfortunately, the only way to defragment them is to back up all the data, reformat, and restore.  Fortunately, it isn't a big enough problem that you need to worry about it.

---

### Post by psusi on 2005-12-16
Also there isn't anything inherant about the FAT or NTFS filesystems that cause fragmentation ( at least any more than just about any other filesystem ).  It is Microsoft's drivers that don't do a very good job allocating blocks that causes lots of fragmentation.

---

### Post by newuser111 on 2005-12-17
ext2 partitions have a defragmentation tool, ext3 doesnt unless its converted to ext2 and converted back after

---

### Post by Galoot on 2005-12-17
[QUOTE=agger]Wow! That shouldn't be possible because Windows and the defragmenter shouldn't be able to see your Linux file system. Must be some truly hideous bug in the defrag software.[/QUOTE]
I was using Diskeeper (for Windows), a program I still swear by. It was an old Mandrake dual-boot running beside Win98, and I let Mandrake take care of the partitioning. I don't know what exactly to blame, but I know that I decided against running a dual-boot system after that. I was forced to choose between the two OSes. Guess which way I went? :D

---

