---
title: "Rebooting in old OS"
date: 2009-05-28
forum: General Help
---

### Post by ThePoodonkis on 2009-05-28
I recently installed Ubuntu via a CD. I tested it, and installed it, but I thought my old OS was better to use.
Here's where things went bad. I rebooted my Laptop, but there's no option to reload in Windows. I installed it to be able to boot either of the two, but Windows doesn't show up.

I've tried the startup menus, and there's noting there.

Please, is there a way to get back onto Windows? I have important documents I can't afford to lose there.
If not, can I take the old files and bring them over to Ubuntu?

---

### Post by lindsay7 on 2009-05-28
Are you running vista or xp? Do you have the windows install disk handy?

---

### Post by deadlockedgamer on 2009-05-28
in place does it have a disk drive there?

---

### Post by ThePoodonkis on 2009-05-28
It ran on Vista, I think I've got the CDs somewhere. I'm not concerned about the OS as a whole, just the files. Will reinstalling Vista bring said files back?

And no, there is not a disk drive in Places. Is that bad?

---

### Post by lindsay7 on 2009-05-28
Put the vista install cd in the the drive and it will boot up, go to the repair option and get to the command prompt.

type bootrec.exe and enter
 
you will get some switch options type
bootrec /FixMbr or bootrec /FixBoot

There needs to be a space between bootrec and the /FixXXX

That will restore the mbr for windows and you can boot from it.  This may mess up your Ubuntu grub file but we can fix that next.  Let us know what happens and we can get you to provide some info to fix this.

---

### Post by deadlockedgamer on 2009-05-28
not having a drive in places makes it sound like you some how did not partioned but wiped it however follow the instruction from the other guy and tell us what happens.

---

### Post by lindsay7 on 2009-05-28
Can you clear up what you did?  Did you install Ubuntu and then install window?  What old os are you talking about. Or was Windows on the machine and then you installed Ubuntu?

---

### Post by ThePoodonkis on 2009-05-28
Okay, slight problem. Someone got rid of my Vista CDs, so I can't reinstall it through a disk. Any way i can install it via download?

As for the whole story...

I was using Windows Vista, and a friend said how great Ubuntu was. I was curious, so I ordered a CD. 
It arrived, and I installed it. I was using it for a bit, and I figured I liked Vista better. 
I rebooted the computer, but Vista was nowhere to be found. This friend failed to tell me that files aren't converted over when Ubuntu is installed, and now I'm afraid that the files may be gone.

---

### Post by cariboo on 2009-05-28
If you told the installer to use the whole disk, you files may be gone. Could you open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

that is a lower case L. Paste the output of the above command in your next post.

---

### Post by lindsay7 on 2009-05-28
The Ubuntu installer will offer to transfer some data files over to the new Ubuntu installation. Have you looked to see if any of these were transfered.  They would most likely be in the home directory.

---

### Post by ThePoodonkis on 2009-05-28
> **cariboo907 said:**
> If you told the installer to use the whole disk, you files may be gone. Could you open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```that is a lower case L. Paste the output of the above command in your next post.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14220   114222118+  83  Linux
/dev/sda2           14221       14593     2996122+   5  Extended
/dev/sda5           14221       14593     2996091   82  Linux swap / Solaris

What does all that mean?

---

### Post by ThePoodonkis on 2009-05-28
> **lindsay7 said:**
> The Ubuntu installer will offer to transfer some data files over to the new Ubuntu installation. Have you looked to see if any of these were transfered.  They would most likely be in the home directory.

What exactly is the home directory?

---

### Post by Don1500 on 2009-05-28
> **ThePoodonkis said:**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14220   114222118+  83  Linux
/dev/sda2           14221       14593     2996122+   5  Extended
/dev/sda5           14221       14593     2996091   82  Linux swap / Solaris

What does all that mean?

Means you wiped windows. You reformated the entire disk. You need to reinstall windows.

---

### Post by Legace on 2009-05-28
> **ThePoodonkis said:**
> What exactly is the home directory?

Type **/home** in Nautilus.
Or open Terminal and type in **nautilus /home**

---

### Post by j7%&lt;RmUg on 2009-05-28
Yep you have formatted your whole drive when you installed ubuntu. You will have to reinstall windows if you still want to use it as was said above.

---

### Post by albinootje on 2009-05-28
> **Don1500 said:**
> Means you wiped windows. You reformated the entire disk. You need to reinstall windows.

You can use testdisk to try to restore your MS-Windows partition :
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck!

---

