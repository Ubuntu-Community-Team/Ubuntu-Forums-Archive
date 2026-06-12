---
title: "Printer sharing between 2 ubuntus"
date: 2011-01-21
forum: Desktop Environments
---

### Post by dargaud on 2011-01-21
Hello all,
I know how to share a printer between Windows and Ubuntu, and the opposite, but I don't know how to do it without Samba/CIFS... On the print server I have selected "Share printers connected to this system", "Allow printing from the Internet" and "Allow users to cancel any job" in CUPS, but in the CUPS of the client I cannot figure out how to install a remote printer. 

I tried several of the "Add printer" CUPS methods, like specifying "http://server:631/ipp", but the print jobs just hang. Isn't there a way to autodetect the printer remotely ?

---

### Post by Morbius1 on 2011-01-21
Don't know you how you this on KDE but somewhere in KDE's cups utility try this type of syntax:

```
ipp://server:631/printers/Linux-Printer-Name
```Or better yet replace the "server" host name with it's ip address:
```
ipp://192.168.0.100:631/printers/Linux-Printer-Name
```

---

### Post by dargaud on 2011-01-22
I got "undefined protocol" when I tried, but then after playing with the "add printer' options of CUPS I managed to find a way to add the remote printer. But that was the least intuitive and most randomly meaningless thing I've seen in a long time.

---

