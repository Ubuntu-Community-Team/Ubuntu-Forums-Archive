---
title: "IceWM problems"
date: 2005-01-18
forum: Desktop Environments
---

### Post by christooss on 2005-01-18
I am using IceME for editing menus and when I add something to PROGRAMS that thing desapear.

I am from slovenia and now my IceWM is in slovene language. How can I change it back to english

Thanks for the anwser

---

### Post by az on 2005-01-18
The last time I used it, I noticed that iceME is buggy.

Do you have the menu package installed?
apt-get install menu
(You probably do, but I figured that maybe that would help)

---

### Post by christooss on 2005-01-19
I alredy solved it with command UPDATE-MENUS.

Now I've got few more qouestions.

1. If I go to logout menu and click reboot system. System logsout and then XDM starts. Same happends if I click Shutdown or Logout. Reboot is working if I write it in terminal. What is the problem?

2. How can I terminate IceWM? I tried
$ ps -e | grep icewm

$ kill **** (icewm PID)

IceWM does shutdown but it starts again. And I can login again.

---

### Post by az on 2005-01-19
You configure the shutdown, reboot and logout commands.  If your user does not have permission to run what is your current default, you will get bizarre behaviour like you describe.  

Are you runing Icewm from gdm or are you just starting X with icewm as your default?

---

### Post by christooss on 2005-01-19
I am runing icewm from xdm.

---

