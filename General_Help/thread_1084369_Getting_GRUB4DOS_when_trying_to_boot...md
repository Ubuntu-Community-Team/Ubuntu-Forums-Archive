---
title: "Getting GRUB4DOS when trying to boot.."
date: 2009-03-02
forum: General Help
---

### Post by randy10 on 2009-03-02
I installed Ubuntu "within" Windows XP onto a separate physical hard drive, which has been working fine for a while now.

However now, when I choose Ubuntu from the GRUB menu, I am just given a grub4dos command line which I have no idea what to do with.  Why isn't Ubuntu booting anymore?

At this point reinstalling is out of the question, there are some very important files in the Ubuntu installation that I just can't lose right now, and despite the Ubuntu disk being NTFS, I can't actually see those files from XP.

Please, for the love of god, how can I fix this and boot into Ubuntu again?

---

### Post by randy10 on 2009-03-02
Well, thank goodness, all is well.

I have this problem in my Ubuntu install where the OS just.. freezes.  I can move the mouse around, but there's nothing I can do.  I have to hit the reset button.

I think this time something actually might have gotten messed up from hitting the button, but after running chkdsk /r in XP (Windows to the rescue of Linux?) it put a bunch of stuff (notably, root.disk) in the found.000 folder on the drive.  I had to make a "boot" folder inside the ubuntu folder and copy all of the things from found.000 into there, and it now works as it did before.

*wipes away sweat*

---

