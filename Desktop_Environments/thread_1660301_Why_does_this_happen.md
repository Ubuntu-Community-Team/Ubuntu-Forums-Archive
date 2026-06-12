---
title: "Why does this happen?"
date: 2011-01-05
forum: Desktop Environments
---

### Post by throese on 2011-01-05
So, I deleted my Ubuntu partion and let my Windows partition take up the whole hard drive, but when you delete the Ubuntu partition, it takes away the grub boot menu and I get stuck with the Grub Rescue > _ prompt...why does this always happen when you remove the Ubuntu part of the hard drive and let Windows have the whole hard drive back? It doesn't make sense, because now I have to re-isntall Windows and all of my programs (gonna Virtual Box it)

---

### Post by howefield on 2011-01-05
Why do you have to reinstall Windows ?

Just fix the Windows boot loader.

---

### Post by Rubi1200 on 2011-01-05
> **howefield said:**
> Why do you have to reinstall Windows ?

Just fix the Windows boot loader.
+1 

There is absolutely no need to reinstall Windows.

How to restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ajgreeny on 2011-01-05
> It doesn't make sense, because now I have to re-isntall Windows and all of my programs (gonna Virtual Box it)

I makes total sense actually.  All the configuration files for grub were on the Ubuntu partition.  Now you have removed that partition, there are no configuration files for grub to use, hence the error.

As others have said, just restore the windows bootloader to the MBR and you're back in business.  If you don't have a windows install CD to use have a look at [http://neosmart.net/](http://neosmart.net/) where you can find ways to restore the windows bootloader.

---

### Post by throese on 2011-01-05
Oh, well, I just decided to install Ubuntu entirely onto my hard drive again. Going to run Windows 7 from Virtual Box.

---

