---
title: "Unable to login to Windows machine"
date: 2005-12-18
forum: Desktop Environments
---

### Post by abyss6 on 2005-12-18
In Terminal Server Client, I'm able to call up a windows login screen, but when I type in the username and password, it says that it can't log me on.  Does this mean something isn't set up right on the windows box?  If so, what do I need to do to fix this?

---

### Post by amohanty on 2005-12-18
In windows do you:

1. have terminal server on?
2. allow more than one user to login?


am

---

### Post by professor_chaos on 2005-12-18
nevermind, I thought I knew this, but as typing realize I did not, so appoligies.

---

### Post by abyss6 on 2005-12-18
I created a new user called 'remote' and I'm able to log in now, likewise with the 'administrator' login, but I have to log off my regular account in order to do so.  As a result, none of my normal settings are there.  Is there a way to get in there so I can use my windows box as-is?

---

### Post by amohanty on 2005-12-18
Thats because of the answer to my second question 
> 2. allow more than one user to login?
on your machine is 1.

I think in the control panel, you can setup the terminal server settings so that it allows more than one user to login at the same time. If you enable that, you can login simulatenously. Unfortunately I dont have access to an xp box right now so cant tell you what the option is, however look around there or fire up the windows help, and you can find it quite easily.

HTH

---

