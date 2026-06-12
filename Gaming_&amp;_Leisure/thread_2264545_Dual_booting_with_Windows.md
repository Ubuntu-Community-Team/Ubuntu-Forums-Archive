---
title: "Dual booting with Windows"
date: 2015-02-08
forum: Gaming &amp; Leisure
---

### Post by greg69 on 2015-02-08
I'd like to dual boot my Xubuntu setup with Windows for gaming purposes. (7, 8 or 8.1, I'm not fussy so long as it works) And I'd like some pointers.

Firstly, What are the security implications? I've heard the scare stories about windows without AV protection being crackable in 20 seconds or less but is that true? Especially if I'm doing no browsing on the partition? What if I did regular ClamAV scans or similar on the partition?

Secondly, How much of a hassle is it to resize one of my 500GB hard drives with a 350GB or so windows partition? It ought to be quite easy but if windows detects Xubuntu on the install will it wipe it or in some other way handicap it?

Thirdly, I can get a copy of Windows 8.1 from the microsoft website for about £50 because it's a student license and I 'am' a student. This will also enable me to upgrade to windows 10 in the future.

Lastly, I run off a home network. With cameras and a few servers and such. Those all run Linux. Also variants like KDE and such. Would Windows or any malware affect those? 

Thanks. I appreciate the help.

---

### Post by oldrocker99 on 2015-02-08
The best way to dual boot is to install Windows **first.** Then, boot the Linux DVD or, preferably (to save a lot of time), a USB. There's a cross-platform program, unetbootin, which will install a Linux .iso to make the USB bootable. Make sure the USB is formatted to DOS format before using unetbootiin.

Then, after you boot, you'll come to a screen asking you how you want to install Linux, wiping the drive, or side by side. I would recommend "Something Else." That will allow you to make two partitions. The first is small (64-96 GB is probably plenty), and formatted ext4 (the Linux file system), and mounted as /, the system folder. The other partition, which is really never too big, is also formatted ext4, and mounted as /home, which is where all your downloads and program settings are stored, and is the only folder you, as the user, have full read-write access to. This will allow you to easily install a different system without having to restore all the files in your /home folder.

If these instructions are confusing, feel free to ask questions. That's what this forum is for.

---

### Post by greg69 on 2015-02-08
I've got experience with Unetbootin and I'm sure I can resize a partition if I try to. I've formatted disks in the past and I've done multiple reinstalls so these instructions aren't difficult to comprehend. I had XP for a while but switched to Fedora, Mint then Ubuntu. 

Thanks for the tips. Now I need to ascertain if the security risks are worth the extra compatibility I can get. It's disappointing that I have to pay £50 for a windows copy that I'll only use because I have to. It'll be nice when steam machines come out and this isn't needed.

---

### Post by oldrocker99 on 2015-02-08
You don't really need a Steam machine to use Steam for Linux. SteamOS is built on the latest Debian stable version, but just about **any** Linux distribution will run Steam very well, on Debian-based systems (like Ubuntu and Mint), Fedora-based, Arch-based, OpenSuSE, and Slackware (users have reported success on all those systems). 

It is strongly advised to use nVidia graphics (I do, and have had zero graphics problems), but a lot of people have had success with ATI. I did have a good experience with the twisted shooter Painkiller:Hell and Damnation, which ran for me on Day One. It took 5-6 weeks for a proprietary ATI driver to be able to run the game. Just sayin.'

Steam has over 900 games for Linux, including AAA titles like CIV V, X-COM, Borderlands 2, CIV:Beyond Earth, Empire:Total War, the current RTS champ, Planetary Annhilation, and many, many more. I quit using (the quite annoying, to me) Windows when X-COM came out for Linux, and I'm not looking back, either. I see zero reason to **pay** to use Microsoft again. Who needs the bugs, the viruses, the "I'll decide for you when I want to reboot" annoyances, the "Windows cannot update files when they are in use" messages? Linux **can** update files when they are in use. What a concept...

Of course, you are completely free to install Windows if you choose.

---

### Post by greg69 on 2015-02-08
I run Steam already but Steam machines are the Catalyst that will (Hopefully) spark the big AAA title devs to make games on linux.
I run a GTX 760 after upgrading from an ATI 7750.
I'll only use the partition for games such as Payday 2 and Skyrim. Which I've failed to get working on WINE.


I've had a chat with a few people and they say that apparently it can catch a variety of viruses without even browsing the internet or opening emails.
My Dad is mainly concerned about the Windows partition attacking the other components in the house on the network. (which run linux and a variety of security protocols) Is he overreacting or should I take special precautions on dealing with my Windows partition? (Such as a firewall or something else).

---

### Post by oldrocker99 on 2015-02-08
One more point; it is pretty critical to defrag Windows before installing any Linux distro. Windows tends to scatter files hither and yon all over the partition, and some of them are essential, so try to get the partition as defragged as possible. Of course, Linux doesn't fragment files; it writes the file to the smallest free area in one piece.

Again, such a concept;).

---

### Post by greg69 on 2015-02-08
Note: If I run Ubuntu on my SSD and the other drive is just storage, Can I install Windows on the other drive without risking my drive space, defrag it, Then shrink the partition to an OK size and use the other part for my Ubuntu partition?

---

### Post by oldrocker99 on 2015-02-08
With an SSD, I would install Windows and then Linux on the same SSD (128GB is, again, plenty for both systems). Use the other drive for /home, and/or your Windows document/settings and Program Files directories. If you want to use Windows, I'd divide it into two partitions, one NTFS, which Ubuntu (or any other Linux distro) can read and write to, and use the other, ext4 partition for /home, which you might be able to access with a Windows ext reader, or might not. You do need to keep the partitions separate, of course, and they can both be NTFS, which has somewhat inferior performance compared to ext4.

> ...Skyrim. Which I've failed to get working on WINE.

If you install PlayOnLinux, a terrific frontend for wine, you can, as I successfully did, use the included script to install Steam for Windows, from within which you then install Skyrim. It worked for me on a 965 Phenom with a GeForce 650ti, and plays at least as it did on Windows. On my current rig it screams. I also installed Oblivion in the same Steam window, and it runs like a champ. I can't tell you about Payday 2, though.

---

### Post by connor16 on 2015-04-10
You shouldn't have any trouble with the other devices on the network. If this answers your question, you should be okay with just the default Windows firewall

---

### Post by psfal on 2015-04-10
I attempted to install Ubuntu 14.04 alongside Windows 8 on my step-daughter's dell, Ubuntu doesn't find any other operating systems on the machine. Is this a UEFI issue? Do I have to set the BIOS to Legacy boot? I've done some dual-boots with Windows 7 with no issues, this is the first time I've tried it with Windows 8.

I solved it, she's just gonna have to deal with not having a Windows option if she wants Ubuntu, her choice...

---

### Post by MikeCyber on 2015-04-13
I remember that Grub needed:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
when I've installed 14.04 with Windows 8.1 a year ago.

PS: Grub also needs a active partition or disk.

---

