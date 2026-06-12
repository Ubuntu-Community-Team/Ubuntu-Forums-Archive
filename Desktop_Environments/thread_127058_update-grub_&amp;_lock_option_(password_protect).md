---
title: "update-grub &amp; lock option (password protect)"
date: 2006-02-08
forum: Desktop Environments
---

### Post by nocturn on 2006-02-08
I added some security to my grub setup.

First, I set up an MD5 password to protect editing the boot options.  Secondly, I added lock to each recovery session to prevent people getting instant-root.

Now, when a kernel update becomes available, update-grub is run  by the packages (good, because I get the new kernel).  But it removes all the lock options and I have to add them back manually (not secure because I might forget).

Is there a way (setting) to have it added automaticly?

---

### Post by nocturn on 2006-02-13
Bump

---

### Post by lcg on 2006-02-13
[QUOTE=nocturn]I added some security to my grub setup.

First, I set up an MD5 password to protect editing the boot options.  Secondly, I added lock to each recovery session to prevent people getting instant-root.

Now, when a kernel update becomes available, update-grub is run  by the packages (good, because I get the new kernel).  But it removes all the lock options and I have to add them back manually (not secure because I might forget).

Is there a way (setting) to have it added automaticly?[/QUOTE]
/sbin/update-grub is a shell script, searching it for "lock" reveals this:
```
# should grub lock the alternative boot options in the menu
lockalternative="false"
```

That option is also present in the automagic block in the menu.lst.
I suppose you could set "lockalternative=true" in your menu.lst, that way all the alternative sections should be locked after running update-grub. I haven't tried it, though.

HTH,
Lars

---

### Post by nocturn on 2006-02-13
[QUOTE=lcg]/sbin/update-grub is a shell script, searching it for "lock" reveals this:
```
# should grub lock the alternative boot options in the menu
lockalternative="false"
```

That option is also present in the automagic block in the menu.lst.
I suppose you could set "lockalternative=true" in your menu.lst, that way all the alternative sections should be locked after running update-grub. I haven't tried it, though.

HTH,
Lars[/QUOTE]

I'll try that one, thank you

---

