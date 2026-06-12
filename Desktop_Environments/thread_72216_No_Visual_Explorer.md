---
title: "No Visual Explorer"
date: 2005-10-05
forum: Desktop Environments
---

### Post by merk on 2005-10-05
I installed and upon booting there is a command prompt interface. How do i get the visual version of this OS to start or am i looking at a reinstall?

---

### Post by Ampersand on 2005-10-05
try logging in at the command prompt, then running 'sudo startx' When prompted, enter thje same password that you entered for your login name during the installation.

Did you accept the default settings for the software to be installed during the installation? If not, try entering the command 'sudo apt-get install ubuntu-desktop'.

---

### Post by darkmatter on 2005-10-05
[QUOTE=merk]I installed and upon booting there is a command prompt interface. How do i get the visual version of this OS to start or am i looking at a reinstall?[/QUOTE]

Strange, you should be taken to graphical a login (gdm).

At the prompt, log in (enter your username) and hit enter. next enter your password in the same manner.

Now type
```
 sudo startx
```

and let me know if that takes you to the desktop. (the 'visual version').

If you recieve any errors when trying to log in, please post them here.

If it works, and you are able to log in, then we can begin to help you get a graphical log in up and running.

Hopefully, no reinstall will be required.

Welcome to the Ubuntu Forums.

EDIT: Ampersand beat me to the post.

---

### Post by merk on 2005-10-06
it said

      sudo: startx: command not found

thanks though

---

### Post by darkmatter on 2005-10-06
[QUOTE=merk]it said
sudo: startx: command not found
thanks though[/QUOTE]

Try 
```
startx
``` without sudo.

---

### Post by merk on 2005-10-06
that command was not found either

---

### Post by darkmatter on 2005-10-06
[QUOTE=merk]that command was not found either[/QUOTE]

That should not be. Which OS are you running?

And may I be so bold as to ask which type of installation you did?

---

### Post by merk on 2005-10-06
I'm using ubuntu 4.1

This install worked the first time, but it didn't pick up my mouse. I then wanted to replace it with mandrake which had numerous errors during the install, and failed to boot. Then I went back to this with a new mouse and there are no visuals.

---

### Post by merk on 2005-10-06
i'll try to reinstall maybe i screwed something up major

---

### Post by merk on 2005-10-06
I got it on reinstall. I must not have installed properly

i appreciate the time you two took to help me out

-amkr

---

