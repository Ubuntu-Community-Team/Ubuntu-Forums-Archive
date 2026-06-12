---
title: "Setting PATH in bashrc"
date: 2006-10-02
forum: Desktop Environments
---

### Post by javarunner on 2006-10-02
I cannot seem to get write access to bashrc so that I can add some PATH info.  I sudo to change permissions to write, but when I open up bashrc in the text editor, I do not have sufficient permission to save my changes.
What am I missing?
TIA...

---

### Post by taurus on 2006-10-02
Are you talking about /etc/bashrc???

```
sudo nano /etc/bashrc
```

---

### Post by javarunner on 2006-10-02
As you can tell I'm a Linux newbie.  First, in the etc directory there is a file called bash.bashrc.  Second, when I enter the sudo command you suggested I get an edit window with none of the file content visible.  I'm guessing that's the result of the nano argument on the cmd line.  So, I guess that I need to know how to enter and save changes after entering my stuff.  All I need to do is set the PATH to point to my Java directory, so that I can start Tomcat or JBoss or whatever.  It doesn't matter if this PATH applies to all users, or just myself since it's my laptop I'm using and I am the only user.  Is there a way to also set environment variables as in Windows.  EG: JAVA_HOME
Thanks for your help...

---

### Post by taurus on 2006-10-02
Did you run it with a filename at the end?

```
sudo nano /etc/bash.bashrc
```
If you want to edit it, use the arrow keys to move around and when you are done, <Ctrl>x to save and exit it!!!

Otherwise, you can modify your own .bashrc, ~/.bashrc, and add the path where java is...

```
gedit ~/.bashrc
```
Add these two lines to the end of it if you don't have it in ~/.bashrc...

```

PATH=$PATH:/path_to_where_java_is/bin
export PATH

```

p.s.  ~/.bashrc mean .bashrc in your home directory, ~...

---

### Post by arkangel on 2006-10-02
if you wnt to set a global  path  you have to do it  in /etc/environment
$ sudo  gedit  /etc/environment   , or nano if you like

if you want to set the path any time you open a console ,  as a setting only for you  
$ gedit ~/.bashrc

---

