---
title: "How can I set the Default operating system?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by ivictor80 on 2006-04-03
Hello,

I have just installed Ubuntu 5.10 on a computer on which I have also Windows XP. The boot-manager (GRUB) is now installed in the MBR. Now the default operating system is Ubuntu, but I want to set Windows XP as the default one. How can I do that?

And another question: hpw can I shorthen the time the computer waits for me to select an operating system to boot? Now that time is 10 seconds, but I want that time to be 5 seconds.

Thank you in advance for your answers.

---

### Post by frodon on 2006-04-03
look here for the first question : [http://ubuntuforums.org/showthread.php?t=153983](http://ubuntuforums.org/showthread.php?t=153983)

---

### Post by taurus on 2006-04-03
Boot into Ubuntu and modify /boot/grub/menu.lst.  If Windows XP is the fourth entry in there, then change the default value from 0 (currently) to 4 and change the timeout to whatever seconds you want...
```

sudo gedit /boot/grub/menu.lst

```
Save it and reboot...

---

### Post by zerhacke on 2006-04-03
[QUOTE=taurus]Boot into Ubuntu and modify /boot/grub/menu.lst.  If Windows XP is the fourth entry in there, then change the default value from 0 (currently) to 4 and change the timeout to whatever seconds you want...
[/QUOTE]
If Windows was 4th, you'd set the default value to 3.  Computers and Linux begin counting at 0, not 1.

---

### Post by ivictor80 on 2006-04-04
> If Windows was 4th, you'd set the default value to 3. Computers and Linux begin counting at 0, not 1.

I set the value as 4, not 3 because, even the count begins from 0, there is an extra line which says "Other operating systems", which is selected if I set the default value as 3.

---

### Post by zerhacke on 2006-04-04
[QUOTE=ivictor80]I set the value as 4, not 3 because, even the count begins from 0, there is an extra line which says "Other operating systems", which is selected if I set the default value as 3.[/QUOTE]
That's right, Ubuntu adds silly things to the list.  I have taken that out of my menu.lst file because it's superfluous.  Forgot about that.

---

