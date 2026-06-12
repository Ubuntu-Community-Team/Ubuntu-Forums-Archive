---
title: "Problem Installing Login Manager"
date: 2005-11-02
forum: Desktop Environments
---

### Post by hzs202 on 2005-11-02
Hi All,

I'm using Hoary 5.04 and I recently tried to change my login-manager. I installed some themes via gnome login screen setup and now only HumanCircle theme works. I cannot change the theme to anything else... I'm not sure of the problem but it is frustrating.

I move HumanCircle to another file and rebooted the machine... I could not login at all... not default or backup login screen was chosen. 

I then deleted all of the login-manager files and reinstalled them... however the same condition remained true... I cannot change my login screen. Please Help!

Best,

---

### Post by Xian on 2005-11-02
[QUOTE=hzs202]I'm using Hoary 5.04 and I recently tried to change my login-manager.[/QUOTE]
I'm not certain what you are talking about. When you say you tried to change your login manager do you mean to say that you wanted to change just a theme, or that you tried to switch to another login manager like kdm?

---

### Post by hzs202 on 2005-11-02
[QUOTE=Xian]When you say you tried to change your login manager do you mean to say that you wanted to change just a theme, or that you tried to switch to another login manager like kdm?[/QUOTE]Sorry, I just mean the theme... I am using gdm and I tried to change the theme... then when I did this I could not get the login screen manager in Gnome Desktop to switch from the default. Its as if it could not read the other the themes however, I could see them in the login screen manager.

---

### Post by Xian on 2005-11-03
The only thing I can suggest is to open the gdm setup w/sudo in a terminal, and then try to make the changes from that entry point. In this manner you will eliminate a host of potential roadblocks. 

```
$ sudo gdmsetup
```

---

### Post by hzs202 on 2005-11-03
[QUOTE=Xian]The only thing I can suggest is to open the gdm setup w/sudo in a terminal...[/QUOTE]That is precisely the problem... gdm setup whether opened from a terminal or gnome doesn't allow me to switch login screens. The bullet that is shaded to indicate which login-screen is selected will not move from HumanCircle (a greeting theme).

What is going on?

---

