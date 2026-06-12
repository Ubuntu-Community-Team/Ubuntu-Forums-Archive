---
title: "Help with slow hard drive"
date: 2009-01-07
forum: General Help
---

### Post by yesfan on 2009-01-07
--------------------------------------------------------------------------------

I have a 500 gb WD external hardrive connected to the usb port. I had the same computer using windows running it and it was quick. I only run music on it but I have a lot. When I click on a folder it takes like 5 minutes to open then when I click on a folder of the artist it can take another 5 minutes. At the top of the screen it says The Media contains software. Then to the left there is a tab that says open autorun prompt. When I click on that it says cannot find autorun program. Evcerywhere I try to run the autorun it still says the same thing cannot find the autorun program. I am not great with computers does anyone know why the hardrive is so slow and will the autorun program make it work faster. I only use the computer for playing music and surfing the web. There are no other programs or anything on the computer. Thanks.

---

### Post by -kg- on 2009-01-07
> **yesfan said:**
> ----------------------------------------------------------------

I have a 500 gb WD external hardrive connected to the usb port. I had the same computer using windows running it and it was quick. I only run music on it but I have a lot. When I click on a folder it takes like 5 minutes to open then when I click on a folder of the artist it can take another 5 minutes. At the top of the screen it says The Media contains software. Then to the left there is a tab that says open autorun prompt. When I click on that it says cannot find autorun program. Evcerywhere I try to run the autorun it still says the same thing cannot find the autorun program. I am not great with computers does anyone know why the hardrive is so slow and will the autorun program make it work faster. I only use the computer for playing music and surfing the web. There are no other programs or anything on the computer. Thanks.

I'm not sure why your disk access is so slow, but you can't autorun the software on the disk because the software is for Windows OS.  A lot of the software on the disk has to do with Windows backup software, etc. (unless you got a MAC version, which I did).

I have a WD 1 TB drive with the same software.  I've never had access speed problems with it, however.  Someone on the forum will be able to help you with access speed.

---

### Post by kyalee on 2009-01-10
I have an 80GB Beyond Micro External HDD and I'm having the same problem. When it's hooked up to my Windows machine, I can transfer files in no time. With Linux, the transfer crawls. I'm researching it now (which is how I found this post), but maybe someone here will have an answer. Or, if I find something in my searching, I'll come back and tell you what I found.

---

### Post by vladi11 on 2009-01-10
I can confirm that.
I have an external USB drive (WD 500 GB) and the transfer rate is terribly slow (around 1 MB/s).
It used to work OK before (under Ubuntu) = 15 MB/s, but not now.
In Windows XP it works fine.
Any idea ?
Thank you.

---

### Post by todak on 2009-01-10
Different file system formats maybe? NTFS<>ext3.

---

### Post by vladi11 on 2009-01-10
> **todak said:**
> Different file system formats maybe? NTFS<>ext3.

Copy from NTFS to NTFS = 775 KB/s
Copy from NTFS to EXT3 = 780 KB/s

I found out it's a known bug :(. [[COLOR="DarkOrange"][COLOR="Red"]Here[/COLOR][/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762")

---

### Post by kyalee on 2009-01-10
From what I can tell searching the forums, it's a problem several people have had and it doesn't look like there's a known easy solution. I read one thread that had a lot of people trying to troubleshoot it, but most of it went over my head and they didn't even seem to come to any conclusions about the best way to deal with it.

I hope the developers know about the problem and are working on it. Files transfer at about 900Kb/s for me and that's really frustrating.

---

### Post by todak on 2009-01-10
Have you tried checking the transfer rate with a large file, say a DVD iso, as opposed to many small files? I have found that  the transfer rate decreases over time when transferring single very large, ~4GB, files. However when I transfer the equivalent file size (about 4GB) consisting of a folder that has 600-700 small files and subfolders, the transfer rate does not slow down.

---

