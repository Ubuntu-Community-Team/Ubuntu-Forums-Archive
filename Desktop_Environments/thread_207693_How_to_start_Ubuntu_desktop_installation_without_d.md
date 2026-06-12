---
title: "How to start Ubuntu desktop installation without desktop??"
date: 2006-07-02
forum: Desktop Environments
---

### Post by AlliumPorrum on 2006-07-02
Hi,

could some please tell me how can I prevent Ubuntu from loading the Gnome desktop? I would like it to start to the console mode by default, and then if I need the desktop, I could start it from there.

---

### Post by Raistlin355 on 2006-07-02
[QUOTE=AlliumPorrum]Hi,

could some please tell me how can I prevent Ubuntu from loading the Gnome desktop? I would like it to start to the console mode by default, and then if I need the desktop, I could start it from there.[/QUOTE]

You need to change the runlevel in /etc/initab

---

### Post by Delkster on 2006-07-02
From System -> Administration -> Services, disable gdm (and kdm and other possible graphical login managers).

Edit:
Looks like merely unchecking the gdm box actually shuts down GDM immediately, terminating the graphical session. Perhaps doing it that way isn't such a good idea after all. ;-)

---

### Post by AlliumPorrum on 2006-07-02
I have nowthis in my inittab:

---------
#The default runlevel
id:2:initdefault:
----------

So what should I write there to disable Gnome??

---

### Post by pzonik on 2006-07-02
[QUOTE=AlliumPorrum]Hi,

could some please tell me how can I prevent Ubuntu from loading the Gnome desktop? I would like it to start to the console mode by default, and then if I need the desktop, I could start it from there.[/QUOTE]

Did you mean - installation or usage ?

If installation you have to use server mode.

1) boot cd/dvd 
2) type 'server'
3) after installation take of # from respositores (/etc/apt/spurces.list)
4) type 'sudo apt-get update' than 'sudo apt-get upgrade'
5) 'reboot'

You have ubuntu without desktop, but you can install desktop if you wan't:

6) for example: XFCe 
sudo apt-get install xubuntu-desktop
or (light version)
sudo apt-get install x-window-system-core xfce4

---

### Post by AlliumPorrum on 2006-07-02
I meant usage. I'm going to use my laptop mainly as a server, but I also need desktop every now and then. That's why I installed desktop version.

Now I have being trying to find out which is the correct runlevel to start ubuntu only to CLI, but it seems that everybody is guessing different values...?? So could some tell me what's the correct runlevel??

---

### Post by kinematic on 2006-07-02
init 3 is the correct runlevel you want....that boots you into the shell.
just don't use init 6....that puts you into an endless reboot cycle ;)

---

### Post by AlliumPorrum on 2006-07-02
That did it, thank you. I also found out that I need to this to make the change work:

 sudo chmod 444 /etc/rc3.d/S*gdm

No more GUI! ;=)

---

### Post by frafu on 2006-07-27
I cancelled my question as it went a bit beyond the topic...

---

