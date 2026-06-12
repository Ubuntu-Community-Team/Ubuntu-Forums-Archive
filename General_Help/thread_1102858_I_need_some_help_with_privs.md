---
title: "I need some help with privs"
date: 2009-03-22
forum: General Help
---

### Post by NazGHuL00 on 2009-03-22
Hello, I am pretty new to ubuntu, to this forum too.
I had many questions about ubuntu many was solved here; other as still unanswered :P.


My problem is that i need to give full priviledges to my user.
So i can edit/delete/move etc etc.

I saw similary threads but i could not do it.

Can you explain me step by step how to do it, Cause i am newbie :P

I am using Ubuntu 8.04

P.S sorry if i post in a wrong seccion or sth. But i am new here.

---

### Post by zvacet on 2009-03-22
If you made just one account (one user) then you have all privileges to install,delete...Always will ask for your password (one you used when you instaled Ubuntu) and if you want to do that things in terminal you will not see anything when you type your password.Just type correctly and that is it.

---

### Post by NazGHuL00 on 2009-03-22
Sorry, But i dont undertand comletelly. In accounts&users there are 2.
root: The first one.
NazGhuL: Mine one.



I am using mine one and when i am trying to edit sth in usr/etc/lib etc...
I doesnt let me do that. I want to move a skin to the Amsn and i cannot.
I want edit etc/hosts and i cannot save the edited file. ://
:(

---

### Post by zvacet on 2009-03-22
Just to be sure (because I´m ~100% sure that you have admin privileges with NazGhuL account) go to the users&groups and under advanced (I think) see if admister system is checked.

To sue admin privileges you have to use **sudo** or **gksudo** in terminal.For editing /etc/hosts

```
gksudo gedit /etc/hosts
```

Read [this]("https://help.ubuntu.com/community/RootSudo") for more information about using sudo.

---

### Post by NazGHuL00 on 2009-03-22
Ok, That's to edit hosts for one time.

I want to make it normally every time.

Not with this command.

How can i take the privs to make it every time?

---

### Post by Admiral Yi on 2009-03-22
You can't change this. ever time you want to edit root files you will need root permissions. Try:

```
sudo passwd
```

It will ask for your password, then you will be able to set a root pass. NO when you type:

```
Su
```

it will ask for the root password then make you root. You will now be able to edit the files using the terminal.

---

### Post by NazGHuL00 on 2009-03-22
I press alt+F2 and the ```
 sudo passwd 
``` and nothing happens :(

---

### Post by Hobgoblin on 2009-03-22
> **NazGHuL00 said:**
> Ok, That's to edit hosts for one time.

I want to make it normally every time.


It's not really a good idea because with such privileges you can very easily break things.

Better to learn to love sudo/gksudo

---

### Post by NazGHuL00 on 2009-03-22
Ah, i dont mind for it. I dont think i am goinh to make sth wrong. I just want take full prirvs. T_T Who can help me? :/

---

