---
title: "how do u install windows in a ubuntu machine?"
date: 2007-10-18
forum: Desktop Environments
---

### Post by sshlady on 2007-10-18
hello people.my windows crashed on me and i since i didnt have the windows cd yet the other day, i decided to try out ubuntu for a while and i liked it better than fedora.it has been a few days and i want to keep ubuntu on my laptop but on the other hand i still need windows for my college tasks.how do i repartition the disk since i install ubuntu without even repartition it at all?and how do i keep both operating systems working for dual boot? before this i had windows before fedora.i am really not sure how will it work to install ubuntu first then windows.

---

### Post by Kalibur on 2007-10-18
well I cant answer ur question in full but I know a few things....
If u boot using the live cd go to system.administration and open gnome partitioner that will allow u to resize ur current partitions to creat some free space.  With this free space u can install ur windows using the normal way boot using the windows cd. 

After that u will lose boot grubber the the thingy that ubuntu uses to boot
So when u restart ur pc will see no ubuntu infact ur windows wont even recognise ur linux partitions.  But dont shy away after windows setup is complete boot using ur ubuntu live cd and there is a  way to re install grub without having to install a freash ubuntu that will restore ur grab so when u pc start u can choose between ubutntu and u other more inferior OS i.e window XP.

I just tried to find the how to reinstall grub after install windows but  am running out of time so you just have to search for it. it was posted early this year or last year I think.
:popcorn:

---

### Post by mattpker on 2007-10-18
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

There is the documentation on how to dual boot.

---

### Post by mmtowns on 2007-10-18
> **sshlady said:**
> hello people.my windows crashed on me and i since i didnt have the windows cd yet the other day, i decided to try out ubuntu for a while and i liked it better than fedora.it has been a few days and i want to keep ubuntu on my laptop but on the other hand i still need windows for my college tasks.how do i repartition the disk since i install ubuntu without even repartition it at all?and how do i keep both operating systems working for dual boot? before this i had windows before fedora.i am really not sure how will it work to install ubuntu first then windows.

Using a program called "Virtual Box" is another option.  This would allow you to keep Linux and then install Windows "inside" of Linux, so you wouldn't have to worry about rebooting or repartitioning.  This requires a fair amount of RAM though.

Here's a few links to help you get started:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
[http://www.howtoadvice.com/UbuntuVirtualBox/](http://www.howtoadvice.com/UbuntuVirtualBox/)

---

### Post by sshlady on 2007-10-19
thanks for all the responses. i repartition the hd to 4 partitions using live cd;linux,swap,ntfs for my windows,and fat32 for shared data.however, i was in such a hurry that i didnt find out how to install grub after i install a fresh copy of windows so i have to install ubuntu again but that's fine by me.double the work but less headache. :P
i'd like to try virtual box someday but i think i need a desktop to do that.the laptop is a bit old and isnt that reliable.it dies on me a few times already.

but my question is, using virtual box, does it means windows run in linux?like some sort of software or something?

---

### Post by Kalibur on 2007-10-19
Here is a snap shot of virtual box at work you need alot of RAM though am on 1.5gb DDR SDRAM but if you be using windows for multimedia its probably not a good idea. I swear to find that thing about how to reinstall grub, I used it alot but after virtualbox there was no need for me to perform hardware based network lab sessions so i lost track of the documents.  Here is a snap of virtual box at work.

---

### Post by Kalibur on 2007-10-20
**Here is that threa\d bout to reinstall Grub**

[http://ubuntuforums.org/showthread.php?t=157599](http://ubuntuforums.org/showthread.php?t=157599)

**If that dont work one of these should work**

** [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall) **
[http://najam.wordpress.com/2007/03/01/reinstall-grub-after-installing-windows-xp/](http://najam.wordpress.com/2007/03/01/reinstall-grub-after-installing-windows-xp/)
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
[http://sidvind.com/wiki/HOWTO_Restore_GRUB_after_Windows_XP_installation-cd](http://sidvind.com/wiki/HOWTO_Restore_GRUB_after_Windows_XP_installation-cd)

[http://ubuntuforums.org/archive/index.php/t-157599.html](http://ubuntuforums.org/archive/index.php/t-157599.html)

---

