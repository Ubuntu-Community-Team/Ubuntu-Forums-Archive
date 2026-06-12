---
title: "Moving Ubuntu to another partition. Need help with Grub too"
date: 2009-04-04
forum: General Help
---

### Post by Njord on 2009-04-04
I originally installed ubuntu on a partition at the end of the disk (3GB - sda4) but found out shortly that it was not enough space. So I deleted the recovery partition (which is 10GB and at the front of the disk) and I want to move my Ubuntu installation to that partition (sda1).

So far I used the command "cp -ax" and have all the files on this partition (sda1), except I got this error
```
cp: cannot stat `/./home/ubuntu/.gvfs': Permission denied
```
Although, from what I found (or didn't find) it doesnt seem important. Hopefully someone can help me on that.

What I need to do now is install grub to this partition (sda1) and edit the boot menu so I can boot from either of the two ubuntu installations (sda1 and sda4)
I'll continue to google, but I'm not finding much.

Thanks for the help

To make it a little more clear, I need to add a line to grub so I can boot off of sda1 (the new copy of ubuntu)

---

### Post by Njord on 2009-04-04
bump

---

### Post by kwalters on 2009-04-04
As an opponent of the command line, I use 2 helpful tools to achieve what you want.

The first of these is called SelfImage, which allows you to move partitions byte by byte.  It comes included with a very useful download (and free) called Ultimate Boot CD for Windows (google UBCD4Win).  I can use it because I dual boot Ubuntu and Windows XP and therefore have the Win XP install disk needed to build UBCD4Win.   Self Image is one of the very few partition management tools that can see both Linux and Windows partitions and copy and restore either.

Self Image is obtainable separately (and also free) but I am not sure how you get it to run in a self booting CDROM without the aforementioned UBCD4Win.  It is much better to use it from a self  booting CD, so that you are not trying to copy sections of a disk from which the OS is running.

If I were trying to do what you want, I would use Self Image to copy my Ubuntu partition to a free disk space (I have a USB hard drive that I use for such things)I would then copy the resultant image to the section of disk where I want Ubuntu to work from in future.  You could, of course copy it directly rather than from a bit of free disk space (the USB disk in my case) but then you would not have a backup for the future (or if anything goes wrong during this process.)

My second vital tool (for me) is something called a bootable Linux rescue CD (I got the ISO image by googling that exact phrase, but I cannot remember exactly what the program is called.  Once that has booted itself up, there are 2 key functions I use more than any other:

If you just let it run through its rather long boot process, without any input from you, you will end up at the end of a screen full of text.  Type <startx> and press enter.  You will then have a GUI screen, one of whose options is to run GPARTED  -  a Linux partitioning tool.  As a minimum, use this to note where your various partitions are, and what they are called in Linux speak and in Grub speak.  In my case, my second Ubuntu variant (yes I run 2 as well as Windows) is on the ninth partition of my second SATA hard disk. That is /dev/sdb9 in Linux speak and hd(1,8) in Grubspeak.

Now to sort out Grub, assuming it is not working.  You need to have a working version of Linux.  If you cannot boot because Grub is not working, try the bootable linux rescue cd above. This time press F2 as soon as that option is presented.  Type <rescuehd root=/dev/sdb9> (for my setup) and press Enter.  This will start the version of Linux in the partition you have quoted.

Once you are there, open a terminal window and type:

sudo -i   [Enter]
then enter password when prompted
then type
grub  [enter} and from the (different) grub prompt type, in turn

root (hd1,8)  [in my case] [enter]
setup (hd0)  [enter]

That sets up grub in the boot sector of your first hard disk

Select Close and Restart and remove the bootable disk.  When the machine starts, grub should emerge and give you a choice of all the operating systems on your machine, with the Ubuntu partition you have been moving as the default

If you do not want it as the default, you will have to find /boot/grub/menu.lst and edit it.  If you need help with that, we had better do it another time.

Hope that helps; it works for me

This website is substituting a smiley face for the figure eight, for reasons which are beyond me

PS  I wish I knew what <bump> means - I keep seeing it

Keith Walters

---

### Post by Njord on 2009-04-04
THanks for the help. I'm in the middle of building the UBCD4W and will do a clone of my linux partition to the new partition. (I noticed what I did didnt copy every thing over :/)

Once I get that far, I'm going to read again what you wrote about grub.

Thanks for the help :)


By the way, bump means to bump the thread. After an hour my post was on the 2nd page; not many people venture from the first so a post will 'bump' it to the top of the forum page. ;)
Thanks again.

---

### Post by Njord on 2009-04-04
Well self image worked. It copied everything over. The only problem is that the size of the '10GB' drive is now 3gb. Gparted says its still 10gb, but 99% full.

How I did it was:
Loaded Up UBCD4W, used selfimage to copy the 3gb ubuntu installation to a file.
Then used the file to copy to the 10gb partition.

Now my 10gb partition is still intact, but it reads as full (via Gparted) but unbuntu says its 3GB.

(Note, the ubuntu installation thats on the 3gb was full)

Anyone know how to fix this?
Thanks!!

---

### Post by Njord on 2009-04-04
I fixed the problem above. I just partitioned a small portion of the space I was using (just large enough for the image [3gb]) applied the image to that, then resize after.

---

### Post by kwalters on 2009-04-05
I have often had difficulty after resizing Linux partitions when the OS is in them.  I always try to do the resizing separately. That is why I am so grateful for Self Image   -  I keep having to return the Linux partition exactly to its original size before I can successfully restore a partition image.

I suspect that Grub is surprised when it finds the partition size has changed and goes into a sulk and refuses to boot.  At present I have about 6GB worth of Ubuntu sitting in a 66GB partition; but every time I try to resize it, grub refuses to boot it.

So if the thing does not work at the end of your process, think back to the resizing part of the process as a potential problem area

KW

---

### Post by Njord on 2009-04-05
I finished this mess last night, and very thing works well. So for the people that stumble across this looking to do the same, I hope this will help you.

Recap:
Ubuntu is on 3.5GB partition and I want it moved to a 10gb partition
**I should point out that my Ubuntu installation was completely full when I imaged. When you go to apply the image I suggest sizing the partition to the size of the image, not the size of the drive from which it was copied (which might be the same size anyways, I dont use selfimage ever [excluding this one time])** 

Here is what I did.
-I built a fresh copy of The ultimate boot CD for windows (I used XP SP2 for the needed files) Then I booted off of it.
-Once I was in the live CD, I used Selfimage to take an image of the Ubuntu installation and saved it to a file (I saved it to my file server, but a USB stick should work nicely)
-Then using Gpart off of the Ubuntu Live CD I partitioned my 10gb of space to the size of the image I wanted to use. (Which was 3.5GB. I made it 4MB larger then It needed because nothing is worse then loading up UBCD4W to find out the partition is 30KB to small [!!!!] You can probably guess it happened to me. **NOTE above**)
-Back to UBCD4W to apply the image to the 3.5GB space (it will complain saying you'll lose data, because its not the originating partition. So make sure its the right partition, and proceed)
-Back to the Ubuntu Live CD to use Gpart to then add (resize) the unused 7GB of space.

Great! Now Every thing is copied over and no wasted space. (besides that 4MB but who cares?) But theres a problem, Grub is still launching off of the old (3.5GB) partition.

This is what I did to fix Grub:
Load up the Ubuntu Live cd again and run terminal.
```
sudo su
grub
find /boot/grub/stage1  #(It should show a list of Harddrives)#
<respond> (hd0,0)
<respond> (hd0,3)
                        #I wanted it on the new partition which was at the front of the disk so I used hd(0,0)#
root (hd0,0)
setup (hd0)

Quit

```

Now restart and once you boot you should be in the new partition. ;)

Thanks again kwalters for your help.

---

### Post by Njord on 2009-04-05
[http://ubuntuforums.org/showpost.php?p=1769691&postcount=5](http://ubuntuforums.org/showpost.php?p=1769691&postcount=5)
This is what I used to fix grub; For reference.

---

