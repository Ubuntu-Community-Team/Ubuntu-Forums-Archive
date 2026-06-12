---
title: "How do I get rid of the Ubuntu dual boot screen?"
date: 2009-05-03
forum: General Help
---

### Post by cheese123 on 2009-05-03
I was dual booting Windows XP and Ubuntu 9.04. But I needed some HD space so I decided to uninstall Ubuntu, after complete removal I still get the multi boot screen when I start up my machine. Is there any way to remove this? Thanks.

---

### Post by adamfaulkner1 on 2009-05-03
Try something like this:

1. boot the XP install cd
2. Choose to go into the Recovery Console
3. Type "fixmbr"

I'm pretty sure that would work, but I am unable to test it.

---

### Post by -kg- on 2009-05-03
As an alternative to that, you could delete the Ubuntu lines in the GRUB menu.lst, rendering the XP lines as default, then change the "timeout" value to "0"

This would cause GRUB to boot only to XP, and with a timeout of 0 you wouldn't see the GRUB menu at all...it would just boot directly to XP.

But the solution above works as well, as long as you have the XP installation disk.

<edit> If you don't want to do that much editing, you could just set Windows as being the default for booting.  Then set the timeout value as indicated and you would have the same effect.

---

### Post by cheese123 on 2009-05-03
> **adamfaulkner1 said:**
> Try something like this:

1. boot the XP install cd
2. Choose to go into the Recovery Console
3. Type "fixmbr"

I'm pretty sure that would work, but I am unable to test it.

That didn't work :(

---

### Post by cheese123 on 2009-05-03
> **-kg- said:**
> As an alternative to that, you could delete the Ubuntu lines in the GRUB menu.lst, rendering the XP lines as default, then change the "timeout" value to "0"

This would cause GRUB to boot only to XP, and with a timeout of 0 you wouldn't see the GRUB menu at all...it would just boot directly to XP.

But the solution above works as well, as long as you have the XP installation disk.

<edit> If you don't want to do that much editing, you could just set Windows as being the default for booting.  Then set the timeout value as indicated and you would have the same effect.

Could you possible tell me how to do this? Sorry I am not sure how to do this.

---

### Post by lisati on 2009-05-03
> **cheese123 said:**
> That didn't work :(

You might want to try, again from the Windows recovery console, the following:
```
fixmbr
fixboot

```

---

### Post by cheese123 on 2009-05-03
> **lisati said:**
> You might want to try, again from the Windows recovery console, the following:
```
fixmbr
fixboot

```

That's what I did, after each entry I confirmed by press "y". Then rebooting, but no results.

---

### Post by lisati on 2009-05-03
> **cheese123 said:**
> That's what I did, after each entry I confirmed by press "y". Then rebooting, but no results.

Does adding "C:" to the commands help?

---

### Post by cheese123 on 2009-05-03
> **lisati said:**
> Does adding "C:" to the commands help?

No :confused:

---

### Post by -kg- on 2009-05-03
Are you still able to boot into XP from the GRUB boot screen?

---

### Post by lisati on 2009-05-03
Just a thought: did you install "within" windows using Wubi?

---

### Post by fornix on 2009-05-03
Do you have two different hard disks?
If you do, then in bios you might want to change the boot priority so that the disk with windows gets higher priority.

---

