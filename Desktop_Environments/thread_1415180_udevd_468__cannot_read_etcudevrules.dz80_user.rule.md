---
title: "udevd 468 : cannot read /etc/udev/rules.d/z80_user.rules"
date: 2010-02-24
forum: Desktop Environments
---

### Post by islamux on 2010-02-24
i have sabily gaza
[http://www.sabily.org/website/](http://www.sabily.org/website/)
 that build ubon ubuntu 9.10 
i went well and after make the letest update and after reboot i saw this letter before i enter to the gnome desktop
> udevd 468 : cannot read /etc/udev/rules.d/z80_user.rules
pleas help me my friend

---

### Post by KIAaze on 2010-04-10
I just had a similar error message on boot:
```
init: ureadahead-other main process (531) terminated with status 4
udevd [513]: can not read '/etc/udev/rules.d/z80_user.rules'

```
It stopped the booting process.

After a reboot it didn't happen again and everything went normally.

---

### Post by Lightstar on 2010-04-30
Same here

udevd[397]: can not read '/etc/udev/rules.d/z80_user.rules'

anyone got a fix?

---

### Post by KIAaze on 2010-04-30
I just removed the file.
It doesn't belong to any package according to dpkg -S, the ubuntu package site or apt-file search (suspect!).
And if I remember correctly, it was even an empty file.

You can move the file to a safe location for backup if you want.

Also, I recommend reading man udev to understand what such files are supposed to do and what their names and permissions should be to work:
```
man udev
```

---

### Post by dcstar on 2010-05-15
> **Lightstar said:**
> Same here

udevd[397]: can not read '/etc/udev/rules.d/z80_user.rules'

anyone got a fix?
```
gksudo /etc/udev/user.rules
```

Add in a single "#" to the previously empty file, save and close the file. No more errors.

---

### Post by Axilus on 2011-08-27
> **dcstar said:**
> ```
gksudo /etc/udev/user.rules
```

Add in a single "#" to the previously empty file, save and close the file. No more errors.

That works for me! But can you please explain the reasons to why that worked/why the error was happening?

---

### Post by hwttdz on 2011-09-17
The error is probably happening because they're checking if the file exists and has non-zero size.  The file exists, but it has zero size, so the check was failing.  But it would just carry on.  Putting a comment in there lets it think the file exists, and when it reads the file, it still gets nothing as was the case before.

---

