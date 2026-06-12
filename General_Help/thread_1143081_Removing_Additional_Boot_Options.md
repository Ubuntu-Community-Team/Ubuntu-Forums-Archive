---
title: "Removing Additional Boot Options"
date: 2009-04-29
forum: General Help
---

### Post by Chaaaaaaaalie on 2009-04-29
I installed Ubunto through Windows Vista, and encountered some problems with my graphics driver (I think I installed the wrong one). I solved this problem by un-installing Ubunto, and re-installing it again. It works great, however when I boot up, it gives me the option:
 
Windows
Ubuntu
Ubuntu
 
The original boot option was not removed when I un-installed it. Is there any way to remove this?

---

### Post by silbar on 2009-04-29
You can edit, as root (sudo gedit), /boot/grub/menu.lst

Save a backup copy for safety.

Dick Silbar

---

### Post by Chaaaaaaaalie on 2009-04-29
Wow! That was fast.  Thanks.
 
Please bear with me.  I am new to this.  I assume you mean to enter the command prompt under Ubuntu and type: (sudo gedit), /boot/grub/menu.lst
 
Or is this just a file I can open and edit through the program: sudo gedit
 
Forgive my ignorance.
 
Perhaps there is a tutorial you could point me to.

---

### Post by caljohnsmith on 2009-04-29
> **Chaaaaaaaalie said:**
> I installed Ubunto through Windows Vista
So did you install Ubuntu inside of Windows Vista with a Wubi install? In other words, do you have a C:\ubuntu directory in Vista? If so, the first boot menu that you get on start up is actually the Vista boot menu and not a Grub boot menu, and thus modifying /boot/grub/menu.lst in Ubuntu won't help. I think the easiest way to modify your Vista boot menu is with a program called "[EasyBCD]("http://neosmart.net/dl.php?id=1")". How about giving that a shot and let me know how it goes or if you run into problems.

---

### Post by Chaaaaaaaalie on 2009-04-29
That was it exactly.  Thanks, it worked great.  It wasn't difficult at all.  Just click "Add/Remove Entries" on the left panel.  Delete the extra"Ubuntus" and hit "Save".  
 
I actually uninstalled both Ubuntus already, and I'm going to start from scratch.  I'm not sure what would happen if I had one installed still, and I deleted the wrong entry.  I'm happy to know that I was able to get my original system back the way it was.

---

### Post by caljohnsmith on 2009-04-29
Glad to hear EasyBCD worked to remove the extra Ubuntu entries from your boot menu. Good luck with your fresh Ubuntu install. :)

John

---

