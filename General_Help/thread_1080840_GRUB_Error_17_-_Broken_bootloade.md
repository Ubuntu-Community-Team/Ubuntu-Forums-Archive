---
title: "GRUB Error 17 - Broken bootloade"
date: 2009-02-25
forum: General Help
---

### Post by 852258 on 2009-02-25
[SIZE="5"]GRUB Error 17 - Broken bootloader[/SIZE]



My computer doesn't boot anymore after I applied an image recovery for an Ubuntu 8.10 partition. I used "Acronis True Image Home 11". When I first created this recovery image there was a warning that this dual boot could only be imaged correctly using the "Sector by Sector Approach". So I created the image using the "Sector by Sector Approach". I attempted to recover my Ubuntu 8.10 partition & after the process completed & I restarted my computer. The computer wouldn't start anymore. The bootloader would not load.



This first picture bellow shows what my computer displays when I turn it on.



[img]http://img26.imageshack.us/img26/4608/dscf0955.jpg[/img]

> GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17
_



This second picture shows what my bootloader looked like before I attempted to recover one of my partitions. The next picture after that shows the 2nd boot screen when I chose the last option which is: "Windows Vista/Longhorn (loader)".



[img]http://img502.imageshack.us/img502/2413/dscf0956.jpg[/img]

[img]http://img15.imageshack.us/img15/6866/dscf0957.jpg[/img]



This is how my partitions are setup:
Partition 1: ntfs Microsoft Windows XP Professional (25GB)
Partition 2: ntfs Microsoft Windows7 Ultimate beta 1 (25GB)
Partition 3: ext3 Ubuntu - Linux 8.10 (25GB)
Partition 4: SWAP (2GB)
Partition 5: ntfs Backup partition (166GB) This partition is for backing up my files from any & all of my OSs.

I installed these OSs in the corresponding order that is listed above.



I'm looking for a solution to this problem. I need to restore my  bootloader to the way it was before without losing any data.

If you require any further information about my computer to solve this problem then please don't be afraid to ask. I will respond with the answer as soon as I can.



```
What I've already tried:
I tried to use "Acronis True Image Home 11" to restore my mbr (Master Boot Loader) but that didn't work.
```



thanks in advance for any help at all.

---

### Post by caljohnsmith on 2009-02-25
How about booting your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal) and doing the following to try and restore Grub:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If the commands complete without errors, reboot and see if you get the Grub menu again on start up. If you run into any problems, then download the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

And do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by 852258 on 2009-02-26
Wow, thank you so much! It worked!!

If it's not too much trouble, I have one more question. I was going to ask my other question in my first post but I thought that this issue would take longer to resolve, if at all.

First off; I wanted to mention, I have seen other tutorials similar to your in the past. Your explanation looks a lot shorter then others & it's also a lot easier to understand. Not to mention the other tutorials on how to repair the bootloader/ GRUB, well the ones that worked, "Anyway," Well lets just say my bootloader looks different every time I repaired it. Except for this time. It looks exactly the same as before it got messed up. So, I'm grateful for that.

So, my question is... If I wanted to restore any other partition; which I do. Is there a right way & a wrong way to apply the recovery image for a dual boot configuration such as mine? You know.. So I don't lose my bootloader again.

I'm using "Acronis True Image Home 11" & the program gave me these options.

Active
Primary
Logical

It was already set to Logical by default but I set it to Primary. I don't know if this has anything to do with why my bootloader was lost but hopefully you or somebody can tell me of a way to apply my recoveries without losing start-up capabilities.

---

### Post by caljohnsmith on 2009-02-26
> **852258 said:**
> 
I'm using "Acronis True Image Home 11" & the program gave me these options.

Active
Primary
Logical

It was already set to Logical by default but I set it to Primary. I don't know if this has anything to do with why my bootloader was lost but hopefully you or somebody can tell me of a way to apply my recoveries without losing start-up capabilities.
If the Acronis software was going to image your Ubuntu partition back as a logical partition by default, probably that is what your Ubuntu partition was in the first place. So if Ubuntu was a logical partition originally, and you chose to copy it back as a primary partition, its partition number would for sure be different, and that temporarily breaks Grub in the MBR until you reinstall Grub and point Grub to use the new partition via the directions from my previous post. That would explain why you got a Grub error 17, because Grub was trying to access the wrong partition for its boot files. As you have seen now, it's not a big deal at all to reinstall Grub to the MBR and point it to the new partition, but if you don't want to do that, you would have to make sure you copy back your Ubuntu partition to exactly the same partition that it was originally so it has the same partition number (so no changing from logical to primary or vice versa). And all other things being equal, I would make Ubuntu a logical partition since Ubuntu boots just fine from a logical partition; the advantage of it being a logical partition is if you decide to repartition your HDD at any point, you will generally have more flexibility about creating any new partitions you might want if Ubuntu is a logical partition. That's because you can have about as many logical partitions as you want, but you are limited to only 3 primary partitions if one of your primary partitions is an extended partition (which would be your case if you have any logical partitions at all). Anyway, glad the Grub commands were all it took to get your Grub menu back and Ubuntu happily booting again; cheers and have fun with your Ubuntu install. :)

---

### Post by 852258 on 2009-02-26
I see, so what your saying is; always leave the default partition type & no matter what OS I recover the mbr or grub will remain in perfect working order. Is that correct?

Also does it make any difference recovering sector by sector or just recovering normally?

---

### Post by caljohnsmith on 2009-02-26
> **852258 said:**
> I see, so what your saying is; always leave the default partition type & no matter what OS I recover the mbr or grub will remain in perfect working order. Is that correct?

If Acronis recovers your Ubuntu partition so that it keeps its same partition number when you leave the partition type set to the default value, then yes, the MBR should not need to be modified afterwards. I've never used Acronis though, so I don't know for sure if it will recover the partition so it keeps its previous partition number; if you since added additional partitions to the drive since imaging the partition with Acronis, then probably Acronis will not be able to keep the original partition number when you image the partition back to the drive. 
> **852258 said:**
> 
Also does it make any difference recovering sector by sector or just recovering normally?
Unless Acronis offers support for partitions with an ext3 file system (which I doubt), then definitely your safest bet is to use the sector-by-sector backup method. The disadvantage is that it will take longer than a more efficient method that would involve copying the file system.

---

