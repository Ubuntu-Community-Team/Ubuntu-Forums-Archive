---
title: "How to run ubuntu without a desktop environment"
date: 2011-10-10
forum: Desktop Environments
---

### Post by kokomodrums on 2011-10-10
Disclaimer: I've tried searching for this probably popular topic, but no specific instructions...

I want to run Ubuntu without any desktop environment, but I would like a window manager still. I'm looking for the simplest way to do this. I'm downloading the 11.04 alternate cd now, I figured installing just the command line version would be the way, then just installing a window manager separately.

I tried 11.04 but didn't like unity, and didn't want to mess with uninstalling all that.

Then I tried xubuntu 10.10 but had issues with hardware compatibility, somehow, and was too lazy to fix it.

So I'm interested in running ubuntu again but without unity or any desktop environment. Should I stick with 11.04 or is unity still installed even if i just do command line install????

Any suggestions?

---

### Post by snowpine on 2011-10-10
You are on the right track. This tutorial shows how to install a minimal system with icewm. You can substitute the windows manager of your choice for icewm.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by kokomodrums on 2011-10-10
Ok, so I need the minimal cd.

If I choose 11.04, does it include unity in some way? I know that might be a stupid question, I just really liked 10.10 but if I'm running a minimal boot I might as well use 11.04, unless 11.04 is THAT different as a minimal install.

What is the standard window manager ubuntu comes with?

---

### Post by snowpine on 2011-10-10
> **kokomodrums said:**
> Ok, so I need the minimal cd.

If I choose 11.04, does it include unity in some way? I know that might be a stupid question, I just really liked 10.10 but if I'm running a minimal boot I might as well use 11.04, unless 11.04 is THAT different as a minimal install.

What is the standard window manager ubuntu comes with?

I think you can also perform a minimal, command-line-only install using the Alternate CD.

The main advantage/disadvantage to 11.04 over 10.10 is that all of the applications will be 6 months newer. Unity won't be installed unless you tell Ubuntu to install it.

There is no "standard" windows manager. You can install whichever one you like (or none at all :)).

---

### Post by fbroce on 2011-10-10
> **snowpine said:**
> I think you can also perform a minimal, command-line-only install using the Alternate CD.

The main advantage/disadvantage to 11.04 over 10.10 is that all of the applications will be 6 months newer. Unity won't be installed unless you tell Ubuntu to install it.

There is no "standard" windows manager. You can install whichever one you like. :)

Why don't you just do a server install? I have 11.10 running just fine.

---

### Post by snowpine on 2011-10-10
> **fbroce said:**
> Why don't you just do a server install? I have 11.10 running just fine.

Ubuntu Server is for servers. Is the OP running a server or a desktop/laptop/netbook?

---

### Post by MG&amp;TL on 2011-10-10
There is no reason why you cannot feasibly run a command-line. Videos, pictures, and the web might be issues, though.

---

### Post by kokomodrums on 2011-10-10
It's a laptop, and I'd like to browse the web, work on text documents and images, etc. Everything I would do on a normal install but without a desktop. And no, not a server, but thanks!

So is Gnome a desktop environment and a window manager all in one? I was under the assumption that there were two separate pieces...

Basically, I don't mind using the command line to open apps and files and etc. (i think it would be cool, actually), but I'd like each program to have a gui. I mean, I need to see webpages and images!

Maybe I just don't understand how this all works???

EDIT: Also, the psychocats guide goes into setting up gnome display manager, is that the desktop environment??

---

### Post by snowpine on 2011-10-10
> **kokomodrums said:**
> So is Gnome a desktop environment and a window manager all in one? I was under the assumption that there were two separate pieces...

Basically, I don't mind using the command line to open apps and files and etc. (i think it would be cool, actually), but I'd like each program to have a gui. I mean, I need to see webpages and images!

Maybe I just don't understand how this all works???

Gnome is a Desktop Environment (DE) and needs a Windows Manager (WM) to run correctly. Typically Gnome uses either Metacity or Compiz as the default WM.

If you are looking for a lightweight alternative to Unity then I recommend either a DE such as Xfce (Xubuntu) or LXDE (Lubuntu) or a stand-alone WM such as icewm, openbox, fluxbox, dwm, etc.

Any of these can be installed in a standard Ubuntu system.  You don't really need to reinstall to benefit from a lightweight DE/WM, and in fact, you can have several installed and choose between them each time you log in. :)

---

### Post by nothingspecial on 2011-10-10
It is possible to view/edit pictures, view videos, webpages etc etc without X.

But you will have to learn a lot.

It is not just a case of install then click.

---

### Post by kokomodrums on 2011-10-10
Ok, so lets say for example I do a fresh command line install with the minimal (or alternate) cd. Now I want to install for example icewm. So I can apt-get install icewm, correct?

What am I looking at now? Do I need to reboot, or do I need to run icewm to get it started? Do I still have icons, or a desktop? Or do I run everything from command line?

Do I have workspaces, or can I configure them separately?

Also, are there any other essential things I need to install? Do any apps like firefox or textedit or etc come with the command line install?

Please excuse me, I'm a newb to the backbones of Linux. Hopefully my post will help direct others newbies out there looking for a similar setup!

---

### Post by snowpine on 2011-10-10
> **kokomodrums said:**
> Ok, so lets say for example I do a fresh command line install with the minimal (or alternate) cd. Now I want to install for example icewm. So I can apt-get install icewm, correct?

What am I looking at now? Do I need to reboot, or do I need to run icewm to get it started? Do I still have icons, or a desktop? Or do I run everything from command line?

Do I have workspaces, or can I configure them separately?

