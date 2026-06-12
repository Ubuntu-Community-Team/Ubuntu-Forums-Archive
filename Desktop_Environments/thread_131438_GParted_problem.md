---
title: "GParted problem"
date: 2006-02-16
forum: Desktop Environments
---

### Post by p0liX on 2006-02-16
I am trying to resize my main partition using the Live cd and Gparted.

I set the new size, and click apply and it goes through the process and coems up and says that it finished and suggests a reboot.

Then it refreshes the partitions and does not show the new partition size.  I reboot into the normal installation and nothing has changed.  The partition was never changed although it says it was.

What could be causing this?

---

### Post by rsmereka on 2006-02-16
In addition to appy, I believe there is a commit button. When I used this utility, I remember the same thing happening to me until I realized that I had to commit the changes.

---

### Post by p0liX on 2006-02-16
I've looked around and dont see any type of commit button only the apply button.  But when doing the apply, it does come back with an error, but the error box is blank and i can't see what the error is.

Is there another way to manually resize a partition?

---

### Post by psusi on 2006-02-16
What kind of partition is this?  Ext3 or reiserfs?  Could you paste the output of fdisk -l?

You can try using parted to resize from the command line.

---

### Post by p0liX on 2006-02-16
The partition is ext3

and the output from fdisk -l  - 

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7131    57279726   83  Linux
/dev/hda2            7132        7296     1325362+   5  Extended
/dev/hda5            7132        7296     1325331   82  Linux swap / Solaris


I'm trying to shrink hda1 an make a spare 10 gig partition for a windows install.

---

### Post by plors on 2006-02-17
there is no 'commit', only 'apply'.
Please use the latest gparted (0.2.1) to try this again. It contains detailed progressfeedback so you can easily follow the process and see if anything went wrong.

cheers :)

---

