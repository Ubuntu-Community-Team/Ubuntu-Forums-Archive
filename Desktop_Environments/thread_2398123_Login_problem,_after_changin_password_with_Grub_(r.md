---
title: "Login problem, after changin password with Grub (root terminal)"
date: 2018-08-07
forum: Desktop Environments
---

### Post by sudenna on 2018-08-07
Hey

I have a problem with my Ubuntu 14.04 install.
I was forgotten my password of it, and try'd to fix it.
And on different site's, i find the solution to fix this problem, with root terminal (with Grub by booting the computer)
See at this Youtube page.
[https://youtu.be/qGpvCZO2oOc](https://youtu.be/qGpvCZO2oOc)

I did the following things:
Booting in Recovery modus.
Than select "Root" in the screen.
Next i enter the following commands into the terminal.


mount -n -o remount,rw /
passwd "login naam"
"New password"
"Repeat new password"
reboot

This did work fine.
Because by the login screen, the system sees my new password as the right one (by any other password the computer give a error command).
But a few seconds later (with the correct password), i get back at the login screen. Like nothing ever happend.

Do i have used maybe the wrong terminal commands?

Thanks in advance
Ruben

---

### Post by sudenna on 2018-08-17
Does someone have an idea of this problem??

---

### Post by steeldriver on 2018-08-17
Is your home directory encrypted?

You may be able to get more information about why it's failing by logging into one of the CLI virtual terminals (Ctrl-Alt-F1 thru Ctrl-Alt-F6) and examining your xsession-errors file

```

tail ~/.xsession-errors

```

---

### Post by sudenna on 2018-08-17
> **steeldriver said:**
> Is your home directory encrypted?

You may be able to get more information about why it's failing by logging into one of the CLI virtual terminals (Ctrl-Alt-F1 thru Ctrl-Alt-F6) and examining your xsession-errors file

```

tail ~/.xsession-errors

```

Yes, my home directory is encrypted.
How do i get into a CLI virtual terminal?

Gr ruben

---

### Post by steeldriver on 2018-08-17
You can get to a CLI virtual terminal using the key combination(s) that I mentioned - Ctrl-Alt-F1 thru Ctrl-Alt-F6

After that, you can either re-wrap the ecryptfs passphrase or change your password back to the old one - this thread on askubuntu is a few years old but the solutions are still valid AFAIK:

[can't log in after password change (ecryptfs)](https://askubuntu.com/questions/281491/cant-log-in-after-password-change-ecryptfs)

Hope this helps

---

### Post by sudenna on 2018-08-18
I search long for fixing the problem like you say.
And it did not work. So i search into my backup drive's and found a backup of nov '17, so it wil do for a reinstall.
(And loss of other files between this date)

---

