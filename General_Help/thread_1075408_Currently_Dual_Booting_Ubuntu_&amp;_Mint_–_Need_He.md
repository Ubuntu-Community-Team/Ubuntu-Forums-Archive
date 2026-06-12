---
title: "Currently Dual Booting Ubuntu &amp; Mint – Need Help Going 100% Ubuntu"
date: 2009-02-20
forum: General Help
---

### Post by bark50 on 2009-02-20
I can find lots of postings from people with Windows/linux dual boots but nothing about dual boots of multiple linux distros.  I installed Ubuntu 8.10 first on my hard drive and Mint a few days later.  Partition Editor shows sda1 as 228.63 GiB with 104 used, so I figure this must be where Ubuntu is.  Sda2 is an extended partition consisting of sda6 with 218.44 GiB size and 21 used, so that's the Mint partition.  Also on sda2 are sda7, linux-swap, at 9.27 GiB which I assume belongs to Mint because the remaining partition, sda5, also linux-swap, is 9.41 GiB which system monitor says is the size of my swap when I'm in Ubuntu.

So, I guess I want to use Partition Manager to delete sda 6 and 7, right?  Can I do that while in Ubuntu or should I do that from the live CD?  Mint took over grub, so how do I get it back in Ubuntu?  I found this article about restoring grub with the live CD -- [http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11") – but that's for people who have grub overwritten by Windows.  Will it work to restore Ubuntu's grub that was overwritten by Mint?  If the process in the link is what I want to do, should I do it before deleting the partitions?

Can somebody please give me some instruction on how to do this?  Thanks.

---

### Post by my window broke on 2009-02-20
yeah, grub should recognize any os you have on your HD, just use a live cd boot and reinstall your grub on your HD

---

### Post by my window broke on 2009-02-20
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

just follow that on how to reinstall your grub from a live cd.

---

### Post by caljohnsmith on 2009-02-20
That tutorial you linked to should work fine for restoring Grub, and you should do it after after you delete your Mint partitions. Good luck and let us know how it goes or if you run into problems.

---

### Post by bark50 on 2009-02-20
Thanks for all your help.  I'm rid of Mint, and I have a functioning, vanilla grub.  For my partitions, I now have:

sda1 ext3 228.63 GiB
sda2 extended    and under sda2
unallocated 227.71
sda5 linux-swap 9.41 GiB

(I tried attaching a screen shot here that I took of gParted, but I got an "Invalid File" message.)

I would like that 227.71 GiB of unallocated to be merged with sda1 so that I have my entire 500 GiB hard drive devoted to Ubuntu.  GParted won't let me simply extend sda1.  I can format unallocated as ext3, but I can't figure how to "attach" it to sda1.  I think what I'm saying (and I'm definitely getting confused now!) is I want one main partition of Ubuntu filling up my hard drive with a smaller, second partition for the 9.41 GiB swap file.  I've read gParted's documentation, but I don't see where this is covered.  Can I please get some more help?

---

### Post by caljohnsmith on 2009-02-20
How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
That will give us a better idea of the physical arrangement of your partitions, and how you might go about adding the unallocated space to your sda1 partition.

---

### Post by Mercury_Alpha on 2009-02-20
As it turns out, you will be better off in the long run if Ubuntu is *not* running on a single partition. You're going to want a separate partition for all your data (and ideally a separate partition for /home altogether). That way you can wipe/reinstall Ubuntu without losing data or settings.

---

### Post by bark50 on 2009-02-20
> **caljohnsmith said:**
> How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
That will give us a better idea of the physical arrangement of your partitions, and how you might go about adding the unallocated space to your sda1 partition.

tom@tom-desktop:~$ sudo fdisk -lu
[sudo] password for tom: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002b649

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   479475989   239737963+  83  Linux
/dev/sda2       479475990   976768064   248646037+   5  Extended
/dev/sda5       957024243   976768064     9871911   82  Linux swap / Solaris
tom@tom-desktop:~$ 

tom@tom-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=479475927, Id=83, bootable
/dev/sda2 : start=479475990, size=497292075, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=957024243, size= 19743822, Id=82
tom@tom-desktop:~$ 


