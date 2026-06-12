---
title: "Using Ubuntu With Windows xp"
date: 2006-03-02
forum: Desktop Environments
---

### Post by abhver on 2006-03-02
i am currently using windows xp and want to install Ubuntu ... the file system on XP is NTFS...will it be OK ? i mean is it fine? .... also will be able to excess and manipulate files from windows partations...

Pzl Reply
--
Abhishek

---

### Post by prizrak on 2006-03-02
You will need to repartition your drive to make some room for Ubuntu. NTFS is fine, the only thing is you will be able to read from your NTFS partitions but not write to them. This [http://www.fs-driver.org/](http://www.fs-driver.org/) will let you access your Linux partition from Windows tho.

---

### Post by ronmarley1 on 2006-03-02
Here's a link to a good How-To on dual booting Ubuntu and Wondoze XP.  Good luck!
[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

---

### Post by mechanic on 2006-03-02
[QUOTE=prizrak]NTFS is fine, the only thing is you will be able to read from your NTFS partitions but not write to them. [/QUOTE]
How come Knoppix users can write to NTFS partitions but Ubuntu users can't?

[http://news.bitdefender.com/NW58-en--LinuxDefender-Live-CD-launched-at-LinuxConf-2003.html](http://news.bitdefender.com/NW58-en--LinuxDefender-Live-CD-launched-at-LinuxConf-2003.html)
(doesn't recognise SATA disks though)

M.

---

### Post by Ramses de Norre on 2006-03-02
The newest kernels do have ntfs write support, I think it's included in dapper.

---

