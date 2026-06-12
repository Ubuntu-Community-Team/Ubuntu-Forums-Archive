---
title: "CUPS is driving me insane!"
date: 2009-01-01
forum: General Help
---

### Post by hyperyoda on 2009-01-01
Ugh why won't CUPS cooperate :-( I tried everything on the other thread:
[http://ubuntuforums.org/showthread.php?p=6465629](http://ubuntuforums.org/showthread.php?p=6465629)

Additionally I tried anything I could find on google and I have exhausted every solution I could find :( As a last resort I tried running lpadmin to set the printer manually and I get that stupid ambiguous error message again, same one I got in the cups web interface. Does anyone know what this error message means and how  I can get my printer (HP Deskjet 960C hooked up to parallel port) setup using lpadmin:

ubuntu@ubuntu:~$ sudo lpadmin -h localhost -p HP -D printer -u allow:ubuntu -P /rofs/usr/share/cups/model/hpijs/HP/HP-DeskJet_960C-hpijs.ppd
lpadmin: Request Entity Too Large

Zach

---

### Post by linux_tech on 2009-01-01
what is output of-
```
ls -ld /var /var/spool /var/spool/cups /var/spool/cups/tmp
```

---

### Post by hyperyoda on 2009-01-01
> **linux_tech said:**
> what is output of-
```
ls -ld /var /var/spool /var/spool/cups /var/spool/cups/tmp
```

```

ubuntu@ubuntu:~$ sudo ls -ld /var /var/spool /var/spool/cups /var/spool/cups/tmpdrwxr-xr-x 10 root   root 160 2009-01-01 02:35 /var
drwxr-xr-x  6 root   root  80 2009-01-01 02:30 /var/spool
drwx--x---  5 cupsys lp    60 2008-12-31 18:09 /var/spool/cups
drwxrwx--T  4 cupsys lp    40 2006-05-17 08:46 /var/spool/cups/tmp
ubuntu@ubuntu:~$
```

---

### Post by hyperyoda on 2009-01-02
> **linux_tech said:**
> what is output of-
```
ls -ld /var /var/spool /var/spool/cups /var/spool/cups/tmp
```

Hello you still here? I posted the output, did you see it?

Zach

---

### Post by donkyhotay on 2009-01-02
According to this:
[http://www.laen.org/2005/11/15/cups-request-entity-too-large/](http://www.laen.org/2005/11/15/cups-request-entity-too-large/)
this error can mean a permissions error. Per your previous post the owner is cupsys while the group is lp. Is your user a member of the lp group? Although (potentially) dangerous have you tried printing as root? Doing that will at least confirm/deny if this is a permissions problem or something else. I would recommend checking your user groups first though.

---

### Post by hyperyoda on 2009-01-03
> **donkyhotay said:**
> According to this:
[http://www.laen.org/2005/11/15/cups-request-entity-too-large/](http://www.laen.org/2005/11/15/cups-request-entity-too-large/)
this error can mean a permissions error. Per your previous post the owner is cupsys while the group is lp. Is your user a member of the lp group? Although (potentially) dangerous have you tried printing as root? Doing that will at least confirm/deny if this is a permissions problem or something else. I would recommend checking your user groups first though.

I checked and cupsys is a member of group lp.

I now have:

drwx--x--- 5 root lp 60 2008-12-31 18:09 /var/spool/cups
drwxrwx--T 4 root lp 40 2006-05-17 08:46 /var/spool/cups/tmp

However it seems since cupsys is no longer the owner of the directories it will not load the printing database when gnome-cups-manager tries to read it. And I tried even running lpadmin as root but I get that same stupid "Request entity is too large" error message that is torturing me lol. Seems cups runs on Ubuntu as user cupsys.

I also tried running gnome-cups-manager and lpadmin with these permissions:

drwx--x--- 5 cupsys lp 60 2008-12-31 18:09 /var/spool/cups
drwxrwx--T 4 cupsys lp 40 2006-05-17 08:46 /var/spool/cups/tmp

But I get the same errors. This is sure vexing.

Zach

---

### Post by exploder on 2009-01-03
Updates for cups released today. Maybe the updates will resolve the problems you are having.

---

### Post by hyperyoda on 2009-01-03
> **exploder said:**
> Updates for cups released today. Maybe the updates will resolve the problems you are having.

Thanks will try that.

Zach

---

