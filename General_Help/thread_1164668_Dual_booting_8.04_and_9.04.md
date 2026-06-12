---
title: "Dual booting 8.04 and 9.04"
date: 2009-05-19
forum: General Help
---

### Post by kooldino on 2009-05-19
Ok, so I'm ready to install 9.04 on my main rig.  However, I want to do a fresh installation of it.  That said, I'm not yet willing to part with my 8.04 installation.

One of the physical disks in my machine is dedicated for the OS.  It has two partitions, the OS and the swap.

How can I set this up?

Can I run the 9.04 installation CD and have it split the OS partition into two, and run 9.04 on one and 8.04 on the other?  Can I just stick with a single swap partition? Will GRUB work everything out for me?  What happens when I finally want to blow away the 8.04 partition?

Thanks in advance!

---

### Post by geraldvillorente on 2009-05-19
here is a simple partition design:

Assuming you have single HDD...

/primary   | for first OS
/swap      |

and

/logical   | for second OS
/swap      |

---

### Post by zvacet on 2009-05-20
Ubuntu installer will give you option to resize existing partition.On that unallocated space install Jaunty.No need for two swap partitions.

---

### Post by kooldino on 2009-05-20
Ok, cool...so it's safe to run one swap partition for both?

And later when I want to remove 8.04, what's the cleanest way to do it that won't upset GRUB?  Do I just delete the partition and reclaim that space with my 9.04 partition?  Will GRUB automatically detect this?

---

### Post by coffeecat on 2009-05-20
> **kooldino said:**
> Ok, cool...so it's safe to run one swap partition for both?

Oh yes. I've set all my machine up as multiboots and it makes sense to have just one swap partition. The only exception is if you use hibernate, when an image gets dumped to the swap partition. If you hibernate from OS 1, and then boot into OS 2 instead of 1, the swap image of OS 1 will get corrupted so that you won't be able to restore your OS 1 session later. That's never been a practical problem for me as I find a fresh bootup to be as quick as a restore from hibernation.

> **kooldino said:**
> And later when I want to remove 8.04, what's the cleanest way to do it that won't upset GRUB?  Do I just delete the partition and reclaim that space with my 9.04 partition?  Will GRUB automatically detect this?

You'll be OK **if** you're using the Jaunty grub - which you probably will be because, by default, the Jaunty installer will detect the Hardy installation, install grub to the Jaunty partition and set up a dual-booting menu. (Triple-booting if you've got Windows or a third OS there.)

Grub stage 2 in the Hardy partition then becomes superfluous and grub stage 1 and 1.5 will be set up to call grub stage 2 in your Jaunty install.

But if anything ever goes pear shaped with grub, it's the work of a couple of minutes to repair grub from a live CD, from SuperGrubDisk or from many other utility CDs. And there's a whole army of helpful members here willing to guide you. :)

But by the time you're ready to ditch Hardy, Languid Lion, (or is it Lolloping LLama?), will be out, and you'll be wanting to dual-boot this with Jaunty. So that partition will come in useful. :p

---

