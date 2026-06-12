---
title: "Uninstalled Ubuntu (Wubi) but I still think I am missing disk space"
date: 2009-04-09
forum: General Help
---

### Post by GumpTron on 2009-04-09
Please delete this thread mod, thank you

---

### Post by balaknair on 2009-04-09
Wubi installs itself into a virtual drive image(located in the C:\Wubi folder on your drive). To remove Wubi completely from your drive, just delete this folder. Since your Vista partition is untouched by Wubi, the only way Wubi takes up space on your drive is the contents of this folder. Since you had issues uninstalling Wubi normally, this might still be present on your hard drive. If you have already restored your boot menu with Easy BCD you can safely delete this folder to get back all the space Wubi might have taken.

Your space is probably being eaten up by Vista itself, probably by means of temporary files and system restore points.

To free up more space, empty the recycle bin, clear the temporary files(C:\Windows\Temp , C:\Users\*your user name*\AppData\Local\Temp ) and temporary internet files folders(IE> Tools> Internet Options> delete Temporary Internet Files, FF> Tools> Clear Private Data> Clear Cache) which tend to build up over time. You can also run Disk Cleanup(My Computer> right click drive icon> Properties> Tools> Disk Cleanup) to regain some space.

Other ways that Vista takes up space- 
1) Hibernation- There will be a hidden file named hiberfil.sys if you have hibernation enabled on your system, that takes up the same space as the amount of RAM installed. To regain this space, turn off Hibernation(in power options).

2) Pagefile- The pagefile.sys file also takes up space on your hard drive for virtual memory. If you have more than 3GB RAM, you can turn off Virtual Memory to regain this space on your hard drive.

3) Prefetch- To increase system speed and improve loadup times, Vista caches commonly used apps in the folder C:\Windows\prefetch . Delete the contents to free up space.

4) Another way your hard drive space gets taken up is if you have System Restore enabled, since creation of restore points also take up more space over time(this is a known bug/feature with Vista where it sometimes sets no upper limit for system restore size). To correct the System Restore bug, you'll need to open a command prompt with admin privileges(no GUI way to do it AFAIK). See this guide on how to do it
[http://www.mydigitallife.info/2007/06/26/how-to-change-and-limit-system-restore-storage-space-usage-size-in-vista-with-vssadmin/](http://www.mydigitallife.info/2007/06/26/how-to-change-and-limit-system-restore-storage-space-usage-size-in-vista-with-vssadmin/)

Hope this is helpful.
All the best.

---

