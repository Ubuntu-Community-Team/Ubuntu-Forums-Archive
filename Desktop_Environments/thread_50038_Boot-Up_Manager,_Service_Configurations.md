---
title: "Boot-Up Manager, Service Configurations"
date: 2005-07-18
forum: Desktop Environments
---

### Post by jlacroix on 2005-07-18
Hello all, I am trying to get rid of the unnecessary startup items in Ubuntu, here is a list of things that I have set to startup. Please let me know what I can get rid of, I have BUM (boot-up manager) installed that will let me turn things off that I don't need. I don't have a printer, or scanner, I have just a standard setup with a few USB game controllers.

Attached is a screenshot of Boot-up Manager that shows all the things that I have turned on. What can I disable?

---

### Post by mad_scientist03 on 2005-07-18
One monotonous way to go about is to start disabling services one by one, and determine which of the services are essential. You will want to keep syslogd, klogd, and gdm at the minimum.

Based on the descriptions provided in your screenshot, you should be able to determine whether the others are necessary. If you are not using a laptop, disable all the laptop-specific services. If you don't want (or use a different driver for) sound, disable alsa. If you don't have a printer, disable cupsys. From what I would guess, you do not need rsync.

Try it out and see what works best for you.

---

