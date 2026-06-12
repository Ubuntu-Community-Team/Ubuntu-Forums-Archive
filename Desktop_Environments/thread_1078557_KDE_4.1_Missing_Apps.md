---
title: "KDE 4.1 Missing Apps"
date: 2009-02-23
forum: Desktop Environments
---

### Post by snorkytheweasel on 2009-02-23
I installed Intrepid Server - x86-64. My first action was to install KDE (4.1). 

I have used desktop since 6.x, server since 7.x, so I think I have a good idea of what should be available. I am surprised at all of the functionality that isn't immediately available. I can't tell if KDE is the problem, or if Intrepid is the source of this bizarre behavior. I'm asking these dumb questions because
[LIST]
[*]the help system sucks (look up 'terminal' or 'shell' and then find instructions on how to launch a terminal window ... or shell )
[*]the set of applications available is bizarre - very little of what is available is useful (widgets for network admin??), and very little of what is available is useful for server/network admin ... there isn't a file system browser or web browser)
[/LIST]

Anti-flame war disclosure:
[LIST]
[*]I'm not interested in a quarrel over whether or not I should be using a GUI with server. However, I am open to Gnome vs KDE for this environment.
[*]If the answers were obvious (to me) I wouldn't be asking.
[/LIST]
[B][SIZE="3"][COLOR="Red"]
Dumb Question #1: How do I open a Terminal Window?[/COLOR][/SIZE][/B]

I should be able to open a terminal from the desktop. From there I can install the many other missing programs (or install a front-end for apt) and manage the system.

Note: this is cross-posted in the x86-64 forum

---

### Post by SuperSonic4 on 2009-02-23
You'd need to install konsole or use one of the tty

```
sudo apt-get install konsole
```

---

### Post by snorkytheweasel on 2009-02-23
> **SuperSonic4 said:**
> You'd need to install konsole or use one of the tty

```
sudo apt-get install konsole
```

The problem is that the machine boots to a KDE logon screen. My installation of KDE has no way (that I can find) to be able to execute that command.

---

### Post by snorkytheweasel on 2009-02-24
The correct answer is

CTRL + ALT + F1

Now I can use apt-get to install putty (my preferred console) and synaptic.

Everything else will flow from those two installations.

---

