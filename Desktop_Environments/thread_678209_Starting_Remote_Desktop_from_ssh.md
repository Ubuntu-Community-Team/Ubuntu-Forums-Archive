---
title: "Starting Remote Desktop from ssh"
date: 2008-01-25
forum: Desktop Environments
---

### Post by rashire on 2008-01-25
I've been looking for hours now on how to resolve this so forgive me if the answer is already posted somewhere.

My problem is my ubuntu box restarted and I've been unable to log in remote desktop because i dont have physical access to it right now. Remote desktop has been configured for my username but every attempt I've made to start remote desktop have failed. Through searching I've discovered the proccess is called vino but this has not lead to much progress.

With only ssh running is it possible to either start my vino proccess or to have my account login locally?

---

### Post by borris.morris on 2008-01-25
Try to kill Kdm or Gdm and then do "startx"
You can kill it through "sudo /etc/init.d/kdm stop" or "sudo /etc/init.d/gdm stop"

---

### Post by rashire on 2008-01-25
xauth:  creating new authority file /home/ed/.serverauth.5864
xauth:  creating new authority file /home/ed/.Xauthority
xauth:  creating new authority file /home/ed/.Xauthority

X: user not authorized to run the X server, aborting.
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.
Couldnt get a file descriptor referring to the console

---

### Post by borris.morris on 2008-01-27
sorry, try "sudo startx"

---

### Post by rashire on 2008-01-27
ed@ed-linux:~$ sudo startx
xauth:  creating new authority file /home/ed/.serverauth.5829

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux ed-linux 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 27 13:20:30 2008
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!


Then it just sits there.

When i looked at screen because im at home now, it has a prompt to coninute as privledged user. So i still had to be at the system to click continue. also when it started up it logged me in as root.

i think this is close to a solution, if there a way for my to start as my username, i was logging in shh through my username.

Thanks for all the help so far, this is closest i've come to a solution in hours of looking.

---

### Post by borris.morris on 2008-01-27
Hmmmm.... I know you can tunnel X through ssh... let me google it real quick..
check out this site:
[http://www.cag.lcs.mit.edu/~wentzlaf/faq/ssh_X.html](http://www.cag.lcs.mit.edu/~wentzlaf/faq/ssh_X.html)
Basically, it appears as though you edit the /etc/ssh or what not file and add
ForwardX11 yes

---

### Post by borris.morris on 2008-01-27
scratch that, this site looks wayyyyyyyy better!
[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by PhrankDaChickenGeek on 2008-01-28
You can run the following command through SSH to start Vino (Gnome Remote Desktop)
```
gconftool-2 --set "/desktop/gnome/remote_access/enabled" --type bool TRUE
```

Change other settings through gconf over ssh, see the bottom of this page [http://www.gnome.org/~bmsmith/gconf-docs/C/gnome.html](http://www.gnome.org/~bmsmith/gconf-docs/C/gnome.html)

---

### Post by rashire on 2008-01-31
Thanks for the helps guys I appreciate the responses. I've been a bit busy the last few days between school and work, I should get to testing out these solutions over the weekend, I'll let you know of my success or failure.

---

