---
title: "XP dual boot problem"
date: 2006-01-06
forum: General Help
---

### Post by HokeyFry on 2006-01-06
When I choose to boot into windows XP from GRUB, it says that the filesystem is unknown. I have no XP boot disk, as the computer did not come with one, so I can't simply re-install XP. How do I fix this?

---

### Post by h4ck3r on 2006-01-06
[QUOTE=HokeyFry]When I choose to boot into windows XP from GRUB, it says that the filesystem is unknown. I have no XP boot disk, as the computer did not come with one, so I can't simply re-install XP. How do I fix this?[/QUOTE]
I am pretty sure that I had some sort of problem you had and what I did was I left my xp cd in the drive. So, I think you should download or buy an xp cd just for booting purposes. Although I don't want to do that it will be my last resort. (I have windows just for games ;) )

Good luck
Ben

---

### Post by HokeyFry on 2006-01-06
well, I do not want to purchase anything or illegally download anything. I COULD obtain a cd for bootup from a friend, but I would have to wait a couple weeks and I need a way to fix this in the next couple of hours, or I'm in deep crap.

---

### Post by hillbilly on 2006-01-06
How did this problem crop up ? Was this the first time you are loggin into xp after installing ubuntu ? Did you modify the grub config file ?

---

### Post by HokeyFry on 2006-01-06
no i have had ubuntu installed for a while. This is the first problem i have had like this. Although after looking into my BIOS, i enabled a couple of screens to show on startup ans I found a windows recovery utility. I am running it and hopefully it will solve my problem, although I could still use help in case it doesn't work.

Actually it is a system recovery, not a windows recovery.

It didn't work. Thanks for all the help so far, and thanks in advance for any help that I recieve.

---

### Post by HokeyFry on 2006-01-06
ok, I have figured out the problem. GRUB will not recognize the NTFS file system, even though in ubuntu I can mount and view my windows partition just fine. Anyone know how to fix this?

---

### Post by Tuntis on 2006-01-06
[QUOTE=HokeyFry]ok, I have figured out the problem. GRUB will not recognize the NTFS file system, even though in ubuntu I can mount and view my windows partition just fine. Anyone know how to fix this?[/QUOTE]
I'm an total newbie at these but have you "chainloaded"?

---

### Post by HokeyFry on 2006-01-06
Although I recognize the term, I do not know what chainloading is. I do know, however, that when I try to boot into XP, it says "chainloader +1", or something like that. I don't know what it means though.

---

### Post by cetol on 2006-01-06
Check your /boot/grub/menu.lst

Under other operating systems look for the windows xp entry. It should have an entry that says "chainloader +1"

If it does and you still cant boot Im lost in grub. I would have to fix the mbr with any windows boot disk floppy that has fdisk. Code:

A:\fdisk /mbr

This will rewrite the mbr allowing windows to boot but linux will then be fubar.

---

### Post by cetol on 2006-01-06
See the thread "menu.lst" in this forum. I think the answer you need is there.

---

### Post by HokeyFry on 2006-01-06
Yeah, I thought of using a diskette to boot up windows (have DOZENS) but this comp has no diskette drive.

I re-installed ubuntu so that GRUB would re-install, but the same thing is happening. After I setup my wireless connection, I will check out the tread you recommended, cetol. Thanks for all the help!

---

### Post by HokeyFry on 2006-01-06
The thread "menu.lst" does not contain what I am looking for. It looks like the guy's issue there is with a bad partition. My issue is that GRUB won't recognize the NTFS file system. It does recognize FAT, but not NTFS.

---

### Post by cetol on 2006-01-06
[QUOTE=HokeyFry]Yeah, I thought of using a diskette to boot up windows (have DOZENS) but this comp has no diskette drive.

Google "ultimate boot disk". Download an image and burn it to cd! Boot from cd

---