Does that help?  Just to be clear (hopefully I'm being clear), I am trying to get the partitions set up like they were when I did a fresh Ubuntu install and had no other operating systems on my hard drive.

Thanks for everybody's help.

---

### Post by caljohnsmith on 2009-02-20
It looks like the issue is you just need to shrink your sda2 extended partition from the beginning so it is right up against the starting point of your swap partition. Then you can use the unallocated space for sda1 if you want. But I think Mercury_Alpha made a good point about not adding all that space on to your main Ubuntu partition; currently your main Ubuntu partition is ~240 GB, which is huge for just the Ubuntu file system. I think you would be much better off using the unallocated space for a data partition for all your personal files, and then you can set it up so it is easily accessible while you are in Ubuntu by having it mounted on start up. Does that sound maybe like something you would want to do? It's up to you of course.

---

### Post by bark50 on 2009-02-20
> **caljohnsmith said:**
> It looks like the issue is you just need to shrink your sda2 extended partition from the beginning so it is right up against the starting point of your swap partition. Then you can use the unallocated space for sda1 if you want. But I think Mercury_Alpha made a good point about not adding all that space on to your main Ubuntu partition; currently your main Ubuntu partition is ~240 GB, which is huge for just the Ubuntu file system. I think you would be much better off using the unallocated space for a data partition for all your personal files, and then you can set it up so it is easily accessible while you are in Ubuntu by having it mounted on start up. Does that sound maybe like something you would want to do? It's up to you of course.

My reluctance to setting up a separate partition for my /home directory is strictly knee-jerk:  just to get to this point has taken me several evenings of scouring posts here on the forums and Googling articles.  I found this article on moving /home to its own partition:   [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")  Most of the instructions are clear, but when I read, “You might have to do some tweaking and honing to make sure you get it all right...”, I hesitate because I don't know how to “tweak and hone”!  So, I think I'd like to just have everything as a fresh install and be done with it.  I can always revisit the separate/home partition later, right?

To that end, I think this is what I need to do:
1.From gParted, I right-click the linux swap file and choose “Swapoff.”  This unlocks swap and my extended partition.
2.Then I click on sda2 (the extended partition) and choose “Resize/Move.”
3.In the box that opens up, I move the left arrow all the way it will go to the right.  This nudges it up right to the swap file, I think.
4.I click on the “Resize/Move” button in the box.
5.After the process finishes, I right-click on swap and choose “Swapon.”   

Is that it?  Will I be done then?  I really do appreciate the help everyone has given me here.

---

### Post by caljohnsmith on 2009-02-20
> **bark50 said:**
> My reluctance to setting up a separate partition for my /home directory is strictly knee-jerk...
Actually I didn't mean setting up a separate home partition, I simply meant creating a separate partition for your personal documents. That's a lot easier than setting up a home partition, because there's no configuration necessary.
> **bark50 said:**
> 
To that end, I think this is what I need to do:
1.From gParted, I right-click the linux swap file and choose “Swapoff.”  This unlocks swap and my extended partition.
2.Then I click on sda2 (the extended partition) and choose “Resize/Move.”
3.In the box that opens up, I move the left arrow all the way it will go to the right.  This nudges it up right to the swap file, I think.
4.I click on the “Resize/Move” button in the box.
5.After the process finishes, I right-click on swap and choose “Swapon.”   

Is that it?  Will I be done then?  I really do appreciate the help everyone has given me here.
Sounds like you have it exactly right if giving the unallocated space to sda1 is what you decide to do. You can omit the last step of selecting "swapon" if you want, as that's not important since I doubt you'll need the swap space when doing the partition changes from the Live CD. Good luck and let us know how it goes.

---

### Post by bark50 on 2009-02-20
I'm going to cry.  Following the 1-through-5 instructions I posted earlier, I ended up with (I think I might have found out how to post a screenshot, but just in case I didn't...):

 sda1------ext3-----228.63 GiB
unallocated----unallocated----227.71 GiB
sda2-----extended-----9.41 GiB
sda5 (nestled in sda2)----linux-swap----9.41 GiB

Where do I go from here?  Thanks.

---

### Post by caljohnsmith on 2009-02-20
It looks like you did a great job, but there's just one more step: click on the sda1 partition, click "unmount", choose "resize", and then move it's end point (use the right arrow in the gparted dialog box) all the way to the right to use the unallocated space that you created by resizing sda2. Then you should be finished. Let me know how it goes or if you run into problems.

---

### Post by bark50 on 2009-02-20
> **caljohnsmith said:**
> ...click on the sda1 partition, click "unmount"...

Booting from the live CD and using gParted, when I click on sda1 the unmount feature of the context menu is grayed out.  If I start up the installed Ubuntu, go to gParted, and right-click on sda1, unmount is not grayed out.  However, clicking on it results in the message, "Could not unmount /dev/sda1.  The partition could not be unmounted from the following mountpoints:  /  Most likely other partitions are also mounted on these mountpoints.  You are advised to unmount them manually."

I do appreciate all the help I'm getting here.

---

### Post by caljohnsmith on 2009-02-20
> **bark50 said:**
> Booting from the live CD and using gParted, when I click on sda1 the unmount feature of the context menu is grayed out.  If I start up the installed Ubuntu, go to gParted, and right-click on sda1, unmount is not grayed out.  However, clicking on it results in the message, "Could not unmount /dev/sda1.  The partition could not be unmounted from the following mountpoints:  /  Most likely other partitions are also mounted on these mountpoints.  You are advised to unmount them manually."

I do appreciate all the help I'm getting here.
You definitely have to use your Live CD to resize sda1, because you can't resize sda1 when you are booted into it. If sda1 is not mounted when you run gparted from the Live CD, there won't be a "lock" icon next to it in gparted, and gparted won't give you the option to unmount it since it isn't mounted. I only mentioned clicking the "unmount" option in case sda1 was mounted, but if it isn't, no need to worry; just continue with resizing sda1. :)

---

### Post by bark50 on 2009-02-20
Doh!  Guess I could have looked at all of the context menu.  Then I would have seen the "Resize/Move" option was already ripe for the clickin'.  Caljohn, may I suggest you consider changing your nic to CalJob to reflect the patience you've shown here?  Everything works great now.  Thank you so much.

---

### Post by caljohnsmith on 2009-02-21
Glad to hear you successfully resized your sda1 Ubuntu partition; cheers and enjoy your Ubuntu install. :)

---

