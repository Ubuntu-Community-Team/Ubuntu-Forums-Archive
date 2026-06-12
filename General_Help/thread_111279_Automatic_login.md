---
title: "Automatic login"
date: 2006-01-02
forum: General Help
---

### Post by Jammy_Stuff on 2006-01-02
I've got XUbuntu with gdm and I was wondering if there's anything I can do to make it log in with a specified user automatically.

Also, if I wanted vncserver to start automatically, how would I do that?

---

### Post by Sef on 2006-01-02
With GDM to get it to log in correctly:    


>  ... to log in manually, this is how to do it automatically: System ------> Administration -------> Log in Screen Set Up -----> Automatic Log in -------> Click on 'Log in a user on the first boot up.' -------> Scroll down and highlight name to automatically log in -----> Click on Close.

[http://ubuntuforums.org/showthread.php?t=110125&highlight=Log]("http://ubuntuforums.org/showthread.php?t=110125&highlight=Log")

---

### Post by Jammy_Stuff on 2006-01-02
In XUbuntu, there isn't a login screen set up. Anyone know a command line way of doing it?

[Edit: Oops. Found it]

---

### Post by Jammy_Stuff on 2006-01-02
Sorry to bump but how do I get vncviewer to start and run a server when the system automatically logs in?

---

### Post by andreas.dalsgaard on 2006-01-02
To automaticly login with gdm you should use gdm's setup, you can invoke it from a terminal:

```
sudo gdmsetup
```

---

### Post by Integralmannen on 2006-01-04
One little trick when using vnc, and there's no session running, (your not logged in), is by editing the gdm.conf.
I use it whenever i need to login on my computer via vnc. I run ssh and X11 forwarding.

sudo gedit /etc/X11/gdm/gdm.conf

AutomaticLoginEnable=true
AutomaticLogin=<your username>

Then:

sudo /etc/init.d/gdm restart

To restart and login automatically.
Remember to remove your edits after you have restarted...

---

