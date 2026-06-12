---
title: "Urgent computer dead please help"
date: 2009-04-23
forum: General Help
---

### Post by Fsmv on 2009-04-23
I had vista and ubuntu 8.1 dual booted with the grub boot loader. Then when I wanted to uninstall Ubuntu (don't hate me). What I did was I deleated all the partitions but the windows one and resized. Then when I turned on my computer it tried to run the grub boot loader and got an error. Now I can't get into windows. I still have all the files I just need to stop the computer from starting the boot loader that I deleated.

---

### Post by rhcm123 on 2009-04-23
that's bad - very bad
you see, you need to have some form of boot loader on the system, be it windows, grub, etc.

When you deleted ubuntu, you also deleted the config file that grub uses to list your operating sytems (it's stored in /boot).

The only real way to fix this now is to boot a windows cd (preferably xp) and use the recovery console to rewrite your MBR (it's one of the options on the list). This will install the windows boot loader and you should have no problems after that.

---

### Post by ActiveFrost on 2009-04-23
Insert your Windows CD ( or boot FDD ) & boot from it ( CD, FDD, HDD - boot sequence ).
```
fdisk /mbr
```

---

### Post by nandemonai on 2009-04-23
Every time you delete Ubuntu a penguin dies :(

Like the above poster said though, just use the windows disc to restore your MBR.

---

### Post by Fsmv on 2009-04-23
The only problem is vista came pre-installed. But I do have a disk for xp if that will work. If not will I have to buy a vista disk? Is there any onther way?

---

### Post by Alterax on 2009-04-23
Maybe Microsoft has a solution for this?

---

### Post by rhcm123 on 2009-04-23
> **Fsmv said:**
> The only problem is vista came pre-installed. But I do have a disk for xp if that will work. If not will I have to buy a vista disk? Is there any onther way?

yeah, the xp mbr should be able to boot vista. run the command the poster above said (hit r on the install screen to open up the recovery terminal), it should say somthing about a non-standard mbr, hit ok, let it run, then reboot and it *should* work.

Note: You should have reccived a recovery disk that should be capable of doing this with your computer

---

### Post by Fsmv on 2009-04-23
> **ActiveFrost said:**
> ( or boot FDD )
What do you mean by that? Does that mean there is a way I can do this without a disk because if it did come with a recovery disk I can't find it.

---

### Post by spillin_dylan on 2009-04-23
> **Fsmv said:**
> What do you mean by that? Does that mean there is a way I can do this without a disk because if it did come with a recovery disk I can't find it.

I think that the "Boot FDD" that ActiveFrost is talking about is probably a Floppy Boot Disk.  The old 3-1/4" ones.  Not very likely you have an XP or Vista version of one of those kicking around, though.

---

### Post by plucky on 2009-04-24
If you still have the problem,see this [link](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) for Vista recovery disc.


Good Luck

---

### Post by Fsmv on 2009-04-24
Thanks so much everyone. As it turns out on the XP disk that I had it had a "fixmbr" command and when I typed it in it literally took less than a second to execute and now my computer is fixed :D.

---

### Post by DenysT on 2009-04-25
> **rhcm123 said:**
> yeah, the xp mbr should be able to boot vista. run the command the poster above said (hit r on the install screen to open up the recovery terminal), it should say somthing about a non-standard mbr, hit ok, let it run, then reboot and it *should* work.

**Note: You should have reccived a recovery disk that should be capable of doing this with your computer**

Almost all PC manufacturers have stop shipping CD's with their systems, usually all they give you any more is a "recovery partition" that destroys all data when you use it. Most don't even give you the option of writing a recovery CD for Vista like some did for XP. And Vista doesn't fit on a CD thus it would take a DVD. (Although Microsoft will sell you a set of Vista CD's for a nominal fee. :P )

---

### Post by rhcm123 on 2009-04-25
> **DenysT said:**
>  (Although Microsoft will sell you a set of Vista CD's for a nominal fee. :P )

cheap windows? Must break moar than the expensive version :). Honestly, the most stable version of windows i ever used has to be 98SE. I still have my original jewel case for it.

@fsmv: No problem - that's what were here for :). Just out of curiosity though, why did you want to delete ubuntu?

---

