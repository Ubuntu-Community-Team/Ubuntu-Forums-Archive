---
title: "Playing Linux Natives... on Windows?"
date: 2009-10-07
forum: Gaming &amp; Leisure
---

### Post by ErikEhlert on 2009-10-07
As much as I hate windows, I am in fact going to start Dual Booting by putting Ubuntu on 1 Terabyte Hard Drive (That's 1000 Gigabytes! :D) with Windows 7. 500/500, so I don't have to constantly switch between my Ubuntu and Windows 7 Eval. Hard Drives. Now, question is, is there a way to download Linux Native games like Nexuiz and Sauerbraten and play them on Windows whenever I am not running Ubuntu?

---

### Post by hikaricore on 2009-10-08
Unlike most windows games, the games you've listed are crossplatform and can be downloaded from their individual websites.

This is one of those rare cases where I'll suggest using Google instead of asking here.

---

### Post by Sindwiller on 2009-10-08
As hikaricore said, you can just download the .zip/tarball provided on the official project websites, which usually include both .exe's and Linux binaries, so it's no big deal. For stuff like that, I'd recommend either setting up a third FAT32 partition or using [this ext2 driver for Linux]("http://www.fs-driver.org/"), the latter being the obviously more dangerous variant.

---

### Post by Saghaulor on 2009-10-09
I'm sure you have your reasons, but I have to ask. Why would you want to run those games on Windows if you don't have to?

Usually it's the other way around, namely, running games on Windows because you don't have a choice. I guess I don't understand.

Don't get me wrong, I like Windows 7. But I really like Ubuntu.

---

### Post by hessiess on 2009-10-09
Instead of installing windows native, set it up on a VM.

---

### Post by Nevon on 2009-10-09
> **Sindwiller said:**
> For stuff like that, I'd recommend either setting up a third FAT32 partition or using [this ext2 driver for Linux]("http://www.fs-driver.org/"), the latter being the obviously more dangerous variant.

I would not recommend a FAT32 partition, as those are very prone to error and cannot handle files larger than 4gb. Using ntfs-3g, he could access his NTFS drive anyway - and that's much, much better.

---

### Post by Dark Aspect on 2009-10-09
> **hessiess said:**
> Instead of installing windows native, set it up on a VM.

+1

Virtual Machines have much better 3D opengl support if the OP has a semi-powerful computer. Also does ErikEhlert have a flash drive, if so you could just use Linux from USB. I recommend [Puppy Linux]("http://www.puppylinux.org/") for this task.

Edit: Oh sorry I thought Hessiess meant set Ubuntu up as a VM, mis-read post.

---

### Post by hikaricore on 2009-10-09
The OP has from what I can tell a low end system with an integraded video chipset which has little to no opengl support.
I'd imagine that he's just frustrated with this affecting his gameplay.

---

