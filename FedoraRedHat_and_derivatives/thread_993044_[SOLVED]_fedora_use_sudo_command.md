---
title: "[SOLVED] fedora: use sudo command"
date: 2008-11-25
forum: Fedora/RedHat and derivatives
---

### Post by melrokz on 2008-11-25
I am a Ubuntu user for more than a year, and I have recently installed fedora also (multi-boot). 
I've tried sudo but always gives this error:
'user is not in the sudoers file. This incident will be reported.'
I then used 'new login' to login as root and tried 'visudo' to edit the sudoers file.
Please tell me how to edit this file and how to save it as it opens for editing in the terminal.

---

### Post by taurus on 2008-11-25
With Fedora, you have a password for root (created when you installed it) so if you need to become root, just open a terminal and run

```
su -
<Enter root password>
```

---

### Post by __Ryan__ on 2008-11-25
I have a writeup on that [here]("http://www.wiredrevolution.com/commands/submit-commands-as-root-with-sudo"):

---

### Post by LowSky on 2008-11-25
I like how you included the commmand for running as another user for sudo, very helpfull for people who want to use multiple accounts with no sudo access.

---

### Post by melrokz on 2008-11-25
How to use the editor that opens the sudoers file when we type visudo?

---

### Post by __Ryan__ on 2008-11-25
The editor is nano.  Just type in the changes and press Ctrl+x to exit and save the changes.

---

### Post by sisco311 on 2008-11-25
you can change the default editor:

kde:
```
VISUAL=kate visudo
```
gnome:
```
VISUAL=gedit visudo
```
xfce:
```
VISUAL=mousepad visudo
```

terminal:
```
EDITOR=nano visudo
```
in nano press Ctrl+o Enter to save the file and Ctrl+x to exit.

---

