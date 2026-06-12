---
title: "Rebooting a server through SSH"
date: 2007-12-01
forum: Desktop Environments
---

### Post by dantheman3212 on 2007-12-01
I've set up a web server through Feisty desktop edition, and would like it just to have a power chord connected to it an thats it, and just have it sit in the corner. My problem is that I want to be able to reboot it from a different location (7 miles away), but when I restart it someone needs to log in, in there any way through SSH or some other remote desktop program to be able to restart the OS without having to log in again? Or do I just have to do it manually? Thanks

-Dan

---

### Post by Whiffle on 2007-12-01
you should be able to do shutdown -r now to reboot it, but what do you mean by "someone has to log in"?

---

### Post by dantheman3212 on 2007-12-02
It's running desktop edition, so I'd like the machine to power down completly and start again, and when ubuntu starts it needs a login name and password, and even if I disabled that, there's still the keyring that needs to be put in for the wireless card, just wondering if theres any way to have it auto log in, and maybe a script to enter the keyring?

---

### Post by Derspankster on 2008-04-27
> **dantheman3212 said:**
> It's running desktop edition, so I'd like the machine to power down completly and start again, and when ubuntu starts it needs a login name and password, and even if I disabled that, there's still the keyring that needs to be put in for the wireless card, just wondering if theres any way to have it auto log in, and maybe a script to enter the keyring?

Just configure your login to be automatic. Easily done Administration>Login Window>Security Tab> check Enable Automatic Login.  Works for me!

---

