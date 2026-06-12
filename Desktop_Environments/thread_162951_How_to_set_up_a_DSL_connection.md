---
title: "How to set up a DSL connection??"
date: 2006-04-19
forum: Desktop Environments
---

### Post by Mr Aragorn on 2006-04-19
Sorry im such a noob in Ubutu, but I have a DSL connection, I have lo input a login and password but when i tried to set it up I didnt find an option for login and password. 

THX

](*,)

---

### Post by shadowfox on 2006-04-20
Go to System >> Administration >> Networking and see if your network card is listed there.

If not, that's your first task.

If yes, go ahead turn on DHCP and most likely you do not have to enter any login username/password.

Open firefox and try to surf.

---

### Post by ec2 on 2006-04-20
My friend has a DSL connection too. Password and username is just what he is afraid of, so he keeps on using windows. I wanted to ask, what should i do, IF my network card isn't listed in the Networking tab?

---

### Post by Mr Aragorn on 2006-04-20
I turn it on, but I dont know were to put mi login and password to make the connection.

---

### Post by worty on 2006-04-21
[QUOTE=Mr Aragorn]I turn it on, but I dont know were to put mi login and password to make the connection.[/QUOTE]

Hi Mr Aragorn, assuming your network card is detected and everything works, go to the console and type:

> sudo pppoeconf

after you go through the setup, type

> pon dsl-provider
to turn it on

and

> poff

to turn it off.

Go here for some other options and help.
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by Mr Aragorn on 2006-04-23
Yayyyyyyyy it worked, thank you!!!:-D :-D

---

