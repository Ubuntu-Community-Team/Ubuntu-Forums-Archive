---
title: "Loading Desktop Enviornment from system command Prompt....."
date: 2007-10-27
forum: Desktop Environments
---

### Post by mdccdm2000 on 2007-10-27
Hello, Fellow Linux Distronee'rs. I just installed Unbuntu linux Server on my new Gateway 386gz computer. I was able to get through the install right away. but when I try to access the login screen in GUI mode. I get a enter Username, Then Password Prompt. Once I login. I get A plain Old command Prompt. No Gui or Graphic based Desktop. As I am new to Linux. Can you please Help. Thanks. In need of Help. Ciao..... :o). :(

---

### Post by kerry_s on 2007-10-27
the server has no gui. you can add 1. 

full de:
[B]sudo apt-get install xorg gdm xubuntu-desktop
reboot[/B]

or 

light wm:
[B]sudo apt-get install xorg fluxbox
startx
[/B]

---

### Post by mdccdm2000 on 2007-10-27
Thanx... Will Try. Laters..... :o).

---

### Post by mdccdm2000 on 2007-10-27
Hello Sexy. Tried loading Sudo Commands Provided by yours truly but everytime I ran either one of the command I recieved an E: couldn't find Package Xorg. error. did I mess something up during the install. Please Respond. Reply. Thanks.... :(

---

### Post by kerry_s on 2007-10-27
> **mdccdm2000 said:**
> Hello Sexy. Tried loading Sudo Commands Provided by yours truly but everytime I ran either one of the command I recieved an E: couldn't find Package Xorg. error. did I mess something up during the install. Please Respond. Reply. Thanks.... :(

What server version are you running?
this->
[B]sudo apt-get update
sudo apt-get install x-window-system-core gdm xubuntu-desktop[/B]
or
**sudo apt-get install x-window-system-core fluxbox**

---

