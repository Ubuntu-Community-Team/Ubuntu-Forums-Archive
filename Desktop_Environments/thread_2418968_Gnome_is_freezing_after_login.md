---
title: "Gnome is freezing after login"
date: 2019-05-14
forum: Desktop Environments
---

### Post by Bargoth on 2019-05-14
Hello,

I have serious problem with my Ubuntu 18.04 installation, particularly with Gnome.

Some issues were independent from me and some them I have created :(.

1. On 13th of May suddenly my perfectly running Ubuntu for so many years (16.04 --> 18.04) suddenly crashed and it was beginning of disaster.
2. On every attempt to reboot Gnome was unresponsive. HDD was working hard but cursor was not moving and some apps couldn't load. It lasted many hours.
3. After looking on different posts and forums I couldn't find any reasonable solution.
4. I checked logs and found that there was error with dbus-core

[FONT=verdana][SIZE=3]**[SIZE=2]dbus-core: error connecting to system bus: org.freedesktop.DBus.Error.FileNotFound[/SIZE]**

[SIZE=2]5. After looking for different solutions and applying them they didn't solve issue.  

Solutions that I have applied in emergency mode in terminal:


 reinstalling dbus-core, 

[/SIZE]===========================
[/SIZE][/FONT][SIZE=2] [FONT=verdana]sudo apt install dbus-x11[/FONT]
[/SIZE]
[SIZE=2][FONT=verdana]sudo systemd-machine-id-setup[/FONT][/SIZE]

[FONT=verdana][SIZE=3][SIZE=2]export DISPLAY=localhost:0

====================

[/SIZE][/SIZE][/FONT]
[SIZE=2][FONT=verdana]sudo apt purge dbus-user-session[/FONT][/SIZE]
[FONT=verdana][SIZE=3][SIZE=2]sudo apt install dbus-user-session

======================
[/SIZE]
[SIZE=2]And last one which really made me mad :

[FONT=verdana]# apt-get purge dbus[/FONT]

[FONT=verdana]# apt-get install ubuntu-desktop[/FONT][/SIZE][/SIZE][/FONT][FONT=verdana][SIZE=3][SIZE=2][SIZE=3]
it was fine until my laptop couldn't connect to archive.ubuntu.com repository. Before this moment my machine was downloading packages without problems[/SIZE]
[SIZE=3]
So I do not have ubuntu-desktop installed[/SIZE]
[/SIZE]

Please help me with this problem wchich is to complicated for me.

1. How to install ubuntu-desktop from DVD (U 18.04.2) or some solution for accessing [FONT=verdana][SIZE=3]archive.ubuntu.com[/SIZE][/FONT]?

2. I will check after getting back ubuntu-desktop if my Gnome will work normally. If not I will ask for help with dbus-core problem.


Thank you for help
[/SIZE][/FONT]

[FONT=verdana][SIZE=3][SIZE=2]Adrian

Ubuntu 18.04 (Lenovo T520)

[/SIZE][/SIZE][/FONT]

---

### Post by Rubi1200 on 2019-05-16
Hi,

You have good, solid backups of all your important data right?

Have you tried dpkg in advanced mode, in other words letting the system try and repair broken packages?

---

### Post by rsteinmetz70112 on 2019-05-16
Try```
 sudo apt install -f
```
Let us know what happens.

---

