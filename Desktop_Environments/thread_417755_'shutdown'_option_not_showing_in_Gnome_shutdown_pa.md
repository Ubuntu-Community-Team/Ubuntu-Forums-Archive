---
title: "'shutdown' option not showing in Gnome shutdown panel?"
date: 2007-04-21
forum: Desktop Environments
---

### Post by hamdodger on 2007-04-21
Anyone have any idea why I would suddenly not be getting the "shutdown" or "restart" options, when using the Gnome log off option in Feisty Fawn?   I get all the other options (i.e Suspend, Hibernate, Log Off, Switch User, etc.) but not Shutdown or Restart.

Any ideas?

---

### Post by rickycodie on 2007-09-12
try here

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/93551](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/93551)

---

### Post by Hilko on 2007-09-18
I have the same problem, since yesterday! The only way I can shutdown my computer is typing ```
$sudo shutdown -h now
``` in a terminal. I very much prefer the button that sits in my panel, but the shutdown and restart options have disapeared.

Any help, please ?

---

### Post by Hilko on 2007-09-18
The above link is indeed the solution. I had to read through to the end to find, so I will post it here.

>  Matt Darcy wrote on 2007-05-20: (permalink)

This bug has been fixed by using the following process.
Go to: System -> Administration -> Login Window

On the Local tab under "Menu Bar" the option "Show Actions menu" has to be enabled.

this resolves the issue on both the shutdown button screen and on the login/gdm screen.

However this is a fix of the symptoms, the problem appears to be either a theme or gdm theme has the ability to change this setting.


Thanks rickycodie and Matt Darcy!

---

### Post by crazyfish666 on 2008-01-04
> **Hilko said:**
> The above link is indeed the solution. I had to read through to the end to find, so I will post it here.

Thanks rickycodie and Matt Darcy!

I don't have a "login window" option under system -> administration what should I do. Also, the background of the dissapearance of the shutdown option is slightly different from the other folks here. A) I am in gutsy and B) it all started when I got my computer working again after [this]("http://ubuntuforums.org/showthread.php?t=653379"). I still boot up to a black terminal-like screen where I log in and then type "startx" in order to get back into a visual interface, this might have something to do with my inability to shutdown. So far the only time I have shut down was after an unrelated malfunction that blacked out my screen.

---

### Post by nealaustin on 2008-01-17
Thanks Hilco I had the same problem in 7.10

---

### Post by cmittle on 2008-01-18
You can log out then when you get to the login screen you should be able to shutdown.

---

### Post by giannis1_86 on 2008-02-03
thank you....i had the same problem.....

---

