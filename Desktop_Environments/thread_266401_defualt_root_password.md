---
title: "defualt root password"
date: 2006-09-27
forum: Desktop Environments
---

### Post by uk_sphinx on 2006-09-27
Here's my prob.
i want to change the default root password.
i only installed unix last night and this is my first day experimenting with it.
when i installed it last night i left it to install while i ocupied myself with somthing else.
i am good with comps on windows os and was very consiouse of security for it.this inevitably led me to sites about hacking.i hav inevitably read pages from certain sites regarding hacking unix boxes.some of these sites say that the first thing hackers do is check to see if they can log in using the default password set up by install.
i am currently logged in as oem(default on sudo i think) and i have changed the password for this which was defaulted as blank.
from as far as i know i have root priveliges on this username as it is the first acount made.
i dont know what the default passwrd for root is as like i said before i left the install to run on its own.
i am guessing that it had a timer on the page where it asked for root passwrd and automaticaly skipped it.

i typed the command sudo -i to change the password for root and entered my oem passwd and the neww pass and the confirm pass and it excepted it.
does this mean that root or super user is actualy oem?
if not could someone plz tell me the default passwd for root?

thinking about it you lot might be thinking that i am trying to get this root pass from someone elses terminal.
if you can think of a way to question me as to wether im being truthfull or not go ahead.
this brings me to the next thing.does ubuntu actually ask you for a password at install or have i got this wrong aswell? i was thinking along the lines of it picking a random password.if it has done this then i guess il have to install it again.

thnx

---

### Post by Kateikyoushi on 2006-09-27
The docs write about the root account.

[Sudo.]("https://help.ubuntu.com/community/RootSudo?highlight=%28root%29")

---

### Post by ayoli on 2006-09-27
there's no default root password, ubuntu root account is disabled by default.
sudo -i asks you for your own password then gives you a root shell.
if you want to enable root account you have to set a root password:
```
sudo passwd
```you will be prompted for your own user password then you should enter your new root password and confirm it.
but enable root account is not neccessary. you may want to read this page:
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

---

### Post by uk_sphinx on 2006-09-27
yes but when i used the sudo -i command like the doc said it said on the console pass changed but there is no acount as root in user acount setup

---

### Post by Ramses de Norre on 2006-09-27
Read [this](http://wiki.ubuntu.com/RootSudo).

As you can read there ubuntu disables the root acount by default, but if I'm correct you have set a root passwd? In that case you can disable the root acount again and I can explain you how.

If not: read the link for all info on how to use root priviliges with a disabled root acount.

---

### Post by uk_sphinx on 2006-09-27
thanks for the replys

i have got it now.
you have to type "sudo root passwd" to enable the root acount and set the password
then type sudo -i to change from oem to root

---

