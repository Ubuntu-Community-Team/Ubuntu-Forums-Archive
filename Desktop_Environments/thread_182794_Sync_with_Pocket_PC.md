---
title: "Sync with Pocket PC"
date: 2006-05-26
forum: Desktop Environments
---

### Post by link141 on 2006-05-26
I have an HP iPAQ that I'd like to sync with on Kubuntu Dapper, but Active Sync didn't work correctly under WINE (latest version).  I have suspicion that I might not be able to find a solution, because my pocket pc is running Windows Mobile.
Does anyone know a program that I can use to extract files from my pocket pc?
Thanks in advance

---

### Post by Jucato on 2006-05-26
I'm not exactly sure how you do it, but there's a Linux app that acts like Active Sync called SynCE. For instructions, go to [http://synce.sourceforge.net/synce/](http://synce.sourceforge.net/synce/)

---

### Post by corstar on 2006-05-28
thanks for this. I have just purchased a hp ipaq (after not being able to find a sharp zaurus anywhere) and relieved to have found kde-synce.
I hope to install opie on it too(open source operating system for pda's)

---

### Post by BooVeMan on 2006-11-19
Hi,
i did install opie and all worked well - only i didn't kept PocketPC/Windows mobile - as I neither used outlook nor windows :-). If you get stuck - just ask.

---

### Post by mosibfu on 2007-04-23
hehe well i tried, i kinda got the problem that it didnt detect my phone :( do u remember what u did/what guide youve done? ive done a couple but none seemed to help.

---

### Post by link141 on 2007-08-06
I've been researching installing linux on PDA's (particularly the iPAQs) for a while, and I found (just today) that there's a version in development (yeah!!:D) that might work on my iPAQ hx2410.  Unfortunately, a site that had compatibility ratings for linux on PDAs didn't have one with iPAQ hx2XXX, even though they had it listed (they were having trouble getting it to boot with WM2005 on the hx27XX variant).  I read through a couple of emails though, and it seems like someone with the exact same model of iPAQ got Familiar Linux to boot up and everything!!  Based on what I've read, it seems like that's the hard part, and from there its easy to install OPIE, GPE, or whatever other Linux PDA environments there are out there.  Maybe I'll take the plunge, and go for it, I can always have HP fix it if it totally craps out on me. 

> **BooVeMan]
Hi,
i did install opie and all worked well - only i didn't kept PocketPC/Windows mobile - as I neither used outlook nor windows :). If you get stuck - just ask.
[/quote] 
I don't like windows or use outlook either, and they're both coming off if I succeed  said:**
>  hehe well i tried, i kinda got the problem that it didnt detect my phone :( do u remember what u did/what guide youve done? ive done a couple but none seemed to help.
Are you trying to install Linux, or get it to sync with Linux.  As far as syncing, I had some problems figuring out how to get my device to connect with Linux correctly until I found out that it used a serial/usb connector, and I had to use synce-serial instead of vdccm.  After that, synce/raki picked it up fine, and I was able to install CAB files, transfer files to/from my iPAQ, and even mirror it to my computer (something windows couldn't do ;)).  Whether you'll have success or not depends largely on what model of phone your using, and how you connect it with the computer.  I'll write a post on how I got mine working when I have more time and I'm more awake, but for now, this link might help: [Official SynCE wiki](http://www.synce.org/index.php/SynCE-Wiki).  Good luck ;).

Thanks guys,
link141

---

