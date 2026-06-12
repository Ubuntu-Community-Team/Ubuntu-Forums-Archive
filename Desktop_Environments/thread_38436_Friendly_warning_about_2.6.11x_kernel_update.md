---
title: "Friendly warning about 2.6.11x kernel update"
date: 2005-05-31
forum: Desktop Environments
---

### Post by GTKpower on 2005-05-31
Just a friendly user-to-user warning about possible problems when updating to the 2.6.11x kernel via Synaptic.

It *might* make your Hoary installation unbootable.

This is not intended as a criticism of the Ubuntu dev team, as there is no such thing as utter perfection when it comes to an OS and the hardware it runs on (not even Apple can claim this!), but rather, as a friendly warning about a possible problem that warrants attention.

If you already hve the 2.6.11x kernel installed and everything runs fine, then great.

There have been, however, 2 or 3 documented cases already where this recent kernel update has caused serious problems, such as rendering Linux unbootable.

If you have yet to perform this kernel update, back up your data just in case, or better yet, hold off on this particular update.  Nothing wrong with using the 2.6.10 kernel for a little while longer.

---

### Post by Martin Witte on 2005-05-31
I did an install of a Debian unstable a few weeks ago (hardware is a Sony Vaio-PCV-W1), my system also became unbootable after upgrading it to a 2.6.11 - 686 kernel - I do not recall the exact error, but in booting a fatal error occured which kept on repeating.

---

### Post by Jenda on 2005-05-31
So, as an almost n00b, when's the time to update the kernel? Which version should I wait for? Is there sth like stable/nightlys in the case of the kernel?

---

### Post by 23meg on 2005-05-31
there's a known issue with gnome that locks it down at startup (it's been solved; see [this thread](http://www.ubuntuforums.org/showthread.php?t=25247&highlight=2.6.11)), but i haven't had or heard of any issue that completely locks down the computer before it reaches that point in the boot sequence. at what point exactly does yours hang?

---

### Post by 23meg on 2005-05-31
[QUOTE=Jenda]So, as an almost n00b, when's the time to update the kernel? Which version should I wait for? Is there sth like stable/nightlys in the case of the kernel?[/QUOTE]

practically, the best is to wait for a stable version, and see if that version has any specific issues with your distro and desktop environment. 2.6.11 is stable right now, but there are some issues, it seems (i've not had any, and many others report the same though). even if it can't boot, you can still boot into Ubuntu if you don't remove your older kernel (which is a wise thing to do) by choosing it from the grub boot menu.

you can track kernel development at [http://www.kernel.org/](http://www.kernel.org/) .

---

### Post by GTKpower on 2005-05-31
Meg makes a good point .. . . . 

Specifically, (this happened to me), when Synaptic is nearly finished updating the kernel, it will stop, and wait for your input.  If you open the console thru Synaptic, it asks you a "yes" or "no" question - whether you want to add the new kernel to the bootloader, if I remember correctly.

It seemed logical to add it to the bootloader.  Computers being computers, however, logic sometimes works backwards.  By adding it, I *think* I doomed my installation.  I got VFS errors on bootup, and it would no longer recognize my root partition, kernel panic, etc.  It made my Linux totally unbootable.  Not even the partitioner on the installation CD could fix it.

My guess would be to select "no" when you get to that point.  It DID give an explanantion as to what each course of action would do, to be fair, but I understood it the wrong way, it seems.  Since I'm a fairly reasonable guy, with a University education, I'm guessing this might cause quite a few people some grief, not just me.

Maybe Meg can explain this "yes" or "no" point a bit further . . . . . ?

---

### Post by 23meg on 2005-06-01
hmm, i don't recall getting this option while installing the kernel; maybe it defaults to adding to the menu if you don't take any action? 

your grub is installed on your mbr, right? do you have windows installed as well, and did you let any windows partitioning utility such as partition magic "correct errors" on your mbr or fat? i've heard this can lead to errors in situations similar to yours, and barely escaped such a disaster myself. hope you didn't lose any data :/

---

### Post by Martin Witte on 2005-06-01
I do not recal exactly when it went wrong, to my memory I got the described fatalities  when I rebooted after installation. Grub is in my master boot record, I do have three operating systems (Debian, Ubuntu and Windows XP) on one disk. I did not use any partition tools after the fatall experiment. I use the Grub of Debian - at that time from the unstable repository. I do have a system rescue cd ([www.sysresccd.org](www.sysresccd.org)) at hand to re-install grub in a working linux partition.

---

### Post by GTKpower on 2005-06-01
No Meg . . . the last time this drive has ever seen windows was nearly a year ago.  Since then, it's been all Linux and ext3.

Yes, Synaptic stopped right before it finished updating my files.  Synaptic rarely stops, but when it does, I know I hve to click on the console view in the Synatpic window and see what it wants.  I got that question, selected "yes" (naturally, I'd like to install the new kernel image onto the MBR), and that basically doomed my installation.

It's alright now, I had all my data backed up, and I have a fresh installation of ubuntu.  It's a bit of pain to reconfigure everything, but that's life.

---

