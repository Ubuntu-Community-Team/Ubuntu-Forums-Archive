---
title: "Samba Broken, Can't Access Network or Printer"
date: 2008-12-14
forum: General Help
---

### Post by Unanimated on 2008-12-14
EDIT: I need my printer in two days, so I need to get this fixed!!

After I "installed" Samba to be able to share my Pictures folder, I was unable to access my networked drives and printers on my Windows computer. I've installed Samba 4 from the repos, to no avail. What's going on? I need my printer very soon for something very important, so this needs to get fixed.

---

### Post by Unanimated on 2008-12-16
bump

---

### Post by Unanimated on 2008-12-19
bump

---

### Post by albinootje on 2008-12-19
> **Unanimated said:**
> After I "installed" Samba to be able to share my Pictures folder, I was unable to access my networked drives and printers on my Windows computer. I've installed Samba 4 from the repos, to no avail. What's going on? I need my printer very soon for something very important, so this needs to get fixed.

Why don't you remove samba for the moment and see whether that helps you printing.

Later you should make sure that if your Windows computer needs to be server that your Linux-machine with samba doesn't win the "elections".
Afaik you can do that by putting this value low :

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
;   os level = 33

And not make it "master".

---

### Post by Unanimated on 2009-01-12
Well, I uninstalled Samba 4 and reinstalled Samba and all of the other crap that involves it. I have the printer set up again, but with the same exact results. The print process hangs on "Processing" and I can't see any of the shared files.

---

### Post by Unanimated on 2009-01-12
It could also be that we recently switched from a wired network to a wireless network, with the Windows computer managing the wireless.

---

### Post by Unanimated on 2009-01-28
bump

---

### Post by cariboo on 2009-01-28
IF you use the cups web interface to manage the printer, does that make any difference?

To access the cups web interface, open Firefox and in the address bar type:

[http://localhost:631](http://localhost:631)

You should be able to controll all sorts of settings from the web interface.

For you samba problems, I would suggest using this these two howto's

[Setup Samaba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

[Mount Samba shares with utf8 encoding using cifs]("http:///ubuntuforums.org/showthread.php?t=288534")

Jim

---

### Post by Unanimated on 2009-01-29
That fixed the problem of being unable to connect to the network, but I still can't get the printer. CUPS says "Unable to connect to CIFS host, will retry in 60 seconds..."

---

### Post by wbrokow1 on 2009-01-30
I get the same CIFS error. i'm running hardy.
If I find out how to fix it I'll post.

---

### Post by Unanimated on 2009-01-31
Okay.

---

