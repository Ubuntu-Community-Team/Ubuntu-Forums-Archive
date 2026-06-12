---
title: "can't use the store or synaptic"
date: 2020-08-21
forum: Desktop Environments
---

### Post by jarp53 on 2020-08-21
after installing XFCE desktop I click on synaptic or any item in the snap store but nothing happens , and if I try software that needs a password then a pop up notification shows that I don't have permission to install software .

---

### Post by ActionParsnip on 2020-08-21
If you run:
```

sudo apt update

```
You won't get any feedback as you type. Does it hit the repos OK

---

### Post by jarp53 on 2020-08-21
yes it updated

---

### Post by CelticWarrior on 2020-08-21
No, it's fully updated only when you do 'sudo apt full-upgrade' after 'sudo apt update'.
And the question "[COLOR=#000000]Does it hit the repos OK?" is about having no errors when querying the repositories. Where they all OK when you run it?[/COLOR]

---

### Post by ajgreeny on 2020-08-21
You installed the Xfce desktop, but installed it into what? 
Which version of the *ubuntu family are you using?
Are you using xorg or wayland graphical system; you choose which you wish to use at login if you have both installed?
I assume you are the first user added when the system was installed which would mean you are a member of the ***sudo*** group, but if your user was added by another user after installing the system you may not be in the sudo group.
What does the terminal command ***groups*** give as output?

---

### Post by jarp53 on 2020-08-21
yes it hits the repos  with no errors; Ubuntu 20.04 , after command < [COLOR=#242729][FONT=Consolas]env | grep -i wayland > there was no respond so I read is wayland ,and I am the only user;
[/FONT][/COLOR]jr@jr-Z68X:~$ groups
jr adm cdrom sudo dip plugdev lpadmin scanner lxd sambashare
jr@jr-Z68X:~$

---

### Post by jarp53 on 2020-08-23
I'm marking this as solved because I'm giving up on the idea of using Ubuntu with fxce desktop; so I'm trying Xubuntu  again and so far this time I'm impress , from here on is just wait and see if it remains stable

---

