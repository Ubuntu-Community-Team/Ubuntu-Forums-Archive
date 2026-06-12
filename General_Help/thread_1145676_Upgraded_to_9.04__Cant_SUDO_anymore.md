---
title: "Upgraded to 9.04:  Cant SUDO anymore"
date: 2009-05-01
forum: General Help
---

### Post by tinker123 on 2009-05-01
Hi;

I recently upgraded to 9.04 from the lates *.*.    Since I did, I can't use SUDO anymore.  When I do, I get this error message:

> 
steve@Wisdom:~$ sudo bash
[sudo] password for steve: 
steve is not in the sudoers file.  This incident will be reported.
steve@Wisdom:~$ 


Any idea how I can fix this?

Thanks

---

### Post by drs305 on 2009-05-01
You will have to boot to the recovery mode, select "Drop to root shell prompt", then run the following and reboot:
```

adduser *yourusername* admin

```

---

### Post by tinker123 on 2009-05-01
How do I boot to recovery mode?

---

### Post by Yellow Pasque on 2009-05-01
Press 'Esc' after your BIOS does its thing, and you will be greeted with the GRUB menu.

---

### Post by tinker123 on 2009-05-02
Fixed.  Thanks guys!

---

