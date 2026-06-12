---
title: "Virtual Box PC to Physical PC"
date: 2009-02-02
forum: General Help
---

### Post by Tom_T on 2009-02-02
I have a Virtual Box Ubuntu 8.10 with postfix, apache2, etc installed.

I know I can back this up using True Image (or similar) and that it could be restored onto a Physical PC.. but would it work ??

Would postfix, apache2 etc all work as before ??
Just a thought ;)

thanks

---

### Post by HermanAB on 2009-02-02
Yes and no.

You could copy a virtual disk to a physical disk (using dd or cat) and reboot.  The system will have some trouble starting up, since the hardware is different.  The Linux start-up system will sort most of the issues out however.

This is similar to taking a hard disk from one desktop machine and plugging it into a completely different box by a different manufacturer and flipping the switch.  It will probably start up, but it sure won't be happy about it.

Hope that helps!

Herman

---

### Post by FluffyElmo on 2009-02-02
I agree with HermanAB, you can try it but may have issues with detection of network cards and such. Another option would be to install something like VMWare Server (I think it's free.) on the new machine and run your image directly. It has less overhead than the typical VM and many data venters use this approach to run multiple servers on one physical machine.

There is still some overhead involved, so your best option would be to try and get Ubuntu running directly on the server. But either approach is valid.

---

