---
title: "Win XP Pro CD Won't Boot - Black Screen"
date: 2009-03-09
forum: General Help
---

### Post by engellion on 2009-03-09
I have Win XP installed on the primary partition, formated into 2 logical drives, and 
Ubuntu installed (after I installed XP) on another partion.

Ubuntu installed Grub as the boot loader and every thing has worked fine (have been booting into either Linux or XP no problems) until recently.

I now need to reload WinXP as a last resort (XP Won't Load from Grub Menu - I get the splash screen for XP coming up, but then it never gets to the login screen, just reboots itself and I get back to the Grub Loader.)    

So, I make sure the bios is set to boot from a CD first, then load my Win XP ProCD.  However, after the message "Press any key to boot from CD", I press a key and then I see for a fraction of a second the message "Setup is inspecting your computer hardware configuration", and after then, a black screen.  

The black screen just waits there indefinately.

I know the XP CD boots on another system. So what is going on here?

This seems to be a known problem (via google), but not a clear solution. I've googled possible solutions, but not really sure what to do.  Some suggest XP gets confused with too many unknown partitions and just hangs.  

Please help me.:(

Thanks in advance.

---

### Post by dusan.saiko on 2009-03-16
I never had simillar problem and actually I think it shouldn ot be caused by unknown linux partitions.

If XP was booting fine at your isntallation and sudenly stopped, then something had to change.

If you have not made any modifications to partition layout, then there are several possibilities to try:
- if XP boots into Safe Mode, then there is something wrong may be with a new XP driver
- I would also scan the pc with antivir (I use Trinity Rescue kit CD for this)
- try to boot into memory test and leave it running over night to see if RAM is OK
- test the hardware in some other way to see if everything works (may be video card problem ?)

---

