---
title: "Uninstalling WUBI"
date: 2008-12-17
forum: General Help
---

### Post by gself on 2008-12-17
I hate to start yet another thread about uninstalling WUBI, but I have not seen a solution for my set of circumstances. I installed Ubuntu 8.10 on a Windows XP machine using WUBI. I checked the partitions on that machine and have only a single NTFS partition of just under 80G (it's an 80G drive), so I know I didn't accidentally do a dual-boot installation.

Now, I would like to uninstall Ubuntu and re-install it in its own partition (like it should have been from the beginning). However, I cannot seem to uninstall what's already there.

There is nothing in my Windows Add/Remove programs list that says WUBI, Linux, Ubuntu, or anything else that looks right.

I downloaded the Ubuntu-Uninstall.exe file and ran it, but it did not seem to do anything.

There is no directory called C:\Ubuntu* or anything like it. (Well, there is a directory called C:\ubuntu-backup, but it is empty.)

There is no directory in the My Documents folder that looks suspicious. There is no directory in my Windows folder that looks like it may belong to Ubuntu.

I did a file search for any file greater than 100M thinking I could find the Ubuntu file that way. Nothing.

My Gawd - Ubuntu is really hiding on my disk somewhere :)

I'm kinda down to just re-formatting the entire hard drive and re-installing everything (which, frankly, wouldn't be such a bad thing since it needs to be cleaned up anyway). Before I take that drastic step, though, I wondered if there was anything I'm missing.

Thanks for any help you can offer.

--George Self

---

### Post by Sef on 2008-12-17
> I'm kinda down to just re-formatting the entire hard drive and re-installing everything (which, frankly, wouldn't be such a bad thing since it needs to be cleaned up anyway). Before I take that drastic step, though, I wondered if there was anything I'm missing.


I have used [Easy Uninstaller]("http://www.download.com/Easy-Uninstaller/3000-2096_4-10286873.html?tag=mncol").   I would recommend trying to uninstall WUBI with that.  It is a no cost installer.   The link above is through download dot com.

---

### Post by ago on 2008-12-19
So is it just disk space missing? Check for a hidden folder called c:\found.000...

---

