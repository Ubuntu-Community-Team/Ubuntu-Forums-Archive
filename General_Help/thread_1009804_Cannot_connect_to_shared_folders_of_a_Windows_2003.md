---
title: "Cannot connect to shared folders of a Windows 2003 Server"
date: 2008-12-13
forum: General Help
---

### Post by Martin Lam on 2008-12-13
Hi!

I am using Ubuntu 8.10 desktop.  There are 3 Windows servers on my network, 2 x Win2000, and a Win2003.  

I could connect to the shared folders for both Win2000 servers, but not for Win2003.  

Any one had success on accessing Win2003 shared folders?  Is there anything special for Win2003?  

Best regards,
Martin Lam

---

### Post by iaculallad on 2008-12-13
Nothing special at all, the steps in connecting to your (2) M$ Server 2K should be the same with the 2003 version. Just be sure that the folder you're trying to access on the 2003 machine is "shared" and access it via Ubuntu's nautilus window by: smb://xxx.xxx.xxx.xxx, the private IP of your server.

This would prompt you for username, domain, and password. Try inputing your windoze administrative account.

*Same step is applied when accessing shared folders on xp machines.

---

### Post by Martin Lam on 2008-12-14
Hi Iaculallad, 

Thanks!  After making sure Ubuntu is accesable to Win2003, I did further tests and found out the difference was that:

- For Win2K server, when I clicked on the computer name, it will list the available shared folders.

- For Win2003 server, when I did the same, it would not show anything.  I needed to hardcode a folder name on the address bar to get connected.

Thanks again.  

Martin Lam

---

### Post by jimmah6786 on 2009-01-15
> **Martin Lam said:**
> Hi Iaculallad, 

Thanks!  After making sure Ubuntu is accesable to Win2003, I did further tests and found out the difference was that:

- For Win2K server, when I clicked on the computer name, it will list the available shared folders.

- For Win2003 server, when I did the same, it would not show anything.  I needed to hardcode a share name on the address bar to get connected.

Thanks again.  

Martin Lam

Is there any way to have the shares auto enumerate in Ubuntu when typing in only the hostname of the server?

---

