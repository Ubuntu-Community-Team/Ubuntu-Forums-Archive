---
title: "chroot to test desktop environments?"
date: 2014-10-14
forum: Desktop Environments
---

### Post by vasa1 on 2014-10-14
I don't know anything about chroot but after reading a quotation provided by mc4man over [here]("http://ubuntuforums.org/showthread.php?t=2248240&p=13143142#post13143142") about crouton I want to know if it's possible to test other environments (say kubuntu-desktop, LXQt, whatever) without "contaminating" the original OS:> Like virtualization, chroots provide the guest OS with their own, segregated file system to run in, allowing applications to run in a different binary environment from the host OS. Unlike virtualization, you are not booting a second OS; instead, the guest OS is running using the Chromium OS system. The benefit to this is that there is zero speed penalty since everything is run natively, and you aren't wasting RAM to boot two OSes at the same time. The downside is that you must be running the correct chroot for your hardware, the software must be compatible with Chromium OS's kernel, and machine resources are inextricably tied between the host Chromium OS and the guest OS.

---

### Post by TheFu on 2014-10-14
I normally just create a new user for each DE and test that way.  Only the login screen seems to be screwed between the different DEs. Everything else is under the individual HOMEs.

When I'm done, **aptitude purge** removes the desktop/DE I don't like.

I've seen the chroot on chromium too and I've used chroot for various other needs, just don't see the need for my testing.  

Take good notes, I'm sure others will appreciate it.

---

### Post by Tadaen_Sylvermane on 2014-10-14
> **TheFu said:**
> I normally just create a new user for each DE and test that way.  Only the login screen seems to be screwed between the different DEs. Everything else is under the individual HOMEs..

I cannot count the number of times I have re-installed my system because I'm a clean freak and don't like useless stuff filling up my /home... May be obvious but I never even considered this before. +1 if I could.

---

### Post by TheFu on 2014-10-15
> **Tadaen_Sylvermane said:**
> I cannot count the number of times I have re-installed my system because I'm a clean freak and don't like useless stuff filling up my /home... May be obvious but I never even considered this before. +1 if I could.

Thanks.

Folks (especially coming from Windows) often forget that Linux/UNIX is designed from the start as a multi-user OS with clear file permissions controlling where things go for the system, for applications and for each, individual, user.

---

