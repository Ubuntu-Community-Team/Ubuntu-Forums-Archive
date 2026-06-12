---
title: "GRUB Error 22 - But only when USB HDD is plugged in"
date: 2009-06-05
forum: General Help
---

### Post by Fleshtone on 2009-06-05
Hey Everybody, 

My system won't boot if I have either of my USB HDDs plugged in.  I have two Western Digital Mybooks.  I dual boot Windows XP sp3 and Jaunty, and I get ye olde GRUB Error 22 at startup.  If those drives are unplugged at startup, both OSs start fine and will recognize the USB drives once they are plugged in.

This GRUB error was initially a serious problem before I started troubleshooting and removed the external drives from the equation.  Then I realized I can unplug the drives, boot up, then plug them back in after GRUB does its thing.  Now it's more of a nuisance, but I'd still like to fix it.

Any ideas?

---

### Post by solidsnake204 on 2009-06-05
Is the internal drive higher then the Mybooks in the BIOS boot priority?

---

### Post by Fleshtone on 2009-06-05
Hmm...  I didn't realize that the BIOS boot order was at play while GRUB was installed.  I guess I don't understand their interconnection.  That could be an issue, but the MyBooks are certainly not higher in the order than the internal drives that carry XP and Jaunty.  Maybe I could remove them from the BIOS list altogether and see if the problem clears up.

---

### Post by Fleshtone on 2009-06-07
That was it.  I removed the USB drives from the Boot order and now the system starts fine with them plugged in.

Thanks!

---

