---
title: "help recovering data from external hdd?"
date: 2009-03-26
forum: General Help
---

### Post by shateredsoul on 2009-03-26
HI everyone... so I dropped my hard drive and now it is not recognized by ubuntu.  It is a western digital passport.  I was wondering if anyone could help me figure this out?

[http://ubuntuforums.org/showthread.php?t=861763&page=2]("http://ubuntuforums.org/showthread.php?t=861763&page=2")

I found that.. but the problem is that it does not appear at all in ubuntu. It does light up though.

I did df in Terminal and it does not appear.  I can open it... and pushed in the connectors to the hdd just in case that had disconnected or loosened nothing. 

In windows xp, it does install supposedly, but i do not see it under my computer or anywhere.  So I cannot do the fix the guy suggested at the end.."type chkdsk /f <DRIVE> in Start>Run" in windows.  The drive goes unrecognized.  

Any ideas?  I would like to recover the files with names.. i heard that photorec will recover with random file names.  I want to avoid that.

=(

---

### Post by absolutezero1287 on 2009-03-26
Post the output of "sudo fdisk -l" (without quotes).

---

### Post by shateredsoul on 2009-03-26
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

---

### Post by shateredsoul on 2009-03-26
and I get the same output when the external is connected...

/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

windows recognized it, but as WD instead of  mypassport like it used to.. and I can olny remove it, but I cannot open the harddrie or see it under my computer.

---

### Post by absolutezero1287 on 2009-03-26
I'm pretty stumped. The only thing I could think of is doing a reboot and seeing if the problem somehow works itself out. Alternatively, you can do a google search and see if anyone else shares your problem. Which I'm sure other people have had Ubuntu not recognize an external hard drive. However, since this happened after you dropped it it is possible that there's a hardware problem.

---

### Post by shateredsoul on 2009-03-26
Oh, i'm not sure if I explained my self well.  The problem is in Ubuntu and Windows xp.. I cannot access the external hdd, but where ubuntu recognizes nothing at all, windows recognizes something and installs it... but, I still cannot access the data from the external hdd in either OS.  I'm really not sure what windows thinks it's installing...

---

### Post by absolutezero1287 on 2009-03-26
Well the bottom line is that neither OS can access your data. In extreme situations I usually use a program called SpinRite to recover information.

Since you did mention dropping your external I'm led to believe that that is the main cause. Windows simply recognizes that "something" got plugged in but it can't read/write to the drive. Ubuntu doesn't recognize the drive and can't read/write to it.

Try it on another computer, perhaps? If this problems persists on another computer then its definitely a hardware problem. If this is the case then you may have to get another hard drive.

Maybe someone else has another opinion/solution?

---

### Post by shateredsoul on 2009-03-26
Yeah, that's what I was thinking.  I killed it... 

hmm.. well I can always buy a new hdd and put it in the casing.

I'm using a program called diskdigger on windows, it recognized a 2000 gb drive... which is weird considering that computer only has 60 gbs.  It's in the process of scanning that drive now, hopefully it's the passport.

After that I'll try that program you suggested, is it for pc of ubuntu?

---

### Post by Ericyzfr1 on 2009-03-26
Under XP there is a lot of free recovery software, it is worth spending time looking. I recovered a partition full of pictures that I was trying to resize, the operation failed when that stupid Trend Micro updated.....

---

### Post by absolutezero1287 on 2009-03-26
> **shateredsoul said:**
> Yeah, that's what I was thinking.  I killed it... 

hmm.. well I can always buy a new hdd and put it in the casing.

I'm using a program called diskdigger on windows, it recognized a 2000 gb drive... which is weird considering that computer only has 60 gbs.  It's in the process of scanning that drive now, hopefully it's the passport.

After that I'll try that program you suggested, is it for pc of ubuntu?

Spinrite is like a LiveCD made for recovering lost or corrupted data. It runs on an OS called FreeDOS. You can probably find it floating around somewhere. Of course downloading it from a torrent would be illegal *wink* even if that's the only place that you can find it *wink*.

---

### Post by shateredsoul on 2009-03-27
of course ;)

.. xp is still scanning the harddrive. It's going by very slowly, I'll post the outcome and the name of the program if it's successful or if any of the other programs work.

---

### Post by mal_conductor on 2009-03-29
testdisk and photorec work well.

Here is a solution to get around the random file naming (last section of my notes).
[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

