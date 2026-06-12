---
title: "User Priveleges"
date: 2006-09-27
forum: Desktop Environments
---

### Post by spacecowboy706 on 2006-09-27
I am trying to change my source list at /etc/apt/sources.list and everytime i make a change the Save button is greyed out and it wont let me save it. I am the owner of this pc and i have the password needed to open the administrative functions. what do i need to do?

---

### Post by madmetal on 2006-09-27
open a terminal and type
sudo gedit /etc/apt/sources.list
then give password.. 
i think now save button is ok!

---

### Post by spacecowboy706 on 2006-09-27
Outstanding, that worked great. God the people on Ubuntu are so helpful and are right on the target every time.

I wonder is there a way to add myself as the super user or root or whatever it is called, so i dont have to keep typing in the darn password every five minutes?

---

### Post by aysiu on 2006-09-27
It's every fifteen, actually. And it may seem quite often when you're first getting set up, but once you get going, you probably won't need to perform administrative tasks as often.

You may find it useful to create a panel launcher button with the command ```
gksudo nautilus
``` This allows you to edit/browse as root.

---

### Post by spacecowboy706 on 2006-09-27
thanks for the advice. added it.

---

