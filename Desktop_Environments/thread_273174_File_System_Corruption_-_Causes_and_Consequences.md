---
title: "File System Corruption - Causes and Consequences?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Ingla on 2006-10-07
Hi.

I'm running Breezy. Lately, I've been expriencing unexplained total freezes which leave me no option but to hit the button (no mouse or keyboard). These are not associated with any particular action on my part, but may be caused by one or more programs ... or having them running together. There is also no regular time period. Breezy may run fine all night or may freeze after just a few minutes and keep doing it. 

I haven't figured out what's causing this, but I'm concerned about some of the apparent results.

Specifically, the file system gets messed up fairly regularly. On boot, I frequently (sometimes after 30 boots and sometimes because of corruption in the meantime) get kicked into a console running fsck. The results are usually similar. Fsck fails and needs to be run manually.

The readout looks something like this (not taken from my machine, but very similar):

--------------------------------------------------------------------------
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Backing up journal inode block information.

PALFA_A103 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 4133: 78675968 78675970 78675972 78675973 78675974 78675977 78675978 78675979 78675982 78675983 78675985 78675986 78675987 78675989
Pass 1C: Scanning directories for inodes with multiply-claimed blocks.
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

File /p2030/p2030.G48.75-00.17.C.wapp3.53910.0091 (inode #4133, mod time Sat Jun 24 02:16:36 2006) 
  has 14 multiply-claimed block(s), shared with 1 file(s):
        <filesystem metadata>
Free blocks count wrong for group #0 (24533, counted=24519).
Fix<y>? yes

Free blocks count wrong for group #2401 (14795, counted=14809).
Fix<y>? yes


PALFA_A103: ***** FILE SYSTEM WAS MODIFIED *****
PALFA_A103: 280/95392 files (8.9% non-contiguous), 92570714/97677200 blocks
-------------------------------------------------------------------------

Actually, my system contains a larger number of mulitply claimed blocks in several inodes. And it requires more cloning and fixing.

I answer "yes" to all requests to clone and fix, and then reboot. That makes everything fine until the next time.

HOWEVER, each time I see that the percentage of non-contiguous files grows by about .1%. At present, it's only 2.2%, but I'm wondering where this will lead and whether anything can be done to fix it. 

Under Windows, I have programs which will make everything contiguous, but have no idea whether or how I can do that on Linux. Sooner or later, I assume this will begin to affect performance more and more.

Can anyone help me understand what's happening and especially what, if anything, I can do about it?

Any guidance much appreciated.

---

### Post by ajgreeny on 2006-10-07
Are you sure your hard disk is OK?  It sounds as though it may be at fault.

As for non-contiguous files etc, there is no real way, or need to do anything about it, and there are no commonly available programs to defrag, which is the same thing as you talk about in windows, in linux.  the file systems used, ext3 or perhaps reiser, are much better at dealing with defragmentation than either ntfs or fat32, and as a result, Imhave never seen the percentage on my machine which I mess about with a lot, get above a max of 4%, and then next time it will be back to about 1.5 - 2%.

As for the freezes, have you checked sufficient coolong of the cpu as that can freeze the action completely as I recall from my old windows days and a previous machine.  Worth checking.

---

### Post by crazymonkey on 2006-10-07
You might also want to check your RAM, try using mem86 test, it should be in your grub or use it from the livecd. I already had problem with unexplained freeze and after a while I realised they were caused by defective RAM.

---

### Post by Ingla on 2006-10-07
Thanks.

I don't know about the hard disk ... it's pretty new. As for other hardware problems, I'm not getting freezes on Windows (although some other weird stuff has happened there). It's a separate hard disk ... same machine.

Synaptic shows me I have memtest 86 installed, but I can't figure out how to run it. Terminal response to probable commands is "command not found". Can you tell me how to run it?

---

### Post by crazymonkey on 2006-10-07
> **Ingla said:**
> Thanks.

I don't know about the hard disk ... it's pretty new. As for other hardware problems, I'm not getting freezes on Windows (although some other weird stuff has happened there). It's a separate hard disk ... same machine.

Synaptic shows me I have memtest 86 installed, but I can't figure out how to run it. Terminal response to probable commands is "command not found". Can you tell me how to run it?

When you boot your computer there should be an entry in GRUB for memtest86 (grub is the menu in which you choose to boot Windows or Ubuntu when you start your computer). If you cant find it there try to boot on Ubuntu live cd, you will have a couple of option (Install and other) and you should see Memtest option.

---

### Post by Ingla on 2006-10-07
Thanks.

I started the test from the GRUB menu. About half way through the first pass, it started showing errors. I don't know how to interpret the test and I stopped it after a few minutes. 

I assume that all those bad addresses and errors mean memory trouble in any case. So, I'll start with that. I think the latest memory chip is still on warranty.

Thanks for the help. I didn't know I had a memory test program installed.

---

### Post by crazymonkey on 2006-10-07
If you have more than one chip you can try to remove one and run the test on the remaining and switch after to figure out which one is defective. Once you find the defective one you can always run linux on the good chip, you will have less ram but your computer will be more stable.

---

