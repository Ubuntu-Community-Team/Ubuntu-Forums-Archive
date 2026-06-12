---
title: "Impossible to remove 'filename': I/O Error"
date: 2009-04-12
forum: Desktop Environments
---

### Post by cristian.palmas on 2009-04-12
Hi,

I have Kubuntu 8.10 with Plasma desktop and I have a problem with my external hard disk (NTFS partition).

A file was badly written and I want to get rid of it.
I tried both "rm" and "shred" but it didn't work. The message is always the same: "Impossible to remove 'filename': I/O Error". So I cannot remove it.

This is a real problem because, when the system reads the sector of that unremovable file, it hangs forever and I have to reboot.
So my question are:

1. How can I get rid of that file?
2. If it is a problem about a damaged sector, which commands I have to use to check the integrity of the NTFS partition of the external HD?

Thanks in advance.

Cristian Palmas

---

### Post by coffeecat on 2009-04-12
You are far better off checking the integrity of a NTFS filesystem with Windows. It is a Microsoft filesystem. For instance, from man ntfsfix:

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.So even a Linux utility is telling you to use chksdk in Windows, which can repair the filesystem and remap bad sectors. Do you have access to a Windows machine? Here are a couple of links for you:

chkdsk in XP: [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)
chkdsk in Vista: [http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html](http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html)

Then it would probably be better to delete the damaged file in Windows.

---

### Post by cristian.palmas on 2009-04-13
> **coffeecat said:**
> You are far better off checking the integrity of a NTFS filesystem with Windows. It is a Microsoft filesystem. For instance, from man ntfsfix:

So even a Linux utility is telling you to use chksdk in Windows, which can repair the filesystem and remap bad sectors. Do you have access to a Windows machine? Here are a couple of links for you:

chkdsk in XP: [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)
chkdsk in Vista: [http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html](http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html)

Then it would probably be better to delete the damaged file in Windows.

Hi,

thanks for the response.
I've access on a Windows XP machine now but my laptop has only Kubuntu 8.10 installed.

I will try on my sister's pc.

---

