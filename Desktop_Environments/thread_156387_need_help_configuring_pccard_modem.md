---
title: "need help configuring pccard modem"
date: 2006-04-06
forum: Desktop Environments
---

### Post by whoa_551 on 2006-04-06
I am trying to use a AmbiCom56k PCCard modem in place of my internal modem (can't get driver installed on internal one).  Ubuntu detects the pccard modem, and using the typical commands (lsmod, cardctl ident, etc.) everything seems okay with it, and the correct driver (serial_cs) is being used.  So, my question is, how do I configure Ubuntu to use my PCCard modem for dial-up, and ignore my internal modem altogether?  (Or is it even possible?) -- I'm using a laptop...

---

### Post by Ampersand on 2006-04-07
It should be possible to disable the internal modem in your laptop's BIOS setup. I've not got much experience using modems under linux, but have you looked under the networking setup (system - administration menu) to see whether you can set the default network device?

---

### Post by whoa_551 on 2006-04-07
[QUOTE=Ampersand]It should be possible to disable the internal modem in your laptop's BIOS setup. I've not got much experience using modems under linux, but have you looked under the networking setup (system - administration menu) to see whether you can set the default network device?[/QUOTE]

Thanks for responding.

I have not checked my BIOS, but for whatever reason, my experience is that it's nonconfigurable (aside from boot drive sequence and password).  I will check it again, though.

As for Networking Setup, I have looked through it several times, and haven't seen anything that can help me with this.  It does not list my pccard modem, even though terminal commands show everything fine.

---

