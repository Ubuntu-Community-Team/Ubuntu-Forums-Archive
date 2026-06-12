---
title: "First boot from mini.iso"
date: 2011-11-22
forum: Desktop Environments
---

### Post by Ritmo2k on 2011-11-22
Why does the first boot after installing with the mini.iso leave you at a terminal with a blinking cursor, its not until you switch to tty1 you get a login prompt?

Thanks

---

### Post by jerrrys on 2011-11-23
If you expect to see gnome-terminal, you must install it:

sudo apt-get install lightdm gnome-session-fallback gnome-terminal

---

### Post by Ritmo2k on 2011-11-28
If you had no intention of installing a desktop on the server, you are forced to always switch tty after it boots.

How do you change the final tty it finishes booting to?

Thanks

---

### Post by jerrrys on 2011-11-28
ubuntu-standard

I ran this package once without any GUI installed and if I remember right, it gives a terminal experience with a UI mix.  May want to try it.

[ATTACH]208157[/ATTACH]

---

### Post by gmargo on 2011-11-28
> **Ritmo2k said:**
> 
How do you change the final tty it finishes booting to?

Good question, and I want the answer too.

Here's an information bit:  If you install the "server" edition, then the tty starts up on 1 like it should.  So we should be able to figure out the difference.

---

### Post by gmargo on 2011-11-28
I love virtual machines.

I installed two new systems, side by side.  One from mini.iso, one from the server .iso.

Here's the difference, from **/proc/cmdline**:

The mini.iso install has "splash quiet vt.handoff=7" appended to the boot parameters, where the server install does not.  Sounds like that "vt.handoff" is the culprit.

Now see the file **/etc/grub.d/10_linux**.  It adds "vt.handoff=7" if the "splash" parameter is present.

So go and edit **/etc/default/grub**.
Remove "splash quiet" from the GRUB_CMDLINE_LINUX_DEFAULT string so it is empty:
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```And run "update-grub".  Then reboot happily onto the default tty1.

---

### Post by Ritmo2k on 2011-11-28
Nice dude!

---

