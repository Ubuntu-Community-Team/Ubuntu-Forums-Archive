---
title: "Copying Bookmarks / System instability"
date: 2009-10-31
forum: Desktop Environments
---

### Post by StephenOK on 2009-10-31
Hi Folks,

Sorry if there is some redundancy in this post, as I've searched for similar and was a bit unclear about the solutions provided.
Here is my issue:

1-Because I can't find a bookmarks folder to backup their bookmarks, I've been doing it manually under the firefox bookmarks menu, which is a bit tedious. Is there a more expedient way?

2- I have a client that I got to move to Ubuntu after having nothing but constant problems with Windows based OS. Everything was fine for some time until the computer began to act in a bizarre manner: it would freeze, report system crash, take forever for pages to load, etc.

After a hardware check, everything seemed to be alright. Then they explained - after a good hour of trouble-shooting - that they encountered a host of viruses while surfing the web. Here is what I came up with from a report they gathered earlier:

**My Computer**
System Folder
System Folders
Shared Documents

My Documents
Viruses Found
Hard Drive
Hard Drive (C:)

Security
Windows Security
Security is affected by virus
100%
Checking: c:\windows\wuauclt1.exe
Your computer is infected
Name                         Type             Threat level
W32/Benjamin.Worm            Virus                High
Trojan Horse       
IRC/Backdoor.SdBot4.FRV      Virus               Medium
Adware.Win32.Winad           Virus               Critical
Trojan.Fakealert.355[        Virus               Medium
W95/Elkern F-Secure          Virus                High
Recommend: Click "Start Protection" button to erase all threats.

This report was generated from the Windows Enterprise Defender - Online Protection [http://fastzone-guard.net/?p=WKmimHVIcW6Hjsbl](http://fastzone-guard.net/?p=WKmimHVIcW6Hjsbl)...

Ok, given, I told them that they just encountered a phishing site that assumed they were using a Windows OS, as none of these "viruses" would affect a Linux based OS.

However, it is curious to note that the bizarre behavior mentioned earlier in the post began to happen right after this incident.

I've also noticed that the processor - this is a dell dimension 8200 - is running at 97-100% under system monitor with no apps running in the background.

Anyone have any clues as to what's going on here?

Much thanks for any assistance.

Best,

Stephen

---

### Post by Bucky Ball on 2009-10-31
Go 'Bookmarks->Organise Bookmarks' and choose 'Import and Backup'.

---

### Post by StephenOK on 2009-10-31
> **Bucky Ball said:**
> Go 'Bookmarks->Organise Bookmarks' and choose 'Import and Backup'.



Thanks, Bucky Ball. Worked like a charm. As for the system instability, I just backed everything up and I'm reinstalling the OS. Hope that solves the issue(s).

Thanks again

---

### Post by Bucky Ball on 2009-11-01
Good news for part 1. As for part 2, if a re-install doesn't work ...

> **StephenOK said:**
> Hi Folks,

2- I have a client that I got to move to Ubuntu after having nothing but constant problems with Windows based OS. Everything was fine for some time until the computer began to act in a bizarre manner: it would freeze, report system crash, take forever for pages to load, etc.



This does sound like RAM but these things can be enigmatic. I would definitely say hardware. Not all hardware checking software is 100% accurate.

The CPU usage in system monitor seems to indicate something fishy also. Look at it like this; if the OS, the application and the machine are purring along fine then suddenly a freeze, it is unlikely the software has suddenly 'broken' mid-stream. This would point to hardware. 

If the machine has more than one stick of RAM I would try one stick in slot one. Number it stick1. If that works, check the next stick in slot one (as you know the slot is working). Number that stick2. Etc ...

If stick1 doesn't work in slot1 try it in slot2. If that doesn't work, slot3 etc. If it doesn't work in any slot you have a dead stick (unlikely 4 dead slots!).

Sometimes it is one of the sticks, sometimes, though rarer, it is one of the slots. This will not always be picked up with a 'virtual' hardware check. RAM problems can be intermittent and hard to catch. Physically testing is the sure-fire way.

---

