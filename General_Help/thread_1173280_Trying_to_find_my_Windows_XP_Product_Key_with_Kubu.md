---
title: "Trying to find my Windows XP Product Key with Kubuntu?"
date: 2009-05-29
forum: General Help
---

### Post by dragonknight42069 on 2009-05-29
Hey,

So I used Partition Magic the other day and it destroyed my main partition with an error. Luckily, I had Kubuntu installed (I usually use Kubuntu, but I use Windows for gaming).

I can't seem to find my Product Key which amazes me, but I'm going to need to grab it from my old Windows OS. I can access the files and its registry, I just need to figure out how to do this.

Since I'm using XP, it won't show my product key via find product key in the registry. (I'm just typing regedit into the terminal and it's working)

I've tried using Magical Jelly Bean with wine, but I can't load my windows registry with it. I found this topic talking about it [http://www.mjbforum.com/forum/viewtopic.php?t=133](http://www.mjbforum.com/forum/viewtopic.php?t=133) but I couldn't figure out the dumping process (Or where it even went!)

I really do not mind reinstalling Windows XP so all I need is that product key number. Although I have tried using system recovery tools with Linux, I'm probably too much of a 'noob' to properly get them to work.

Can anybody help me? Whether it's recovering my old windows xp data with a system recovery tool made for Linux or finding out my old product key.

Thanks! :KS

---

### Post by mister_p_1998 on 2009-05-29
Ive used a program called keyfinder many times in the past, try googling that..
Steve

---

### Post by dragonknight42069 on 2009-05-29
> **mister_p_1998 said:**
> Ive used a program called keyfinder many times in the past, try googling that..
Steve

Thanks for the reply

That keyfinder is Magical Jelly Bean however
Do you know how to get it to work with wine? I need to load the hive, and loading the direct windows XP dir doesn't seem to work

---

### Post by dragonknight42069 on 2009-05-29
Nobody knows how to do this?

After I typed in:

dumphive /Root/host/WINDOWS/system32/config/software ~/software.reg HKEY_LOCAL_MACHINE

Where is that new software.reg file at?

---

### Post by HavocXphere on 2009-05-29
This is going to be a bit of a mission...

I believe the key you need is in:

\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion -> LicenseInfo

Use the windows recovery console to dump that key somewhere (in the form of a .reg file). Just google for the exact command. Then fire up a Virtual box with a working windows. Edit out the other part of, leaving only the LicenseInfo item. Import it onto the VM'd OS and use some key extractor like Jelly to get the key. The VM thing is needed because the key is stored in an encrypted form.

Alternatively, you could try to repair the broken install & *hope* that it is good enough to get into safemode.

---

### Post by irv on 2009-05-29
If you bought the PC with the Windows OS loaded then it should have a tag on the bottom/back with the product code. If you registered it then MS should get it to you if you call them. If you have the CD it should be on there also.
One more thing, does it have a hidden partition on it with Windows files for reinstall. If you have the CD or can get one, you might be able to roll back to a good copy of the OS from a past date.

---

