---
title: "Administrator password error using GUI"
date: 2006-08-28
forum: Desktop Environments
---

### Post by johnusa on 2006-08-28
I am new to linux.  When I try to perform an administrative task using the GUI, I am prompted for the su password.  After entering the password, I receive a validation error.  I then issue the corresponding command from the shell prompt (such as "synaptic"), I am prompted for the su password.  The password is accepted and the command executes.  The is the same password I entered when I tried to use synaptic using the GUI Administration menu.  I don't know what is wrong.  Can anyone help?

I changed the su password and tried again.  The password is accepted if I entered it at the shell prompt.  But the same password is rejected if I use the GUI.

Thanks in advance for you help!

---

### Post by aysiu on 2006-08-28
From the shell prompt, you just type ```
synaptic
``` and are prompted for a password? That's odd.

What happens when you type ```
gksudo synaptic
``` instead?

---

### Post by johnusa on 2006-08-28
Correction:
If I go to the shell prompt to become su, I enter the same password that I entered via the GUI (System->Administration->Synaptic Package Manager). I then enter "synaptic" at the shell prompt and I get the synaptic package manager.  When using the GUI interface, I get wrong password even though I entered the same password that allows me to become su from the shell prompt.

---

### Post by aysiu on 2006-08-28
With the Ubuntu default installation, you should not be able to *su* to root. Did you create a root user password?

---

### Post by johnusa on 2006-08-28
Yes.  After installation, I created a password for the superuser.

---

### Post by aysiu on 2006-08-28
When you go to System > Administration > Synaptic Package Manager, you're supposed to enter your *user* password, not *root* password. More info here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by johnusa on 2006-08-28
When the dialog asked for the password to do administrative tasks, I was thinking superuser password.  This thread is now closed.

Thanks again for your help!

---

