---
title: "gdm doesn't start"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Michman_ on 2006-09-15
Hi.
I didn't change anything at the system, but since today gdm doesn't start. It shows me the following error-message:
> Als Server-Authentifizierungsverzeichnis (daemon/ServAuth/Dir) wurde "/var/lib/gdm" festgelegt, dies ist jedoch kein Verzeichnis. Bitte korrigieren Sie die GDM-Konfiguration und starten sie GDM neu.
In english that means something like:
> As server-authdirectory (daemon/ServAuth/Dir) “/var/lib/gdm” was specified, however this is no directory. Please correct the GDM configuration and start again GDM.

I tried to do a ```
sudo dpkg-reconfigure gdm
```
But it shows me the message:
> dpkg-query: Couldn't open "var/lib/dpkg/status" : Not a directory

What can I do?

Thanks ;)

---

### Post by ayoli on 2006-09-15
does your /var/lib (even /var) dir still exist ? or have permissions on it changed ?

---

### Post by wkulecz on 2006-09-15
I had the same happen to me.  I tried everything I could think of, apt-get remove and reinstall after deleting their directories gdm, xserver, then install kde.  Nothing worked.

I had set up two nearly identical systems, the second got bit by the defective kernel update that broke the nvidia-glx driver, after I fixed it I cloned the broken system from the working one with Norton's Ghost 2003.


If there is a fix I'd like to know in case it happens again, but you may end up having to re-install.  IF you've anything you need to save you should be able to copy it to a USB memory stick if you boot the LiveCD or Knoppix before you re-install.  Total mystery as to why the system cratered, shut it down, moved it to the lab it was to live in, and it wouldn't boot :(

Good luck!
--wally.

---

