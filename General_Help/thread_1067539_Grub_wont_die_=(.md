---
title: "Grub wont die =("
date: 2009-02-12
forum: General Help
---

### Post by oopsie on 2009-02-12
I've been using Ubuntu for the past week. It's been fun, but there's too many things it can't do that I need. So I'm trying to install my old windows 2000

I booted from my windows2000 disk. Went through the installation procedure. And it said "Windows will now reboot and continue installing after the reboot" or something along those lines.

So, it reboots. And grub comes up. And Ubuntu loads :confused:


Okay, I boot from my windows2000 disk again. I format my C and D drives (Not my E drive with my backups), and again I install windows. It says it will continue installing after a reboot. It reboots. And Grub comes up again! Only, ubuntu isn't there now I formatted, so it does nothing.


So, how on earth am I supposed to be able to install my windows2k again? When Grub keeps coming back.

I'm posting this using the Ubuntu live disk.

Could somebody please help, or give me some advice?:confused:

---

### Post by k3rnelmustard on 2009-02-12
While your booting up your windows disk, hit R to go to the recovery console.  (I'm assuming w2k has this, I actually don't know).  When you get there type 'fix mbr' or maybe its 'fixmbr' one of the two.  It will say master boot record fixed, and that means it will have overwritten grub.

---

### Post by adult swim on 2009-02-12
with your windows 2000 cd, boot it like you are going to install but dont install.  look for an option that says someting like recovery console, or dos prompt.  whenever you get there, enter in the commands ```
fixboot

fixmbr

quit
``` and that should take care of grub.

---

### Post by oopsie on 2009-02-12
Thanks you two. I'll try that. :)

---

