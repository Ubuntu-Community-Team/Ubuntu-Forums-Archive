---
title: "Administartor mode in Control Centre ?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by lemmi150570 on 2005-04-12
Hi everybody,

How do I use KDE´s Control Centre for system administration? When I hit the Administrator Mode button, I have to enter a password. Entering my default user account password brings me back to the Control Centre front page. The root password is rejected. Logging in as root is not possible (btw a concept that does not make any sense to me).

So is there an alternative to command line administration in Kubuntu?

P.S. sudo KControl simply crashes.

Joachim

---

### Post by bin on 2005-04-13
Hmm this is a bit stupid isn't it - no doubt the answer will surface

In the meantime:-
1. sudo root passwd
- your own password
- new password for root

2. edit /etc/kde3/kdm/kdmrc and change the line AllowRootLogin to =true

You can then login as root.....

in light

bin

---

### Post by lemmi150570 on 2005-04-13
Thanks!

Joachim

---

### Post by vapor on 2005-04-13
When admin mode misbehaves I find deleting the folder /var/tmp/kdecache-<your username> restores functionality.

---

### Post by lemmi150570 on 2005-04-14
That's done the trick!

Thank you!

Joachim

---

### Post by pofadda on 2005-04-17
[QUOTE=bin][snip]
2. edit /etc/kde3/kdm/kdmrc and change the line AllowRootLogin to =true

bin[/QUOTE]

You just gotta know where to look! Thanks.

What about the relevant file for Gnome...?

Pofadda

---

### Post by Dragonfly_X on 2005-04-22
I still have the same problem after doing all the stuff mentioned here.  ](*,)

---

### Post by kubuntuuser on 2005-04-22
I have had the same problems too and it resurfaces every now and again.

I really dont know what causes it but the follwowing seems to work 

sudo apt-get install --reinstall kcontrol

However i dont know whether doing this also makes the ammendments others have outlined above. 


KubuntuUser

---

### Post by Dragonfly_X on 2005-04-22
[QUOTE=kubuntuuser]I have had the same problems too and it resurfaces every now and again.

I really dont know what causes it but the follwowing seems to work 

sudo apt-get install --reinstall kcontrol

However i dont know whether doing this also makes the ammendments others have outlined above. 


KubuntuUser[/QUOTE]


Just tried it and it works as far as enableing the textboxes and buttons. But a new problem came up!

When I enter any new IP address, DNS ect. and click apply "kcmshell" crashes and the new settings are not applied, thus still leaving me without a connection to the net.

---

### Post by segrewb on 2005-04-22
I know this doesn't help fix the issue at hand.  However I have read in another thread that if you install Ubuntu then apt-get install kubuntu-desktop that those people are not having this problem.

A solution, a drastic one, but one none the less.

I personally just delete the kdecache-username and I'm back in business when I run into this problem.  I'm not reinstalling! ;-) 

Segrewb

---

### Post by dreadnought on 2005-04-24
I have loaded Kubuntu Desktop from Ubuntu but still get this problem.
It seems to be a random bug. Hopefully you clever KDE/Ubuntu hackers out there can get to the bottom of it.  :smile:

---

### Post by Dragonfly_X on 2005-04-25
This is a sh*t problem to have, but it's a problem none the less and it must be fixed!

The only problem with doing apt-get install kubuntu-desktop from Ubuntu is that all the Gnome apps still show on the menus in KDE and it causes it to be clutterd and confusing!

---

### Post by kejlbo on 2006-05-02
[QUOTE=vapor]When admin mode misbehaves I find deleting the folder /var/tmp/kdecache-<your username> restores functionality.[/QUOTE]

In the folder /var/tmp/kdecache-<username> there is a file called ksycoca. It is a readonly database which stores system configuration settings.
It is created/updated by ```
kbuildsycoca
```
Running kbuildsycoca from the commandline solved the problem for me.

kbuildsycoca should have been automatically executed by *kded* when changes were made to the configuration, so I guess it must have failed to detect a change.

/emil

---

### Post by aysiu on 2006-05-02
Alt-F2 ```
kdesu kcontrol
```

---

### Post by giaguara on 2006-05-06
Wohoo, removing the kdecache folder helped. I had the same problem. :)

---

