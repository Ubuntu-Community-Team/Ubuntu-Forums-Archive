---
title: "Directory gone"
date: 2007-10-29
forum: Desktop Environments
---

### Post by CWBillow on 2007-10-29
If I type
 
find /boot/grub/ubuntu_grub
 
I get bat (hd0,10)
 
That's OK.
 
but then, if I type cd /media
 
That's OK, and then 
 
cd grub
 
I get
 
"no such file or directory...."
 
??
 
Chuck Billow

---

### Post by rowanparker on 2007-10-29
Why should /media/grub exist?
In the first line you search for /boot/grub/ubuntu_grub which is nothing to do with /media so it confuses me?

---

### Post by CWBillow on 2007-10-29
> **rowanparker said:**
> Why should /media/grub exist?
In the first line you search for /boot/grub/ubuntu_grub which is nothing to do with /media so it confuses me?
 
Rowan:
 
I'm, sorry, I was incomplete in my info.
 
I have Ubuntu, Kubuntu, and SUSE installed on my hard drive.
 
I have set up a separate GRUB partition;  I want to totally isolate each of the distros thereby.
 
So, in Ubuntu, if I go to Places/Computer, the GRUB partition shows up.
 
I then mount it.  
 
First, shouldn't I be asked for a password at this point?  'Cause I am not.
 
So I double-click (mount) the GRUB partition.
 
Then I open a Terminal window.
 
Then I type
 
sudo -s, and my password.
 
Then I type 
 
cd media
 
At this point, if I type ls, or dir, shouldn't I see GRUB in the listing that is then shown?
 
Regards,
Chuck Billow

---

### Post by rowanparker on 2007-10-29
Ah. Can you show me your '/etc/fstab' file and the output from 'sudo fdisk -l' please?

---

### Post by CWBillow on 2007-10-29
> **rowanparker said:**
> Ah. Can you show me your '/etc/fstab' file and the output from 'sudo fdisk -l' please?
 
Rowan:
 
Here's the problem with that:
 
I re-installed Ubu trying (again) just to make sure I had typed rightly.
 
And I, in trying to put the grub files on the separate partition, when it asked about putting GRUB to the MBR, I said "no... put it on (hd0,10)"... My Ubu partition.
 
It took it fine, but now when I boot all I get is my "old" WinXP boot screen.
 
Chuck

---

### Post by rowanparker on 2007-10-29
Erm.... I'm a bit unsure.
Maybe someone else will pop along.

---

### Post by CWBillow on 2007-10-29
> **rowanparker said:**
> Erm.... I'm a bit unsure.
Maybe someone else will pop along.
 
Rowan:
 
'Sokay.  I've got something I can try... I'll let you know...
 
Regards,
Chuck

---

### Post by rowanparker on 2007-10-29
> **CWBillow said:**
> Rowan:
 
'Sokay.  I've got something I can try... I'll let you know...
 
Regards,
Chuck
Good luck with that :)

---

### Post by oldos2er on 2007-10-29
Your system is always going to check the MBR first for a bootable partition, so you're going to need some kind of bootloader there if you want to boot more than OS. Grub should recognize Win XP when it installs, and create an entry for it in /boot/grub/menu.lst.

---

### Post by Jhongy on 2007-10-29
why would it appear as /media/grub? most likely /media/disk0 or something, unless you have named it grub somewhere (fstab)

---

### Post by MudCrab on 2007-11-01
I would just like to clarify what Chuck meant by this.

The Master GRUB partition has a partition label of GRUB. When the partition is mounted by going to Places->Computer and double-clicking on the GRUB drive icon, it is added to the /media folder as /media/GRUB.

In the Terminal program, typing

cd /media
ls

...will show GRUB in the list of files.

I think what the problem is, is that when he typed **cd /media/grub** it should have been **cd /media/GRUB** since Linux is case sensitive.

In post #1, the **find** command was run from the GRUB shell and the **ubuntu_grub** file reference is to a "marker" file created using **touch ubuntu_grub** to "tag" the Ubuntu partition's /boot/grub folder making it easier to find when setting up the Master GRUB partition.

---

