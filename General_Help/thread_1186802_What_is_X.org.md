---
title: "What is X.org?"
date: 2009-06-13
forum: General Help
---

### Post by JIMIneitor on 2009-06-13
I mean, I know what it does, but why, does it do it, how and why dont they make a graphic manager or however its called more windows like, not having such a complicated thing at the top of your OS?

Is it really so complicated?

---

### Post by meeples on 2009-06-13
as far as i know ( and im no techy guy), x.org is what makes ur gui. it puts all the pictures on the screen, its in charge of showing where your mouse is etc. its basically whats on your monitor. unless u use a text only interface..

im pretty sure windows uses something similiar, if not, something not quite as good.

---

### Post by ddrichardson on 2009-06-13
Xorg is an implementation of the X Window System and provides a graphical user interface. Really it only provides a framework that other window managers can run on top of.

The modularity this affords however tends to mean improved stability as each window is isolated and shouldn't crash any others (this is not really true of Microsoft Windows, as Explorer allows messages between windows).

Given Linux's usage, the ability to detach the interface from the OS is a real benefit - for example, in server set ups you remove an unnecessary overhead.  On a high end system I can run KDE with compositing and on a netbook I can run Fluxbox but both can run the same applications because they aren't tied to an interface.

X Window's only real critiscism is client/server seperation but for most of us that's not an issue.

---

### Post by JIMIneitor on 2009-06-14
ohh, i see, but i still think is way too complicated

I think Linux should use something like

Kernel   ----]    Driver ------} Gui ------} Apps

:popcorn:    but nevermind, im not a coder or something so i might be wrong, i beg your pardon for my ignorance

---

### Post by jenkinbr on 2009-06-14
```

                                                  / ] APP
                                         / ] GUI <
                                        /         \ ] APP
                                       / 
Kernel ---] Driver ---] X.org server <
                                       \
                                        \         / ] APP
                                         \ ] GUI <
                                                  \ ] APP

```

A bit complex, but the X.org server will allow you to run multiple instances, each with it's own logins and applications running.

---

### Post by iponeverything on 2009-06-14
> **JIMIneitor said:**
> ohh, i see, but i still think is way too complicated

I think Linux should use something like

Kernel   ----]    Driver ------} Gui ------} Apps

:popcorn:    but nevermind, im not a coder or something so i might be wrong, i beg your pardon for my ignorance

This is actually part of Unix design philosophy, that Linux uses. Because of its highly modular design, we can run systems with or without a GUI - with choices like gnome, kde, fluxbox, etc.

It seems more complex initially, but it's actually more difficult to understand monolithic systems like windows. Because you can't break the problem down in to small enough pieces.  With windows, you have a big black box, plug in A in here and a dancing paper clip comes out there. Having things like the graphics subsystem so tightly embedded in the kernel also can decrease stability and efficiency.

---

### Post by tgalati4 on 2009-06-14
You can run your X windows session remotely as I am doing right now.

I am on a powerbook running OS X Tiger, with a workspace running X windows.  In that window I am logged into a Dapper machine, a Gutsy machine, and an Intrepid machine.  Each of these machines can display their graphical applications locally on my mac.

The X windows system was developed in the early 80's and predates Windows, and ethernet.  Presumably named "X" as one step better than the "W" window system. 

It's amazing that such a framework is still in use today. Yes it's complicated, but you can do some cool stuff with it.

---

### Post by JIMIneitor on 2009-06-14
cooool, they say you learn something new everyday
and  today i learned how to sync my ipod touch using linux, how to have different wallpapers for each desktop, many other irrelevant stuff, and another reason why Linux is waaay better than Windoze  :KS

---

