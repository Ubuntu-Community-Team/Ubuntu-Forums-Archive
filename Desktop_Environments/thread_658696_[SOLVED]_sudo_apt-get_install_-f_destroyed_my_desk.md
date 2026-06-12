---
title: "[SOLVED] sudo apt-get install -f destroyed my desktop"
date: 2008-01-04
forum: Desktop Environments
---

### Post by olsoveasna on 2008-01-04
When I am running update installation, and error of installing dependencies occurred. A message box appeared command to run sudo apt-get install -f in terminal. I followed and it removed corrupted package successfully. But it asked me would I like to continue? I typed y ang then it removed my desktop. Now I cannot log in and using my feisty anymore. Please help!

---

### Post by Zack McCool on 2008-01-04
Which package did it uninstall?

Which distribution are you using?  Ubuntu, Kubuntu, Xubuntu?  Which version?  6.06, 7.04 or 7.10?

If you have the package name, try reinstalling the removed package.  Or, try sudo apt-get install ubuntu-desktop .

---

### Post by olsoveasna on 2008-01-05
I have been using Ubuntu 7.04 Christian Edition. I do not remember the package that it was installing. As I remember it begins with lib?????.deb. Thank you very much for your comment but I have question of how to start terminal even now I cannot see desktop appear. After log in I see only blank screen.

---

### Post by urukrama on 2008-01-05
Try to login at the command line. Boot your computer normally, and when GDM (the login screen appears) press Ctrl+Alt+F1 (or F2, F3). A command line will appear. Login there as you would normally and you'll see the typical command prompt *yourusername@yourcomputer name*. (If for some reason you can't get this far, you could use the 'Recovery Mode' at GRUB; it will then boot into a command line system as root so be very careful what you do -- you can easily mess it up).

Then try reinstalling ubuntu-desktop (If you use the recovery mode leave out the sudo):
> sudo aptitude install ubuntu-desktop

Ubuntu-desktop is a metapackage that pulls in everything that comes default with an ubuntu installation. That should solve the problem. I'm not sure about the CE stuff though. I assume that shouldn't clash with ubuntu-desktop, but I've never used it so I can't confirm.

---

### Post by olsoveasna on 2008-01-06
It seems to be a good solution. I followed what you wrote but unfortunately, it needed internet connection. Actually I'm using dial up internet connection. I don't know how to connect to internet if my computer is being like this. How to do it in offline?

---

### Post by urukrama on 2008-01-06
If you have the installation CD, put that one in, boot your system as I wrote earlier, and use the CD as a source. Make sure that it is mentioned in your sources list, though. To check whether it is included use nano:

> sudo nano -B /etc/apt/sources.list

You shoudl see a line that starts with "deb cdrom:" If there is a # in front of it, remove it. If you have no line like that, you'll have to add the CD to the list. To do so, exit nano (Ctrl + X), and type:

> sudo apt-cdrom add

Your installation CD will then be added to your /etc/apt/sources.list file. Update apt:

> sudo aptitude update

and you can start installing ubuntu-desktop from the CD (it will always first install from the CD, and only go to an online repo if the package is not on the CD. Ubuntu-desktop is on the CD).

Hope this helps.

---

### Post by olsoveasna on 2008-01-09
Thank Urukarma. Now I am enjoying my ubuntu agian. I wrote this reply on it. :)

---