Also, are there any other essential things I need to install? Do any apps like firefox or textedit or etc come with the command line install?

Please excuse me, I'm a newb to the backbones of Linux. Hopefully my post will help direct others newbies out there looking for a similar setup!

The [page I linked to earlier]("http://www.psychocats.net/ubuntu/minimal") has screenshots of exactly what you will see when you log in to your minimal icewm Ubuntu.

---

### Post by MG&amp;TL on 2011-10-10
I've been doing a bit of digging and it seems that:

```
zgv <picture>
and feh <picture>
```will allow you to view images from command-line.

Although I don't have a true console, only a terminal, and zvg broke my Ctrl-All-F1 console. :(

Lynx browser will allow you to view web from command-line. I think.

---

### Post by MG&amp;TL on 2011-10-10
No, things like browsers and text editors will not be there.

```
sudo apt-get install firefox gedit network-manager
```

For instance.

---

### Post by hhh on 2011-10-10
Gnome Display Manager handles the graphical login window and starting X. It's one part of the GNOME environment.
> **kokomodrums said:**
> So is Gnome a desktop environment and a window manager all in one? I was under the assumption that there were two separate pieces...Maybe I just don't understand how this all works???
If you have a minimal install with Natty in sources.list and for example you do... ```
sudo apt-get install gnome-desktop-environment
``` ... you get all the packages listed in this next link with a red or green bullet, plus all the packages those programs require, etc...
[http://packages.ubuntu.com/natty/gnome-desktop-environment](http://packages.ubuntu.com/natty/gnome-desktop-environment)

Instead, you could get more default packages by installing gnome or less packages by installing gnome-core.
[http://packages.ubuntu.com/natty/gnome](http://packages.ubuntu.com/natty/gnome)
[http://packages.ubuntu.com/natty/gnome-core](http://packages.ubuntu.com/natty/gnome-core)

If instead you start minimal and do...```
sudo apt-get install openbox
``` you get a few required libraries, openbox and a default set of openbox themes, and that's it...
[http://packages.ubuntu.com/natty/openbox](http://packages.ubuntu.com/natty/openbox)

obconf, the package that's a GUI for openbox's preferences, doesn't even get installed automatically! You can see how by choosing programs with fewer dependencies than the ones bundled with gnome or kde you can get an "environment" requiring less memory (a nice minimal setup might idle at startup at 70MB memory usage, while a full kde session running effects might be above 400MB).

I'd suggest openbox as a good way to start. It's how I started and there is this excellent guide by forum member urukrama to get you going...
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

These pages are must-sees too...
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://openbox.org/wiki/Help:Getting_started#Using_Openbox_without_a_desktop_environment_.28The_lightweight_approach.29](http://openbox.org/wiki/Help:Getting_started#Using_Openbox_without_a_desktop_environment_.28The_lightweight_approach.29)

Also, Crunchbang Linux uses openbox as it's default window manager and has an active forum...
[http://crunchbanglinux.org/forums/](http://crunchbanglinux.org/forums/)

Hope that helps.

---

### Post by ceti331 on 2011-10-10
> **kokomodrums said:**
> 
I want to run Ubuntu without any desktop environment, but I would like a window manager still. I'm looking for the simplest way to do this. I'm downloading the 11.04 alternate cd now, I figured installing just the command line version would be the way, then just installing a window manager separately.
Any suggestions?

have I understood incorrectly.
From a regular linux install, just sudo apt-get install fluxbox,FVWM or whatever, reboot and select session->fluxbox, and thats what you get.. window manager with no desktop environment, very light.

they'll usually give you a desktop root menu that can launch a terminal. fluxbox can certainly be made to give you startup apps. i usually just setup some hotkeys for launchers

Is there a 'fluxbuntu' ? i've no idea how to go about a custom install setup like this from the outset.

---

### Post by nothingspecial on 2011-10-10
You can view images/videos etc perfectly well without a window manager. Or even X.

[ATTACH]203974[/ATTACH]

---

### Post by snowpine on 2011-10-10
> **ceti331 said:**
> have I understood incorrectly.
From a regular linux install, just sudo apt-get install fluxbox,FVWM or whatever, reboot and select session->fluxbox, and thats what you get.. window manager with no desktop environment, very light.

they'll usually give you a desktop root menu that can launch a terminal. fluxbox can certainly be made to give you startup apps. i usually just setup some hotkeys for launchers

Is there a 'fluxbuntu' ? i've no idea how to go about a custom install setup like this from the outset.

Fluxbox is [one of many]("http://www.techradar.com/news/software/applications/5-of-the-best-lightweight-window-managers-for-linux-972570") good choices! There was indeed a distro called Fluxbuntu but the project fizzled out around 2007, no worries though because you can make your own Fluxbuntu like this:

```
sudo apt-get update
sudo apt-get install xorg xterm gdm fluxbox menu firefox gksu synaptic --no-install-recommends
sudo service gdm start
```

Menus, hotkeys, etc are configured by editing text files in ~/.fluxbox (a hidden folder in your /home) using your favorite text editor (gedit, leafpad, nano, etc).

Here are a few Fluxbox-related links:

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
[http://box-look.org/](http://box-look.org/)
[https://wiki.archlinux.org/index.php/Fluxbox](https://wiki.archlinux.org/index.php/Fluxbox) (not Ubuntu but some good info)

---

### Post by foxmulder881 on 2011-10-11
> **nothingspecial said:**
> It is possible to view/edit pictures, view videos, webpages etc etc without X.

But you will have to learn a lot.

It is not just a case of install then click.

True. But I really don't know why anyone would bother with the amount of trouble involved.

---

