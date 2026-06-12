---
title: "Editing Boot Loader for Multiple OS's"
date: 2008-12-14
forum: General Help
---

### Post by Kivamaki on 2008-12-14
I have 2 HDD's in my computer, and one USB External HDD. It says my WINDOWS HDD is sdb, my EXTERNAL HDD is sdc, and my other HDD is sda.

Ok, Windows is installed on one HDD (sdb), while Ubuntu, Fedora, and openSUSE are installed on another (sda).

When I installed ubuntu within the windows environment, it gave me a standard simple boot loader of "Windows Vista, Ubuntu" to choose from when my computer booted up. Then I installed Fedora and it installed it's own boot loader which has them all listed. Then I installed openSUSE and after it installed, it still went to the Fedora Boot Loader, and openSUSE isn't listed there. I can still get to the Microsoft Boot loader though, i just choose Vista under the Fedora Boot loader and it takes me straight to Microsoft Boot loader. And if I choose Ubuntu under the Microsoft boot loader, then i can enter the ubuntu menu and choose all my Operating Systems. Now, within ubuntu i'm trying to add all my operating systems in menu.lst, but I can't get them to boot right. I'm pretty sure I know what (x,y) they are, but they never boot. I just want one boot loader with all my operating systems, can someone help me?

> ## ## End Default Options ##

