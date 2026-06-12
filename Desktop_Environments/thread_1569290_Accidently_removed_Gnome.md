---
title: "Accidently removed Gnome"
date: 2010-09-06
forum: Desktop Environments
---

### Post by ecomoney on 2010-09-06
On a friends computer using a wireless internet connection, I accidently removed gnome, the only window manager available on this computer. Now I only get a log in screen, but even entering the correct login details just returns me to the login menu.

Ive managed to get to the command line, and I understand I can do this...

```
sudo apt-get install ubuntu-desktop
```

This should reinstall. Unfotunetely, it seems that the machine (now I am back at home) will not connect through my ethernet connection, so the machine will not connect to the software sources to do this task. Im getting...

```
connecting to gb.archive.ubuntu.com
```

...which times out.

how do I get out of this situation...my friend needs her computer back for tommorow! :sad:

Thanks in advance

---

### Post by ajgreeny on 2010-09-06
Not sure how you could possibly "accidentally remove gnome", but you are on the right lines with what you are trying to do.  However, it may be a lot easier to add ubuntu-desktop back using a wired connection, if you are not doing so at the moment.  Without a gnome system, wireless will certainly be a lot harder to manage.

If you are already using a wired connection, what happens if you try for example the command ```
ping www.google.com
```You may have a connection, but for some reason be unable to connect to that ubuntu archive address.  You can also try ```
ping gb.archive.ubuntu.com
```

---

### Post by xircon on 2010-09-06
All the packages are on the CD, so if you add the cd to your repos:

```
sudo nano /etc/apt/sources.list
```

Or what ever command line editor you have installed instead of nano.

I installed Kubuntu64 and would add this line to top of file:

```
deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted

```

This should do it, but is obviously untested.

---

### Post by xircon on 2010-09-06
Forget the above:

```
sudo apt-cdrom add
```

---

### Post by ecomoney on 2010-09-07
Thanks guys for the quick response. Ive just discovered the CD rom in the computer wont eject! Re-installation of gnome from the web is my only option now (as I cant find a pin!). Im sorry Im unable to test your solution. I did figure out how to fix it myself though...

I have ethernet here, which Ive tried to connect (the last connection was wireless). I have a standard four port ADSL router to which clients connect using DHCP. I tried

```
sudo dhclient3 eth0
```

Which reported I had aquired an i.p. address within the range offered by the router this had failed before, as I didint realise I had a ppxe netbooting server running on another computer on the network, which was answering the DHCP request before the router:redface:

It was then a matter of issuing the command

```
sudo apt-get install ubuntu-desktop
```

and rebooting once the installation had finished. This brought up the familiar Gnome login screen and were back to where we were.

In case your wondering how I managed to uninstall gnome, I was trying to remove pulseaudio so that the sound would work (it keeps creeping back in with the updates). It was my birthday party yesterday so lets just say my head wasnt in full working order either ;)

Thanks for your help anyway guys :D

---

### Post by ajgreeny on 2010-09-07
I've been to birthday parties like that!

I'm glad you're up and running again.

---

