---
title: "Major trouble with GRUB/Unetbootin"
date: 2009-02-10
forum: General Help
---

### Post by redandwhitestripes on 2009-02-10
Hi guys, forgive me for posting this here - I am an Ubuntu user but this is not an Ubuntu specific query. I'm putting it here because this forum is so active and useful. Plus the Vector Linux forum is down, again :-)

Hello, I hope someone can help me as I need assistance badly!

I tried to install Vector Linux light on my old PC. As the CD drive is broken,
I used unetbootin. Now in the past, unetbootin has bought up a GRUB menu with
my  installed distros (Slitaz and Puppy) along with the new choice of the ISO I selected.

Not so this time. The GRUB bootloader came up with only Vector Linux.
To make things worse, VLL will not install. It gives me a message about a 
possibly corrupt config file. This despite the fact I verified the files and
used the same ISO file to install on another PC without problems.

I CAN access MC and other programs from the console prompt, though.

So I appear to have lost all access to Slitaz. I tried to do a ROOT, SETUP 
instruction with GRUB to restore the old GRUB menu but it stayed the same. It seems unetbootin alters the GRUB menu.lst file.

I also tried to manually edit the grub command  from the bootloader menu as I have a   paper copy of the old menu.lst but I get a kernel panic. Here is an example of what it says:
"010d   4096   ram 14  (driver?)"

Kernel panic - not syncing VFS: unable to mount root FS on unknown block"


So I am in a fix and as a newbie, I have no clue what to do.

I  need to access Slitaz. I have not touched the partition it is installed on 
though I did create a new partition with the VLL install programme. I'm also sure 
a made a backup copy of the grub menu.lst in the same directory.

What can I do? Has my old laptop effectively been killed?

Hope someone can help.
Thanks.
Taz

---

### Post by redandwhitestripes on 2009-02-10
OK With help from elsewhere I managed to solve this problem.

I went to GRUB command prompt and entered 
root (hd0,1) where my grub is installed

then I enetred the details of my vmlinuz file
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/hda7


It helped that I had these details saved onto a file on a seperate computer.

Hope this might help somebody else in future.

---

