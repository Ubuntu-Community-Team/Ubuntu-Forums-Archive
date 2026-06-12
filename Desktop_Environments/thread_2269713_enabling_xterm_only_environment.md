---
title: "enabling xterm only environment"
date: 2015-03-17
forum: Desktop Environments
---

### Post by mistrblank2 on 2015-03-17
I had a previous environment that included two Ubuntu hosts, one as a jump box to administer other Linux/Unix hosts and another that sits as my terminal.  Both have been running 10.04 since April of 2010.  I'm now looking at upgrading because the LTS running out is causing our security administrators to throw a fit for audit purposes.  

Upgrading the Jumpbox hasn't been much of a problem other than I can't stand the desktop and flashback still isn't producing the results that I like, but everything behind the scenes works.

My Terminal system is the huge problem.  I used to just boot this system and log into an Xterm session.  With the Xterm session I would ssh to the Jumbox and then start gnome-session which would consume the native session on the Xterm and give me pretty much all of the performance advantages of running locally but really be over the network and behind firewalls (which my security folks thought was slick).  

There doesn't seem to be an Xterm session only option and I can't seem to find an easy option to turn it back on or a good alternative.

---

### Post by kerry_s on 2015-03-17
the old gnome 2 is now "ubuntu mate" [https://ubuntu-mate.org/](https://ubuntu-mate.org/)

the log in manager is now lightdm, install gdm back on & it should be like the good old days for you.

---

### Post by mistrblank2 on 2015-03-18
I've looked, because this was an upgrade, gdm was left in place so I configured the host to use gdm instead of lightdm.  This alone does not give access to an xterm session. 

I've looked around and found the solution is simple and works for gdm or lightdm:

The solution is derived from: [http://askubuntu.com/a/155198](http://askubuntu.com/a/155198)

[COLOR=#333333][FONT=UbuntuRegular]The login choices are .desktop files in /usr/share/xesssions. The "Recovery Console" is a text file named xterm.desktop with contents[/FONT][/COLOR]
[Desktop Entry]
Encoding=UTF-8
Name=Recovery Console
Comment=Failsafe session with only xterm
Exec=xterm
TryExec=xterm
Icon=
Type=Application





I changed the name of mine from recovery though to just XTerm

As for the other issue, I'm looking at MATE and looking at Cinnamon.  

Thanks for the response.

---

### Post by egeezer on 2015-03-18
If you hate the desktop, just
```
sudo apt-get install xfce4 xfce4-goodies
sudo apt-get update
```
That gives you an Xfce4 desktop with all the rich configuration options Xfce offers, access to all the software Ubuntu had originally, and you don't need to do a big reinstall. In my experience, it works better than MATE.

---

