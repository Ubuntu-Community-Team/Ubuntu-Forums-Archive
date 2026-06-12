---
title: "I dont want desktop"
date: 2007-05-16
forum: Desktop Environments
---

### Post by bveb on 2007-05-16
Hi all.
I dont want any desktop environment and login screen on my computer. I only want default X  init session.. And also I want to login automatically Which configuration file can I use?

---

### Post by WakkiTabakki on 2007-05-16
Hi
Don't quite understand what you mean by "no desktop environment, only default x init session", but having it log you in automatically is a breeze. 
Open "Login Window" available under the menu "System / Administration" and then click the tab "Security".
Here you can choose which user should be logged on automatically, or after a certain amount of time.

/N

---

### Post by bveb on 2007-05-16
I dont want  gnome. I only want failsafe terminal session. Also no need for login screen. But I dont want terminal window visible. Also I want to change background color.

---

### Post by eentonig on 2007-05-16
Maybe it's going to be a lot easier to understand if you told us what you want. And how you want to use it.

If you just want a CLI interface, just disble GDM for starting at boot.

---

### Post by bveb on 2007-05-16
I just only want to configure my pc as media center. I dont want gnome at startup. I will boot my pc and immediately my TV program starts. I dont want any login screen or gnome desktop environment... Pure X with initially started programs is enough for me.

---

### Post by Viskovitz on 2007-05-16
What about using fluxbox? It loads in a second and can be easily configured to do what you want. Plus, you can't still use your PC for anything else.

---

### Post by mrazster on 2007-05-16
Or just do a "server install" of ubuntu...that way you don't get any "Desktop Enviroment"...just commandline.

---

### Post by Ptero-4 on 2007-05-16
get yourself openbox. IT doesn´t have toolbar and to have X start directly (w/o affecting Xterms) you can use a conditional statement (an if instruction block) using the != (doesn´t match) XTERM to tell bash that if the shell isn´t a xterm then it will run startx (to run X) and you just put your TV apps plus openbox in the xinitrc.

---

### Post by bveb on 2007-05-17
> **Ptero-4 said:**
> ....IT doesn´t have toolbar and to have X start directly (w/o affecting Xterms) you can use a conditional statement (an if instruction block) using the != (doesn´t match) XTERM to tell bash.....


Where is this statement? in xinitrc?

---

### Post by Ptero-4 on 2007-05-18
It is put in the bash login file (I don´t know that much about bash scripting but I know enough to know that bash support conditional statements.

---

