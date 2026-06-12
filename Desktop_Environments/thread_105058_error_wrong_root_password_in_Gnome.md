---
title: "error: wrong root password in Gnome?"
date: 2005-12-17
forum: Desktop Environments
---

### Post by shaqan on 2005-12-17
Hi.

I've just installed Ubuntu and i got a notification in my upper right corner stating i had 37 updates available. I click one of the options and get asked to input the password. I'm not quite sure what password it wants, mine or the admins.

If i input mine, the dialoge box dissapears and nothing apparently happens. If i try to click "package manager", "show all updates" etc, i only get that annoying "click" sound (it doesn't even want my password anymore).

If i input the adming password i get wrong password. Now i can click again and i will be prompted for a password again).  The strange thing is i can log onto root in the console with that very password. 

Help please?

PS. Sorry if i'm offending anyone by my english :)

---

### Post by aysiu on 2005-12-17
It should be the password of the first user you created during installation (**if you did a regular installation**).

The fact that you have a root account that you can log into separately leads me to believe you might have done an **expert installation**. Did you?

---

### Post by earobinson on 2005-12-17
Sounds like the program crashed and wont run agan.

go to the terminal and do
```
sudo synaptic
```
type in your password then mark all upgrades and install. The install link thing should go away and work next time. FYI it wants your password assuming u have sudo priviliges

---

### Post by earobinson on 2005-12-17
[QUOTE=aysiu]It should be the password of the first user you created during installation (**if you did a regular installation**).

The fact that you have a root account that you can log into separately leads me to believe you might have done an **expert installation**. Did you?[/QUOTE]
fast as always aysiu

Is not your first statment false, it wants the current users password assuming that user has sudo rights?

---

### Post by aysiu on 2005-12-17
[QUOTE=earobinson]
Is not your first statment false, it wants the current users password assuming that user has sudo rights?[/QUOTE] You're right, actually. Good point.

---

### Post by shaqan on 2005-12-17
Well, i DID run an expert installation, so you are right there. :) (i think i had to as regular install didn't give me the option to set the GRUB parameters myself).

I tried the "sudo synaptic" in the console, it asked for a password, then nothing happened... maybe a reinstall will solve it? :rolleyes: 

Thanks for the replies!

---

### Post by earobinson on 2005-12-17
I assume in the expert install you set up a root account?

If so this should work:
```
su
<root password>
synaptic
<do updates>
exit
```

---

### Post by shaqan on 2005-12-17
Thanks and THANKS. That was the final piece in my noob puzzle :D

---

### Post by earobinson on 2005-12-17
not a problem, you should also be able to edit the permisions of the current user to make sudo work so that you could do it both ways

---

