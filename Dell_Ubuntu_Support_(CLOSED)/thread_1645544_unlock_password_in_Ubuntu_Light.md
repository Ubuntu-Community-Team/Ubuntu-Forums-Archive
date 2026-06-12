---
title: "unlock password in Ubuntu Light"
date: 2010-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dr.roo on 2010-12-14
Sorry if this has been answered previously - I couldn't find it. I'm new to linux and recently got a Dell M101Z laptop with Ubuntu light installed alongside Win 7. I realise it's stripped down but I seem unable to do anything from the administrative perspective - the user password appears locked (according to passwd -S) and I only get a permission denied when I try to unlock it. This is the case after a fresh reinstall from Win 7 - there appear to be no options to set the password or even user name. Any suggestions?

Thanks, Roo

---

### Post by nm_geo on 2010-12-14
> **dr.roo said:**
> Sorry if this has been answered previously - I couldn't find it. I'm new to linux and recently got a Dell M101Z laptop with Ubuntu light installed alongside Win 7. I realise it's stripped down but I seem unable to do anything from the administrative perspective - the user password appears locked (according to passwd -S) and I only get a permission denied when I try to unlock it. This is the case after a fresh reinstall from Win 7 - there appear to be no options to set the password or even user name. Any suggestions?

Thanks, Roo

Do a Google Search on Lost Locked sudo password or maybe this link.

[http://hints.macworld.com/article.php?story=20001217230925152](http://hints.macworld.com/article.php?story=20001217230925152)

It is a breach technique and well known on the Internet it appears.

---

### Post by dr.roo on 2010-12-15
Thanks. I think the problem was I didn't know how to start single user mode. I have now solved this - details as follows for others:

On Grub screen (with the two OS options) press e

Edit the last line of text from:
linux /boot/vmlinuz-2.6.35-5-generic root=/dev/sda4 ro   quiet splash ... etc etc ... osi=\"!Windows 2009\" ar
to
linux /boot/vmlinuz-2.6.35-5-generic root=/dev/sda4 ro   single

press ctrl-x to boot
A recovery menu eventually appears - select root (drop to root shell prompt)
At the prompt type: passwd Username
and then enter your new choice of password.

Restart the computer and select Ubuntu normally, and the user (sudo) password is now changed.

Roo

---

