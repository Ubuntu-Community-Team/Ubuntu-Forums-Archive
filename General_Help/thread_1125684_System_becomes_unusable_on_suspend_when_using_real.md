---
title: "System becomes unusable on suspend when using realtime kernel"
date: 2009-04-14
forum: General Help
---

### Post by ireneshusband on 2009-04-14
When I suspend my machine with the realtime kernel, the interface locks up and I have to force a hard shutdown. I do not get this with the generic (Intrepid amd64) kernel. My machine is a Thinkpad R61i.

What happens is that I get a message of the form "Freezing of tasks failed after 20.00 seconds (2 tasks refusing to freeze)". The actual number of obdurate can vary.

The first two or three times this happened, the tasks that refused to freeze were NetworkManager and wpa_supplicant. The next time it was those two plus avahi-daemon and gnome-do.

At this point the suspend indicator light kept flashing as if the machine was still in the process of suspending, and the disk light was showing some intermittent activity, but the interface froze entirely, hence the need to force a shutdown.

Does anyone know what is going on here and how to stop it? A non-realtime kernel is not an option for the work I need to do at the moment.

Many thanks in advance.

---

### Post by me13221 on 2009-05-02
> **ireneshusband said:**
> 
The first two or three times this happened, the tasks that refused to freeze were NetworkManager and wpa_supplicant. The next time it was those two plus avahi-daemon and gnome-do.


How did you figure out which tasks were the ones that refused to freeze?

---

### Post by BslBryan on 2009-05-02
Does the screen go blank?

---

### Post by ireneshusband on 2009-05-03
> **me13221 said:**
> How did you figure out which tasks were the ones that refused to freeze?

It hangs with a message to this effect displayed, listing the tasks refusing to freeze.

---

