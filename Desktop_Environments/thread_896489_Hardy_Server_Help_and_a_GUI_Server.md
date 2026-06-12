---
title: "Hardy Server Help and a GUI Server"
date: 2008-08-21
forum: Desktop Environments
---

### Post by amarendra on 2008-08-21
am setting up a wireless LAN in my class LAB. around 10-15 comps. We
have got one HP workstation and an IBM Blade server too. However we
shall install Linux server(I have an Ubuntu Hardy Server CD) on the HP
workstation and then network all the systems wireless. We also plan to
enable Internet access and data access from all other computers (and
even from laptops brought students) by using an USER-ID and password
assigned to them.
Any system can access any system's data in the WLAN on the basis of USER
permissions including workstation. Shall we have to make more servers or
all the systems will also have to act as servers for this purpose?
Remember the other systems may have other OSs as well like XP,Vista and
different Linux distros.
Please reply if you can find time, or suggest some useful links(near the
point).
Please at least tell us the task list so that we will search how to do
it from Internet.
i will explain again
i want a GUI for this server. I am a linux newbie. So, I need it. I installed it and after tht I was clueless what to do. I have to install Ubuntu Server on a HP workstation in my college's IT Lab and then network the lab which is already wi-fi. All the systems have wireless cards. first we will try with 2-3 systems only and that HP workstation.
shall i need to put the Gnome or whatever from another source or that is already in the CD and hence is on the Hard disk ..if yes then how?
How shall i know that the wi-fi internet available in the lab is being accessed by the worksstation after that server install?

in such matters a gui will help

---

### Post by pytheas22 on 2008-08-21
The Ubuntu server CD doesn't include a GUI.  If you want Ubuntu with a GUI, your best and easiest option is to burn a desktop-edition CD from [http://www.ubuntu.com/](http://www.ubuntu.com/).

If that's not possible, you could also install with the server CD, and after the install completes, run this command:
```

sudo apt-get install ubuntu-desktop
```

It will download and install the desktop edition for you (alongside the server edition), including Gnome and all the GUI applications.  Keep in mind that if you install using the server edition, you will first have to establish an Internet connection before you can download Gnome; it may be difficult for you to get online if you have little Linux experience and need to connect wirelessly without the assistance of GUI tools.  So I'd highly recommend that you download the desktop edition instead and install that.

Do the students connecting to your server need to have a GUI, or just a command-line?  If they only need a command-line, that's really easy: just create accounts for them on the Linux server, install an ssh server on Ubuntu:
```

sudo apt-get install ssh
```

and then they can connect to the Linux machine with a command like this on Linux or a Mac:
```

ssh username@linux-server-IP-address
```

or on Windows, they can use [Putty]("www.chiark.greenend.org.uk/~sgtatham/putty").

If the students need to access the whole graphical desktop remotely (keep in mind that this will require a lot of bandwidth and will put a heavy load on the server, if you have a dozen people logged in graphically at once), your best option is probably to use [VNC]("https://help.ubuntu.com/community/VNC").

---

