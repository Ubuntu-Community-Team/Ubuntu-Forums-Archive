---
title: "seamlessrdp works, but it shows WIndows shell AND XP shell"
date: 2008-12-07
forum: General Help
---

### Post by Macmee on 2008-12-07
here's a screenshot:
[IMG]http://s4.tinypic.com/k3vcyq.jpg[/IMG]

It's fine for using applications but the start button isn't really functionable like this.

To start RDP I'm using this:
> rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.0.128:3389 -u "owner" -p ******
I get this back:
> Autoselected keyboard map en-us
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
WARNING: Broken Window Manager: doesn't handle restack (window was moved to bottom)
Fooo!
Fooo!
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
Fooo!


If anyone knows what's wrong, I would really appreciate knowing how to fix this:P. Thanks!

---

### Post by Macmee on 2008-12-08
bump

---

### Post by Macmee on 2008-12-09
Anyone?

---

### Post by Macmee on 2008-12-10
Bump :confused:

---

### Post by Macmee on 2008-12-10
bump

---

### Post by Macmee on 2008-12-11
bump :(

---

### Post by Macmee on 2008-12-12
bymp

---

### Post by ShockME on 2008-12-15
I think you need to be logged out fully before starting the seamlessrdp session. That's the trick that worked for me. Let me know if it helped.

---

### Post by drazen on 2010-06-01
> **ShockME said:**
> I think you need to be logged out fully before starting the seamlessrdp session. That's the trick that worked for me. Let me know if it helped.

I know it has been a while but I have found solution for your problem. You need to uninstall rdesktop provided by official ubuntu repository and install rdesktop from Debian repository
In my case I am using Ubuntu 9.10 and I uninstall package rdesktop-1.6.0-2ubuntu2 and install rdesktop_1.6.0-2_i386.deb package from this url:
[ftp://ftp.debian.org/debian/pool/main/r/rdesktop/](ftp://ftp.debian.org/debian/pool/main/r/rdesktop/)

---

### Post by paulmcq on 2010-10-13
@drazen: is that still true for Ubuntu Lucid 10.4?

---

