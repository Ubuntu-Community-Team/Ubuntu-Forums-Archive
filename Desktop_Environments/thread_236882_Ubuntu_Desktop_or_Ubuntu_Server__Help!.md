---
title: "Ubuntu Desktop or Ubuntu Server?  Help!"
date: 2006-08-15
forum: Desktop Environments
---

### Post by klgsx on 2006-08-15
First I like to said that i am pretty new to the world of linux/ubuntu/Fedora/etc.

A couple of months ago I used ubuntu in one of my laptops.  Things work out very find, I was very pleased in how things work right out of the box.  With in a few days i discovered Automatix and it helped me a great deal in my transition from Micro$oft to linux(ubuntu).

Unfortunally for me, my lapto got stolen and end up buying a new one.  So i came back to ubuntu to download the installation cd and saw that now there are 2 choices: server and desktop.

I have a couple of old pc's laying around my basement and i wanted to get something going with them along with my new laptop.  I come from the world of M$ and do a little of web developemt: asp/html.

So now, after all that bla/bla/bla :-({|=   ...I downloaded the server and the desktop cd's.  Installed, now questions:

1) I installed ubuntu server in one of my old pc but after the istanllation was done, I got no GUI ala "desktop" just a text interface :confused: 

2) In my other pc, I installed the desktop.  Can I run "Apache" in ubuntu  desktop? and does anybody knows a good link to "How-to host asp/html in apache".  [-o< 

3) One of my boxes is currently running Micro$oft Terminal Server.  Is this possible tru ubuntu desktop or server? 

hope i am not taking much of anybody's time

thanks in advance for any response or suggestion.

---

### Post by kaamos on 2006-08-15
Hello!

1) most *nix server are run like that. If you want, you can install the desktop with "sudo apt-get install ubuntu-desktop"

2) sure. just install apache2 with synaptic. Guides can be found for example in howtoforge and wiki.ubuntu.com

---

### Post by kebes on 2006-08-15
> **klgsx said:**
> 1) I installed ubuntu server in one of my old pc but after the istanllation was done, I got no GUI ala "desktop" just a text interface :confused: 

The server version by default does not install a GUI. (It's a server after all!) To install a desktop manager is quite easy, however:
```

sudo aptitude install ubuntu-desktop

```
(You can use "kubuntu-desktop" if you prefer KDE over Gnome... or you can install them both if you like.)

> 2) In my other pc, I installed the desktop.  Can I run "Apache" in ubuntu  desktop? and does anybody knows a good link to "How-to host asp/html in apache".  [-o< 

You can certainly run an apache web-server using the Ubuntu desktop version. Again the installation is pretty simple:
```

sudo aptitude install apache2

```
That's it! You can also use the "Synaptic" graphical package installer (or "Adept" if you are using Kubuntu) to do the installation. Just search for "apache2" (or "apache" if for some reason you prefer the v.1 branch of apache).

I don't know anything about asp, so I can't point you to a good how-to. For apache in general there are lots of guides out there.

> 3) One of my boxes is currently running Micro$oft Terminal Server.  Is this possible tru ubuntu desktop or server? 

Are you looking for a linux equivalent to Microsoft Terminal Server? (like running SSH, SFTP, etc.) or are you wondering about how to have linux systems use Microsoft Terminal Services?


P.S.: Sorry to hear about your laptop being stolen.

---

### Post by klgsx on 2006-08-15
Thanks for the fast response.

I was wondering if is possible to run most of ther server stuff in the desktop version of ubuntu, then why would i even boder downloading/installing the server?

Without going tru the major explaination, can someone give me the 2 minutes story as in what is diferent between ubuntu desktop vs unbutu server?

](*,)

---

### Post by derouge on 2006-08-15
If you're running a server you won't need the fancy desktop environment. Try XFCE or Fluxbox, maybe. They'll eat less resources than Gnome or KDE. 

This link ([http://www.ubuntu.com/server?highlight=%28server%29](http://www.ubuntu.com/server?highlight=%28server%29)) tells a bit about the Server version. It looks like the main difference is that the Server version comes with no ports open (regular Ubuntu might have ports open for the clock, ftp maybe, not sure though) and an automatic tool for setting up a "LAMP" server which is a server using Linux as its OS, Apache, MySQL and PHP. I don't know if you can setup an ASP server using Linux, since it's Microsoft technology. Heh, they kinda tailor everything to their own OS. ;)

---

### Post by kaamos on 2006-08-15
> It looks like the main difference is that the Server version comes with no ports open (regular Ubuntu might have ports open for the clock, ftp maybe, not sure though)

Both come with no ports open. But otherwise you were correct. The versions also come with differently configured kernels (tuned for desktop or server).

---

### Post by David Corrales on 2006-08-15
The server and desktop use the same package base but they install different package configurations by default. So installing the desktop edition is the same as installing the server and then adding the aforementioned meta-packages like **ubuntu-desktop** and switching to a regular 686/K7 kernel.

Personally, I'd use the desktop edition for regular workstations and start with the server cd for pure servers and add a lightweight desktop (like xfce with the package **xubuntu-desktop** for example) later on to use some graphic environment for configuration if you're not comfortable with the CLI (command line interface).

You should also set up a service like webmin on the server so you can configure it remotely from any workstation via a web browser.

---

