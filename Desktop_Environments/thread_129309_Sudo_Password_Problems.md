---
title: "Sudo Password Problems"
date: 2006-02-13
forum: Desktop Environments
---

### Post by ShackletonEH on 2006-02-13
All,
   I am trying to login as root using the "su" command for sudo. When it asks me for the password I type in the same  password I use as an Administrator.It has been working until now. I rebooted the system thinking that that might fix it. 

    I get the following error message:
Authentication failed. Sorry!

Please help!

ShackletonEH

---

### Post by amunimanghi on 2006-02-13
are you in the terminal or the startup screen thingy

if you are in the start up screen thingy try logging in as

root

and enter your password. thats how i do it

---

### Post by ShackletonEH on 2006-02-13
What about when I am in Terminal? I tried the command in "su" in terminal and entered the passwrd and got the error message. let me know if this is a feature of Ubuntu. Then I'll be alright. Else this would be a problem when I am installing or updating the system

---

### Post by amunimanghi on 2006-02-13
it works with me in the terminal.

---

### Post by RonJohnson on 2006-02-13
Ubuntu doesn't allow access to root by default. The easiest way to get root without configuring the password is sudo -s. 

If you absolutely need access as root then follow the steps at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

---

