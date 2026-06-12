---
title: "ATLAS on Windows PC and Ubuntu PC dual booted."
date: 2022-05-01
forum: Gaming &amp; Leisure
---

### Post by makem2 on 2022-05-01
I have two 1TB SSD drives and one is devoted to games. Steam has its Download folder on the games SSD and while I waited for 22.04 to be available I installed ATLAS in windows 10 using the ATLAS data in the Steam download folder.

Ubuntu 21.01 would not play the game at all. I have updated 21.10 to 22.04 and am using an NVIDIA  GeForce RTX 3060 gfx card.

I have installed Steam in Ubuntu and set it's Download folder to the same data used by windows.

When I try to play ATLAS on Ubuntu I select 'Play' and ATLAS has a Launching message. It then has a 'Cancel' option followed immediately by a 'Stop' option. Now, it immediately reverts to the 'Play' option. Prior to that, as expected it downloaded and updated files totalling 6.

Has anyone got this game working in Ubuntu?

---

### Post by TheFu on 2022-05-01
I don't game, but something that jumps out to ask is whether the file systems used are native to Linux - i.e. NOT NTFS.

---

### Post by makem2 on 2022-05-03
> **TheFu said:**
> I don't game, but something that jumps out to ask is whether the file systems used are native to Linux - i.e. NOT NTFS.

You are correct. Because the game failed to work in 21.10 I used NTFS because I was running the game in Windows.

However, I did think that as Linux is capable of reading and writing NTFS files that it should work.

Is there a reason you are aware of which would prevent this?

I will see if I can get Steam to move the download folder of ATLAS to ext4 and if that is possible it may well work. I think Steam can have games on multiple folder.

Like you, I never gamed for most of my life but Covid got me into it (Thats my excuse anyway)

---

### Post by TheFu on 2022-05-03
Linux expects Unix file and directory permissions.

I don't game on full computers.  Pull out a PS2 console for a few days every other year.  I do play mind games on Android.  And most days the game I play most is the "evil operator from hell" - that's interactive with other people and they pay me! ;)

People shouldn't trust NTFS on Linux as much as they do.  The code has been poorly maintained for years. Even the new code, added to the kernel about a year ago, hasn't been maintained. The project team spent years to get some proprietary code ready and accepted (it was rejected 3-5 times by Linus), then they appear to have thrown it over the wall and nobody has touched it.

When I use NTFS, it is with the expectation it will be corrupted. In my use, that happens about every 3 months and I'm forced to reformat the partition.  I only use it when there isn't any other choice or the other choice is even worse, like FAT32.

---

### Post by makem2 on 2022-05-03
> **TheFu said:**
> Linux expects Unix file and directory permissions.

I don't game on full computers.  Pull out a PS2 console for a few days every other year.  I do play mind games on Android.  And most days the game I play most is the "evil operator from hell" - that's interactive with other people and they pay me! ;)

People shouldn't trust NTFS on Linux as much as they do.  The code has been poorly maintained for years. Even the new code, added to the kernel about a year ago, hasn't been maintained. The project team spent years to get some proprietary code ready and accepted (it was rejected 3-5 times by Linus), then they appear to have thrown it over the wall and nobody has touched it.

When I use NTFS, it is with the expectation it will be corrupted. In my use, that happens about every 3 months and I'm forced to reformat the partition.  I only use it when there isn't any other choice or the other choice is even worse, like FAT32.

You actually get paid for being evil!!

I get where you are coming from and agree. I too only touch Windows when I have to.

I have moved the files to an ext4 drive using the Steam 'app' from the repositories. It downloaded and installed a Windows Distributable (I forget the full name) and started the splash screen. It then showed a Fatal Error message listing maybe 40 errors.

[https://drive.google.com/file/d/1e0sgTiWGuwAsIDh6mxYszqDVqeRYgWY3/view?usp=sharing](https://drive.google.com/file/d/1e0sgTiWGuwAsIDh6mxYszqDVqeRYgWY3/view?usp=sharing)

When I realised that Steam was available from the repos. I crossed my fingers that the game would now work. I tried starting it without using Battleye with the same error list.


[IMG]https://drive.google.com/file/d/1e0sgTiWGuwAsIDh6mxYszqDVqeRYgWY3/view?usp=sharing[/IMG]

---

