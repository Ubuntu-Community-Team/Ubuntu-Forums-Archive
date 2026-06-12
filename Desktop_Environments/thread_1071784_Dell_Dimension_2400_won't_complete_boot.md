---
title: "Dell Dimension 2400 won't complete boot"
date: 2009-02-16
forum: Desktop Environments
---

### Post by Stucco on 2009-02-16
I have an older Dell Dimension 2400 2.4Ghz Celeron 512MB Ram
I added 256MB RAM to make it 512, and did the mem test.  It passed completely.

I installed 8.10 after running the CD check.  I made it through the install fine.  On the first boot everything looked good.  I made it up to the point where the mouse is enabled and I'm waiting for the desktop to come up and it sticks right there.  I have the autologin enabled so I'm not sure if it is hanging before or after login.

I can boot into the command if I hit Esc in grub and choose to do so.

I increased my video buffer from 1MB to 8MB in the BIOS.  I reduced the video memory from 128MB to 64MB.  I removed quiet and splash from the kernal line in grub.  I booted to recovery mode and ran xfix.  I did a file system check and it came back perfect.  Nothing has done the trick.  I still hang on a black screen with a white cursor.  The mouse moves, but the keyboard will no longer change num lock status once I hang.

---

### Post by chato92 on 2009-02-16
mhh i have the exact same computer and i installed ubuntu 8.10 on it no problems maybe it dint install correctly on your machine maybe reinstalling will help

---

### Post by Stucco on 2009-02-16
You know I searched a ton before I posted but behold here is the answer

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

Taken from 
[http://ubuntuforums.org/showthread.php?t=965478&page=2]("http://ubuntuforums.org/showthread.php?t=965478&page=2")
Post #17

It booted perfectly after uninstalling that

---

### Post by abn91c on 2009-02-16
+1 for removing compiz, the problem is the intel 845 video card, if you want some "eye candy" you can always install kubuntu. Note the problem is with 8.10, compiz will work on 8.04
Also the Max ram for the 2400 is 2 gig, I have 1.5gig in mine and it flies :-)

---

### Post by frogging on 2010-04-29
OK so I'm new at this and have another dell I had graphic problems with at it was Compiz I had to uninstall it.

That was an dell optiplex GX115.  

Onto this problem with Dell Dimension 2400

I try to install Ubuntu 9.10 and it hangs in the boot up.

I tried with it inside of windows and it hangs.

I have a Knoppix 5.0 live CD disk and it loads and runs fine.:(

My question is how do I get to a treminal without loading Ubuntu on this Linux Toy.  ( Learning some lingo )  :lolflag: 

I need to do these changes

***Start Copy Paste***

Fixed it . 

Edited /etc/default/grub
changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to GRUB_CMDLINE_LINUX_DEFAULT="splash"
and ran 'update-grub'

I power cycled the machine and it booted automatically this time without having to go through the boot device menu.

**found this workaround at** 

[http://ubuntuforums.org/showthread.php?t=1334658]("http://ubuntuforums.org/showthread.php?t=1334658")

***End Copy Paste***

If anyone can help

Seems like the programmer's should make Compiz an install option

I have an Idea tell me if it will work and if so How do I do it.:?:

Can I put Ubuntu 9.10 on a CD-RW and then use Knoppix 5.0 terminal to edit the boot to not load compiz and change the splash screen.

***Added with edit***

And then install/boot with the CD-RW after the edits.  Or make a new CD-R from the CD-RW and then install/boot with it.

---

