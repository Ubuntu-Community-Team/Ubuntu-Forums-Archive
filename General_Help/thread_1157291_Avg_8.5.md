---
title: "Avg 8.5"
date: 2009-05-12
forum: General Help
---

### Post by iswear on 2009-05-12
I installed AVG yesterday and saw it didnt have a GUI, and havent been able to figure out how to use it. 

If anyone could help i would appreciate it.

---

### Post by DeMus on 2009-05-12
> **iswear said:**
> I installed AVG yesterday and saw it didnt have a GUI, and havent been able to figure out how to use it. 

If anyone could help i would appreciate it.

Why you installed it? Did you install it in Ubuntu? To do what? Scan for Windows viruses on Windows disks?
There is absolutely no need to install a virus scanner in Linux. Even when there are viruses they can do no harm since they need root access to destroy important system files. You use your computer as a "simple" user with limited rights. So even you can not destroy system files.
You better uninstall it and safe your CPU power for really important work.

---

### Post by geirha on 2009-05-12
[https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)

---

### Post by DeMus on 2009-05-12
> **geirha said:**
> [https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)

Okay, there seems to be a Linux version. The question remains: what ever fore?

---

### Post by iswear on 2009-05-12
Yea im trying to scan a windows disk. lol my sister got a trojan on it.

---

### Post by hyperdude111 on 2009-05-12
You really don't need a Linux anti-virus. The only reason this exists is to protect windows computers from windows viruses that are on your system but will have no effect on ubuntu.

If you are only using a ubuntu machine you will NOT need an anti-virus, and even if you are using windows as well the chances of any damage being done are minuscule at best.

---

### Post by DeMus on 2009-05-12
> **iswear said:**
> Yea im trying to scan a windows disk. lol my sister got a trojan on it.

Okay, but I wonder if AVG is the best solution for it, since:

```
AVG Free is a version of the AVG antivirus which is free for private and non-commercial use.

It can only detect viruses; it **cannot** remove them from files. 
```

So, at the end you may know in which file the trojan is hiding but you can not change it, other than to throw away that file with all consequences.

---

### Post by geirha on 2009-05-12
Mainly for web-, file- and mail-servers I believe. If you have a web server where people can upload files for instance, you'll want to check them for viruses. Windows users that download them may get infected.

---

### Post by iswear on 2009-05-12
Thank you for your help.
Is there a better anti-virus program for linux then?

---

### Post by lovinglinux on 2009-05-12
> **iswear said:**
> Thank you for your help.
Is there a better anti-virus program for linux then?

Bitdefender. Works like a charm here, have a nice interface, a drop box and nautilus integration.

[http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html)

Click the download link, then fill the form, then get the real download link from your e-mail then go back to the previous page and click the button to request a license.

---

### Post by altonbr on 2009-05-27
Guys, you're not answering his question. He downloaded AVG Free 8.5 and it doesn't seem to have a link in the Applications menu. I remember using 7.5 and it had one, but I just downloaded 8.5 and can confirm there is no link in the Applications menu.

Here are the executable of the package according to the man pages and Synaptic:
> avgd
avgscand
avgsched
avgspamd
avgcfgctl
avgctl
avgoad
avgupd
avgupdate
avgavid
avgdump
avgscan
avgtcpd

I guess they took out the gui and made it cli only. If that's the case, you'd have to run something like:

```
avgscan / -x /mnt
```
which will scan your entire Ubuntu hard drive (so if you want to scan /media/disk, change it to that) but exclude /mnt

Hope that helps!

---

### Post by gkiteguy on 2009-06-09
> **altonbr said:**
> Guys, you're not answering his question. He downloaded AVG Free 8.5 and it doesn't seem to have a link in the Applications menu. I remember using 7.5 and it had one, but I just downloaded 8.5 and can confirm there is no link in the Applications menu.

Here are the executable of the package according to the man pages and Synaptic:


I guess they took out the gui and made it cli only. If that's the case, you'd have to run something like:

```
avgscan / -x /mnt
```
which will scan your entire Ubuntu hard drive (so if you want to scan /media/disk, change it to that) but exclude /mnt

Hope that helps!

Thanks, I am not the poster but had exactly the same problem.  The package installed the following
/opt/avg/avg8/bin/avgavid
/opt/avg/avg8/bin/avgcfgctl
/opt/avg/avg8/bin/avgctl
/opt/avg/avg8/bin/avgd
/opt/avg/avg8/bin/avgdump
/opt/avg/avg8/bin/avgoad
/opt/avg/avg8/bin/avgscan
/opt/avg/avg8/bin/avgscand
/opt/avg/avg8/bin/avgsched
/opt/avg/avg8/bin/avgspamd
/opt/avg/avg8/bin/avgtcpd
/opt/avg/avg8/bin/avgupd
/opt/avg/avg8/bin/avgupdate
/opt/avg/avg8/bin/avgwrapper.sh


None appeared to execute, but I used your command and got 
bash: syntax error near unexpected token `c'

I had planned to scan my wife's Windows Partitions. 

Thanks, 

Gkiteguy):P

---

