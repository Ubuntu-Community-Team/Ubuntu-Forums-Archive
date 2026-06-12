---
title: "Share printer"
date: 2005-06-12
forum: Desktop Environments
---

### Post by BerryB on 2005-06-12
Hello,

I've installed plain Ubuntu (server option) with Xorg and XFce4 for graphic stuff (so no gnome apps). Now I want to use the shared printer (sits on my WinXP computer). So I installed CUPS, with the GNOME-CUPS-MANAGER (which I installed) I added the printer, I editted my smb.conf according to a website, but still I can't print! Of course the printer is shared. Here's my smb.conf

```
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   guest ok = yes
   printer admin = root, @Berry

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```

(only the printing part...)

---

### Post by clb137 on 2005-06-12
Hi,

Have a look at your file 'printers.conf'  In /etc/cups

In there you will see a line as shown below

DeviceURI smb://yournetwork/yourxpbox/yourprinter

change it to read the following

DeviceURI smb://guest@yournetwork/yourxpbox/yourprinter

Restart 

should work a treat


good luck 

clinton bennett

---

### Post by BerryB on 2005-06-12
is it just the word guest, or is it my username?

---

### Post by RastaMahata on 2005-06-12
admins, please move this :(

---

### Post by BerryB on 2005-06-13
ok, sorry for placing this in the wrong forum part...

---

### Post by clb137 on 2005-06-13
[QUOTE=BerryB]is it just the word guest, or is it my username?[/QUOTE]


Hi,

Use the word 'guest'


clinton

---

