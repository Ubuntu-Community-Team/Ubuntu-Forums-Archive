---
title: "Can I get to terminal with a crashed xserver?"
date: 2007-03-29
forum: Desktop Environments
---

### Post by DapperMe17 on 2007-03-29
Hi

I recently edited my xorg.config file with an incorrect driver name, which caused xserver to crash at login, leaving me at the black screen(not the GUI). 

How can I get to a terminal from this screen?

Thanks

---

### Post by JAPrufrock on 2007-03-29
If you have a prompt, you can work directly in bash.  If it's a blank screen, Ctl-Alt-F6 will get you to a prompt.  Ctl-Alt-F7 will get you back to where you started from.  Type "gnome-desktop" in a terminal to start gnome.  Ctl-Alt-backspace will also restart gnome.

---

### Post by DapperMe17 on 2007-03-29
I suppose I could work with bash. I'll substitute "kde-desktop" as its a Kubuntu box.


Thanks for your information!

---

### Post by dreadlord_chris on 2007-03-30
> **DapperMe17 said:**
> I suppose I could work with bash. I'll substitute "kde-desktop" as its a Kubuntu box.


Thanks for your information!

that would be:
```

sudo /etc/init.d/kdm restart

```

---

