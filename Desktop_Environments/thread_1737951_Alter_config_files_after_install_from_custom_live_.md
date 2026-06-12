---
title: "Alter config files after install from custom live cd"
date: 2011-04-24
forum: Desktop Environments
---

### Post by Jagoly on 2011-04-24
Hello. I'm building my own ubuntu variant for low resource systems at the moment. It's based from the ubuntu 10.10 minimal install (12mb iso). It uses openbox as the window manager and SLiM as the login/display manager.

What I would like two know is how to have a few config files that are on the live cd to be altered for the installed system. Specifically, SLiM autologin, but I'll probably find other things to change aswell. Basically a sort of "first boot script".

Thanks for any knowledge.

---

### Post by Paddy Landau on 2011-04-24
Create your system on your hard drive as you want it.

Then use [Remastersys]("http://www.geekconnection.org/remastersys/"). I've never used it, but it is supposed to make an installable copy of your existing system (option 2: a distributable version without your personal data).

Do you know of [Lubuntu]("http://lubuntu.net/")? It is a lightweight flavour of Ubuntu, which may be what you need.

---

### Post by Jagoly on 2011-04-24
No no no. I already have used virtualbox to install ubuntu 10.10 minimal, then install and customise everything I need (x server, xfce terminal emulator, panels, network mangers, office utilities, ect.). Then I have already put that installation onto a live cd fowlowing the guide at [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)
It works very well, it installs too. What I would like to know is if there is a way to difference certain configuration files from the live cd to the installed system. Eg, wether or not SLiM will autologin. Nescecary for the live cd, but not a real installation. Remastersys is good if you don't need full control of everything. Eg, you just want a few extra programs, like gimp.

---

### Post by Paddy Landau on 2011-04-25
I'm sorry, I don't know the answer. My initial thoughts would be to write a script that runs only the very first time the new installation boots. Use something like a file to check whether it has run, and don't run it if it has run already.

Good luck.

---

### Post by Jagoly on 2011-04-25
I suppose that would work. It could alter the autorun file to tell it to stop runnin, and then delete itself. Thankyou :)

---

