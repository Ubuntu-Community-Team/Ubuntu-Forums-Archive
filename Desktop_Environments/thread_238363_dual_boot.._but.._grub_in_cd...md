---
title: "dual boot.. but.. grub in cd.. ??"
date: 2006-08-17
forum: Desktop Environments
---

### Post by ShamuaL on 2006-08-17
Hi..

I'm complete newbie here..
trying hard to get used to linux..
ubuntu is nice...
now i've got a problem..

i want to run winxp and ubuntu in a same machine different in partitions..
but i want the machine to normally boot to xp...
but when i'll put the grub cd in the cdrom.. 
it'll show me the option to boot to linux...

i mean i want to install the grub in a cd rom.. or dvd..
and use it to show the linux boot prompt.. otherwise.. nothing just xp...

is it possible?
i saw once in a forum.. someone did this.. but lost the link..
can someone help me out? or at least gimme any helpfull direction or link..

thanks ...

---

### Post by meng on 2006-08-17
Not sure why you would want to do that - if you install Ubuntu and dualboot with WinXP, you can set grub to load WinXP by default, with the option to interrupt (with the ESC key) within a few seconds (or any time interval of your choice) if you want to load Linux instead.

But if you're sure you don't want to do it this way (which is pretty simple!) then fine (but I don't know the answer to your question.)

---

### Post by bulldog on 2006-08-17
I think that what you want to achieve must be possible,but I don't know how.

On the other hand,why make it so difficult?
When you install Ubuntu and install Grub you are able to log in both,Ubuntu and XP,in a quick and clear way.

If you are troubled with messing with your menu.lst take a look at the following link.

[http://www.ubuntuforums.org/showthread.php?t=228104&page=2](http://www.ubuntuforums.org/showthread.php?t=228104&page=2)

GrubEd is a grafical interface to change your boot-sequence and a lot more if you want to do so.

---

### Post by ShamuaL on 2006-08-17
thanks for replies guys..

yeah..
i know about normal grub loader in mbr..
i'm currently using it...
but i wanted to implement the CD or DVD or USB drive.. option
that way.. everything goes normally..
and i insert the linux boot cd... grub cd.. 
and boommmm... i have linux booting option in HDD..

its nice and hidden..

don't u guys also wanna know.. how this thing works?
i do..

can anyone help please?

---

### Post by b_martinez on 2006-08-17
There is a way to use Windows bootloader to initiate Linux,but grub is a better loader, and if you decide to get rid of Linux, you can always boot the windows cd and fix the mbr.
Bill

---

### Post by meng on 2006-08-17
> **ShamuaL said:**
> don't u guys also wanna know.. how this thing works?
i do..
Sure, Linux is all about choice, so if you really want to do it this way, good luck to you. Myself, I'm not particularly curious how to get this working, as it doesn't really suit my needs.

---

### Post by bootlinux on 2006-08-17
***This came from***:  [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#TOCq4](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#TOCq4)

These are instructions for making a boot floppy with which you can boot Ubuntu. You could, I guess interpolate these instructions to make a cdr but I've not tried it. 8-)  



   1.  Create a filesystem in your floppy disk (e.g. mke2fs /dev/fd0).
   2. Mount the floppy on somewhere, say, /mnt.
   3. Copy the GRUB images to the directory /mnt/boot/grub. Only stage1, stage2 and menu.lst are necessary. You may not copy *stage1_5.
   4. Unmount the floppy.
   5. Run the following commands (note that the executable grub may reside in a different directory in your system, for example, /usr/sbin):

      /sbin/grub --batch --device-map=/dev/null <<EOF
      device (fd0) /dev/fd0
      root (fd0)
      setup (fd0)
      quit
      EOF

---

### Post by mdurham on 2006-08-18
Here's the instructions that I used to make a bootable CD. It works fine.
> 3.4 Making a GRUB bootable CD-ROM

GRUB supports the no emulation mode in the El Torito specification5. This means that you can use the whole CD-ROM from GRUB and you don't have to make a floppy or hard disk image file, which can cause compatibility problems.

For booting from a CD-ROM, GRUB uses a special Stage 2 called stage2_eltorito. The only GRUB files you need to have in your bootable CD-ROM are this stage2_eltorito and optionally a config file menu.lst. You don't need to use stage1 or stage2, because El Torito is quite different from the standard boot process.

Here is an example of procedures to make a bootable CD-ROM image. First, make a top directory for the bootable image, say, `iso':

     $ mkdir iso

Make a directory for GRUB:

     $ mkdir -p iso/boot/grub

Copy the file stage2_eltorito:

     $ cp /lib/grub/i386-pc/stage2_eltorito iso/boot/grub

If desired, make the config file menu.lst under iso/boot/grub (see Configuration), and copy any files and directories for the disc to the directory iso/.

Finally, make a ISO9660 image file like this:

     $ mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

This produces a file named grub.iso, which then can be burned into a CD (or a DVD). mkisofs has already set up the disc to boot from the boot/grub/stage2_eltorito file, so there is no need to setup GRUB on the disc. (Note that the -boot-load-size 4 bit is required for compatibility with the BIOS on many older machines.)

You can use the device `(cd)' to access a CD-ROM in your config file. This is not required; GRUB automatically sets the root device to `(cd)' when booted from a CD-ROM. It is only necessary to refer to `(cd)' if you want to access other drives as well. 


---

### Post by patrickfromspain on 2006-08-18
I find that thing just pointless. Having to put a cd everytime I want to boot into linux just to get a boot loader... 

I'd set up grub to boot windows with a 1 second count down. This way, if you want windows, you nearly won't notice grub (and if your family uses the pc to they won't have time to do anything in grub) and if you want to boot to linux you'll have 1 second time to change the option. Much easier.

---

### Post by cmason on 2006-08-18
ShamuaL:

I am looking for exactly the very same thing...you are not alone. Why not boot to grub?  Because other family members the PC, and things go wrong or they push the wrong button, or whatever. I don't want them trying to figure out what this Linux thing is, or even being exposed to it...1 second or not. I want to boot to Linux when I am ready, not everytime the PC boots.

Will await an answer with you ShamuaL...

---

### Post by RRS on 2006-08-18
There's a couple well explained options on [Hermans site]("http://users.bigpond.net.au/hermanzone/index.htm"). 

One is how to completely [hide grub]("http://users.bigpond.net.au/hermanzone/p15.htm") (item 5 in the menue) so other users will only know of your chosen default operating system.

[The other]("http://users.bigpond.net.au/hermanzone/p12.htm") covers the Gag bootloader which doesn't need grub installed in the mbr to but your system. I have a copy on cd as a potential rescue tool.

One of these should suit you needs.

---

### Post by Herman on 2006-08-18
I agree with patrickfromspain, for a more verbose how-to with illustrations, try the following link, 'Hiding the GRUB menu during bootup..........................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")' 
Just give it a try, it works really well!

Also, if anyone wants to share Ubuntu with other family members safely, just create more user accounts for them and let them use Ubuntu as much as they like. They can't hurt anything, or access any information in your own user account except what you set the file permissions for. I would be strongly encouraging children and teenagers to use Linux and learn the command line. I think it will become an important part of their education because Linux will eventually come to dominate, especially for business and work computers. 

Both mdurham and bootlinux's instructions for making a Grub CD or Grub floppy should do all you need too. The question has already been answered.

If you still want even more alternatives, you could look at [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm"), and [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").
Regards, Herman. :D

EDIT: Oh, sorry RRS, I didn't see in time that you have already posted just ahead of me - thanks for recommending my site, keep on doing it whenever it will help people, Regards, Herman :D

---