title		Ubuntu
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=E4643C7E643C5610 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu (Recovery Mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=E4643C7E643C5610 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		----Other operating systems----
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
chainloader	+1

title		Fedora
rootnoverify	(hd1,1)
chainloader +1

title		openSUSE
rootnoverify	(hd1,5)
chainloader +1

---

### Post by bodhi.zazen on 2008-12-14
See if this thread helps you (it has a number of suggestions)

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Kivamaki on 2008-12-15
Didn't really explain what I needed..

---

### Post by bodhi.zazen on 2008-12-15
Why not ?

You can either make a dedicated boot partition or call a config file or edit /boot/grub/menu.lst

---

### Post by Kivamaki on 2008-12-15
I'm not a linux expert, and that was detailed and confusing for me. I have 4 boot loaders for all my OS's. I just want one.

---

### Post by fuzzybear3965 on 2008-12-15
Hey, coincidentally I just did this today (installed 5 new OS's).  I read your intro. and you are definitely wrong somewhere.  If you installed an OS on sda then grub would read (hd0).  (hd1) means sdb.  So I'm going to help you assuming that you truly did install all your linux OS's on sda.

What you want to do, though, is use grub.  So navigate to the ubuntu grub folder in the terminal (cd /boot/grub) then type "sudo gedit menu.lst" without the quotes.

Now the trick is to be very explicit with your grub entries.  For example:  for your Fedora entry it would read like this:

title     Fedora
root      (hd0,1)
# Notice the root entry reads (hd_0_,1)
kernel    /boot/vmlinuz.......-default  root=UUID=**UUID of drive** ro quiet splah
# fill in the "...."'s with the correct info found in /boot
#the UUID of the drive is found by "sudo vol_id --uuid /dev/sda2" assuming that it #is the second partition on the first drive.
initrd    /boot/initrd. . . .-generic
#again fill in the . . .'s with the kernel found in the /boot folder
savedefault
boot

Something that would be helpful would be if you could download gparted from the repositories and screenshot the display where it lists your partitions.  Also, make sure in gparted you take a screenshot of each drive.  If you do this, then i can customize you a menu.lst .  I will reply as quickly as possible.

---

### Post by Kivamaki on 2008-12-15
Your right, they're on sdb, but when I was partitioning for openSUSE, it said they were all on sda, oh well. Here are the screenshots. I didn't take one of sdc because thats my 500gb external, kind of pointless. Thank you for helping me out, much appreciated.

---

### Post by TeXtonyx on 2008-12-15
"And if I choose Ubuntu under the Microsoft boot loader, then i 
can enter the ubuntu menu and choose all my Operating Systems. "

Does that include Microsoft? Besides being able to choose all your
OS, do they all boot? At some point you will probably need the
command, sudo fdisk -l (a lowercase L). Then notation that fdisk
uses and the notation that menu.lst uses, differs in partition # 

sda  = root (hd0)
sda1 = root (hd0,0)
sda3 = root (hd0,2)

sdb  = root (hd1)
sdb1 = root (hd1,0)
sdb5 = root (hd1,4)

sdc  = root (hd2)
sdc2 = root (hd2,1)

That is a common mistake, getting the numbers wrong, so I will
pass that along and move on. Using Super Grub Disk (with Help) is 
useful in finding out and making a note of the right (hdx,y) as 
you test it by booting then and there. Use your notes for menu.lst
if you get stuck using Gparted, fdisk and gksudo gedit ~/menu.lst

---

### Post by Kivamaki on 2008-12-15
To get to my Ubuntu Boot Menu I have to do this:

Turn on Computer, Fedora Boot Loader Comes up > Click Windows Vista > Microsoft Boot Loader Comes Up > Click Ubuntu > Hit ESC to Enter Menu

Windows isn't listed there, only Ubuntu and Fedora is because I manually edited the menu.lst earlier, but none of them boot except for Ubuntu.

Here is my fdisk -l

> Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4335    34816000    7  HPFS/NTFS
/dev/sdb2   *        4336        4360      200812+  83  Linux
/dev/sdb3            4361        8184    30716280   83  Linux
/dev/sdb4            8185       19457    90550372+   f  W95 Ext'd (LBA)
/dev/sdb5            8185        8446     2104483+  82  Linux swap / Solaris
/dev/sdb6            8447       11057    20972826   83  Linux
/dev/sdb7           11058       19457    67472968+  83  Linux

**EDIT:** I also tried adding Ubuntu to my menu.lst (I'm on Fedora) with the instructions above, however it came back with an Error: 17 Cannot Mount

title Ubuntu
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-9-default root=UUID=E4643C7E643C5610 ro quiet splah
initrd /boot/initrd.img-2.6.27-9-generic
savedefault
boot

---

### Post by fuzzybear3965 on 2008-12-15
Okay I'm going to make your grub loader today.  However, I need to straighten some things out.  I can see that sda1 is your Windows partition/drive.  Sdb1 is, what, a shared partition?  sdb3 is ubuntu.  sdb4 is the extended partition, sdb5 is your swap, sdb6 is what?  sdb7 is what?.  So i just need to know what sdb6, sdb7, and sdb1 are.

---

### Post by bodhi.zazen on 2008-12-15
These links may help :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There is a steep learning curve with GRUB, but GRUB can boot all your OS, it is just a matter of understanding the partitioning conventions.

I suggest you work through the first link I gave you as, IMO, you really need to understand how to maintain booting of your OS or you will run into issues as you update your OS (kernel updates).

If you have a specific question , please ask.

---

### Post by TeXtonyx on 2008-12-15
> **Kivamaki said:**
> To get to my Ubuntu Boot Menu I have to do this:

Turn on Computer, Fedora Boot Loader Comes up > Click Windows Vista > Microsoft Boot Loader Comes Up > Click Ubuntu > Hit ESC to Enter Menu

Windows isn't listed there, only Ubuntu and Fedora is because I manually edited the menu.lst earlier, but none of them boot except for Ubuntu.

Here is my fdisk -l
Device Boot Start End Blocks Id System
/dev/sdb1 1 4335 34816000 7 HPFS/NTFS
/dev/sdb2 * 4336 4360 200812+ 83 Linux = root (hd1,1)
/dev/sdb3 4361 8184 30716280 83 Linux  = root (hd1,2)
/dev/sdb4 8185 19457 90550372+ f W95 Ext'd (LBA)
/dev/sdb5 8185 8446 2104483+ 82 Linux swap / Solaris
/dev/sdb6 8447 11057 20972826 83 Linux   = (hd0,5)
/dev/sdb7 11058 19457 67472968+ 83 Linux = (hd0,6)


**EDIT:** I also tried adding Ubuntu to my menu.lst (I'm on Fedora) with the instructions above, however it came back with an Error: 17 Cannot Mount

title Ubuntu
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-9-default root=UUID=E4643C7E643C5610 ro quiet splah
initrd /boot/initrd.img-2.6.27-9-generic
savedefault
boot

Your fdisk reports
Device Boot Start End Blocks Id System
/dev/sdb1 1 4335 34816000 7 HPFS/NTFS
/dev/sdb2 * 4336 4360 200812+ 83 Linux

root (hd1,0) means sdb1 which is NTFS (Windows) not Ubuntu. 

I showed you that in the notational difference chart in post #8
sdb  = root (hd1)  
sdb1 = root (hd1,0) <-- grub menu.lst entry--> root (hd1,0)
sdb5 = root (hd1,4)

This is what you used above:
title Ubuntu
root (hd1,0) but that grub entry points to NTFS not 83 Linux

OP wrote: "Ok, Windows is installed on one HDD (sdb), while 
Ubuntu, Fedora, and openSUSE are installed on another (sda)."

Your fdisk report shows you have Windows installed on sdb1
as well as four other Linux OS. I can't tell what you have on
sda because your fdisk report doesn't show anything for sda.

You must get another boot menu from Windows after Linux grub.
But you can make Windows the default with a very short timer
so that it won't seem like you are getting another menu to see.

You said that you installed the OS in this order:
(Vista?)
Ubuntu    sdb3? = root (hd1,2)
Fedora    sdb6? = root (hd1,5)
OpenSuse  sdb7? = root (hd1,6)

You also seem to have a special small /boot partition, sdb2, and
maybe Fedora put its boot files there. Did you manually create
a /boot partition, or choose the creation of a /boot partition
during an OS install? See if there are grub files on sdb2 = (hd1,1)
I'm not sure if sdb2 is part of Fedora or Opensuse.

You need to use where the grub boot files are actually located
for each OS. So after you get your correct grub entries decided
(including an entry for Vista) you will need to reinstall the
Ubuntu grub to the MBR. (be sure there are no grub files on sdc)

Sudo grub 
grub>find /boot/grub/stage1

You need to match up the grub files on the Ubuntu partition with
the grub being written to the MBR. Since you have a few Linux OS
you will probably find that stage1 files are more than one place.
Use the stage1 files for Ubuntu, maybe in sdb3 = (hd1,2)

grub>root (hd1,2) (If my guess is right)
grub>setup (hd1) (writes grub to the MBR of the second drive sdb)
grub>quit

Reboot and you should get the Ubuntu grub menu.lst you created.
This will work if you boot from sdb, second drive, from bios.
I don't know what you have on sda, anything which is bootable?
It is possible to install grub to the MBR of sda, first drive
in the setup step, setup (hd0), but then you need to add an entry
for that OS you want to boot up into your Ubuntu menu.lst so that it
appears as an option; looking something like (hd0,0) 1st partition.
You would want to use the correct (hd0,x) entry of the bootable OS.

---

### Post by Jo Owen on 2008-12-15
Does what he said about installing from within windows have any effect on the boot set up? 

ie. does grub need an extra hack to boot a loopback image from the windows filesystem?

Not sure of the answer, but i think that might be the problem which i think some answers so far have missed.

---

### Post by Kivamaki on 2008-12-16
fuzzybear:

sdb1 - 33.2 GB
sdb2 - 196.1 MB Linux Native
sdb3 - 29.2 GB Linux Native
sdb4 - 86.3 GB Extended
 sdb5 - 2 GB Swap
 sdb6 - 20 GB /
 sdb7 - 64.3 GB /home

When I installed Ubuntu within Windows, I had to choose the size of it, so I choose 30GB, so Ubuntu has to be either sdb1 or sdb3 since those are the closest to 30GB, and it was also the first OS/Partition installed on that empty HDD.

Next I installed Fedora, I manually created the boot, / partitions. Which I'm guessing to be sdb1 as (/) or sdb3 as (/) while sbd2 is the (/boot).

Finally I installed openSUSE, now I told it so use all 80GB remaining left on the HDD, so I believe it created three partitions which would be the sdb5 (swap), sdb6 20 GB, and the sdb7 (/home).


TeXtonyx:

I don't think Windows is installed on my sdb because..sdb and sda are completely different hardrives. I checked in Windows and it's harddrive is still intact and not partitioned. My Grub menus goes from this: Computer Starts >  Fedora Grub > Can get to Windows Grub > Can get to Ubuntu Grub.

So I either have to remove the Fedora Grub so Ubuntu Grub will be my default, or just add all my OS's under the Fedora Grub.

Yes, I installed in this order:

Vista (DIFFERENT HDD)
Ubuntu (DIFFERENT HDD, not the same HDD as Vista)
Fedora (Same HDD as Ubuntu)
openSUSE (Same HDD as Ubuntu and Fedora)
[B]
EDIT: I also did what you said and looked for stage 1 on Ubuntu in the Terminal, it came back (1,5). So I setup to (hd1) and changed it to boot from my second HDD in my BIOS, and now it brings up the openSUSE boot loader, which is the most current one I installed. Now I just have to figure out how to add correctly the other OS's to my menu.lst (or just have a default grub boot loader)[/B]

---

### Post by Kivamaki on 2008-12-16
6 pages behind, slight bump.

---

### Post by meierfra. on 2008-12-17
> Does what he said about installing from within windows have any effect on the boot set up? 

Yes, it does. Grub is not able to read  "ntfs" file systems and since  Wubi installed  Ubuntu inside  an ntfs file system (/dev/sdb1),  it is not possible to directly boot Ubuntu  from the Suse or Fedora grub menu (unless you copy the Ubuntu kernel from the Ubuntu partition to the Suse or Fedora partition).

I suggest to use EasyBCD to add Suse and Fedora to the Vista boot menu:

[Easy BCD]("http://neosmart.net/dl.php?id=1")
[Adding Linux to the Vista Boot Loader]("http://neosmart.net/wiki/display/EBCD/Linux")

You will need to install   Suse's and Fedora Grub to the boot sector of their partitions:
```
sudo grub
root (hd1,5)
setup (hd1,5)
root (hd1,1)
setup (hd1,1)
quit
```

---

### Post by TeXtonyx on 2008-12-17
That was a very insightful solution meierfra, I didn't figure out
that OP had Ubuntu/Wubi installed inside the Windows partition. 

I think Easybcd assumes that the Vista bootloader is installed to 
the MBR, but at the moment OP has Opensuse in the MBR so he will 
have to put Vista back into the MBR I think, using the Vista install
cd, or the Vista Recovery cd available from Neosmart. 

Kivamaki wrote: "I just want one boot loader with all my operating 
systems, can someone help me?" 

I think the Vista bootloader is the closest one can get to that goal
since a grub solution will also require booting the Vista bootloader 
to get to Ubuntu, so that meierfra's suggestion does that best. The 
primary Linux OS's and Ubuntu within Windows grub menus can be set 
to hidden with no time delay, so it will seem like there is only boot menu. 

To restore Vista to the MBR use the Command Prompt, which is at the 
bottom of the attached screenshot, and issue the following commands.

C:\bootrec /fixmbr     <enter>
C:\bootrec /fixboot    <enter>
C:\bootrec /rebuildbcd <enter>

---

### Post by meierfra. on 2008-12-17
[QUOTE=Tex]but at the moment OP has Opensuse in the MBR [/QUOTE]

Yes, but in the MBR of /dev/sdb:

[QUOTE=Kivamaki] it came back (1,5). So I setup to (hd1) and changed it to boot from my second HDD in my BIOS,[/QUOTE]

The Vista MBR in /dev/sda should still be intact.

---

### Post by TeXtonyx on 2008-12-17
> **meierfra. said:**
> Yes, but in the MBR of /dev/sdb:
The Vista MBR in /dev/sda should still be intact.
-------------------------

Kivamaki wrote:
"I don't think Windows is installed on my sdb because..sdb and sda are completely different hardrives. 

Yes, I installed in this order:
Vista (DIFFERENT HDD)
Ubuntu (DIFFERENT HDD, not the same HDD as Vista)
Fedora (Same HDD as Ubuntu)
openSUSE (Same HDD as Ubuntu and Fedora)"
-------------------------------

But fdisk says there is ntfs at sdb1. And you are likely right about 
Ubuntu/Wubi within Vista/sdb1. So we know Vista is installed on 
sdb1 and OP only mentions installing Vista once, and he is wrong
about Vista being on a DIFFERENT HDD if he only installed Vista 
once. I think there is a gap in his explanation, and I would
feel more comfortable if his fdisk report had included sda.

Nonetheless, you may be right as you have also figured out Wubi,
but I think you have done it with mirrors; it's magic to me. :-)
It does seem likely though that there is some bootable OS on sda.

---

### Post by texasjim on 2009-01-06
OPENSUSE causes a lot of this grief. I have had 2 bad experiences installing OpenSuse on different systems.  In both cases it has stolen the MBR and ignored my other systems.  My easiest solution is to use the SuperGrub stand-alone cd to fix it. Use Linux>2 option and Auto.

I'm about to decide downloading OpenSuse is a waste of bandwidth.

  Jim

---

### Post by bodhi.zazen on 2009-01-06
> **texasjim said:**
> OPENSUSE causes a lot of this grief. I have had 2 bad experiences installing OpenSuse on different systems.  In both cases it has stolen the MBR and ignored my other systems.  My easiest solution is to use the SuperGrub stand-alone cd to fix it. Use Linux>2 option and Auto.

I'm about to decide downloading OpenSuse is a waste of bandwidth.

  Jim

Multibooting is a bit of a problem (not limited to OpenSUSE). Fedora will also behave the same way.

There is a secondary issue, why happens when you update the kernel ?

See the thread on multibooting to make life easier.

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by texasjim on 2009-01-07
> **bodhi.zazen said:**
> Multibooting is a bit of a problem (not limited to OpenSUSE). Fedora will also behave the same way.

There is a secondary issue, why happens when you update the kernel ?

See the thread on multibooting to make life easier.

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")
Thanks,I'll give it a look.  An opportune time; I'm just installing a 500G drive and migrating 2 40G's to it, same cast of characters- XP, Ubuntu, and the new OpenSuse release.

  Jim

---

