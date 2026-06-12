---
title: "How to create partitions after installation"
date: 2006-08-19
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-08-19
Hello,

I have a large HDD and would like to partition it so I can have a FAT32 partition. How would I do this. Ubuntu is already installed.

Thanks,
Ian

---

### Post by slimdog360 on 2006-08-19
Im using xfce so I cant remember the exac way from gnome but I tihnk that its 

system-->admin-->disks

you can also download a gparted live cd

---

### Post by kriding on 2006-08-19
if Ubuntu is already installed, why do you need a fat32 partition?..sorry, enquiring minds and all:) 

Do you have free space on your partition already? If so, then you can go to System=>Admin=>Disks, create a partition and format as you like.

If you need to resize your current partition, you will need to use a GParted live CD

---

### Post by The Pinny Parlour on 2006-08-19
I want a FAT32 partition for windows to pick it up on a network for file transfers between windows and linux.

---

### Post by The Pinny Parlour on 2006-08-19
System/Admin/Disks are greyed out so I can't create or edit.

---

### Post by RRS on 2006-08-19
You need to use the live cd to alter your patitions as gparted can't modify a mounted partition. 

Reboot to the livecd and from System>Administration select "partition editor".

The stand alone gparted livecd seems to work a little better. You can get it [here]("http://gparted.sourceforge.net/livecd.php").

---

### Post by The Pinny Parlour on 2006-08-19
Thank you RRS.  It all worked perfectly and without an issue.

So for others who want to do it:

1.  Download gparted (Gnome Partition Editor) liveCD from [here]("http://gparted.sourceforge.net/livecd.php").

2. Burn the gparted liveCD image to a CD. (I found Gnomebaker easy to achieve this).

3. Pop the newly created liveCD in your CD/DVD drive and restart your PC.

4. Follow the instruction and use gparted recommended options.  (I just next, next, next through it all).

5. I had a 300gig, ext3, hda1 partition.  I firstly resized it by with a mouse click onto the "Partition" menu and choose "Resize-Move".   A Resize /dev/hda1 window will appear and I just choose the free space option to create my FAT32 partition, then hit the "Resize" button.

6.  The newly created unallocated 'space' was in my case 12gig.  I then click on it and selected FAT32.  

7.  Hit the apply button.  It takes awhile so make a cuppa.  Let it finish and remove livecd and restart.

It's complete.  When I go into System>Admin>Disks  I now have a FAT32 partition that is a touch under 12gig.


I should mention a great guide with images can be found [here]("http://gparted.sourceforge.net/documentation.php").

---

### Post by The Pinny Parlour on 2006-08-19
Hold on..... 

I have just found out that I can't open this partition when I select Place>Computer> then the partition or volume.

I get the follwoing error:

Unable to mount the selected volume.
error: device /dev/hda3 is not removable

error: could not execute pmount

Can anyone help me be able to access this please?

In Disk Manager, Access Path is selected to "none" should it be something?

Thank You,
Ian

---

### Post by RRS on 2006-08-19
Glad I could be of help.

You need to create a file path (directory) and then add the partition to your fstab.

Aysiu explains the procedure much better then I could [here]("http://www.psychocats.net/ubuntu/mountwindows.php"). The specific fat32 instructions are towards the bottom of the page.

---

### Post by The Pinny Parlour on 2006-08-19
Again thank you.  :) 
That all worked after thoroughly reading it and customizing it to my installation.  

Cheers,
Ian

---

