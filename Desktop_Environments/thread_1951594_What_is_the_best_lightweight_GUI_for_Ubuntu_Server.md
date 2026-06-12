---
title: "What is the best lightweight GUI for Ubuntu Server?"
date: 2012-04-02
forum: Desktop Environments
---

### Post by roffisserver on 2012-04-02
I have a server and want to install a GUI but I don't know which one I should get. Could  someone help me?:confused::confused::confused::confused::confused:

---

### Post by snowpine on 2012-04-02
Servers don't usually have a GUI.

But if you want one, I recommend using whichever is your favorite. If you don't have a favorite, you can visit the Ubuntu, Kubuntu, Xubuntu, Lubuntu websites and look at the screenshots to see if you prefer Unity, KDE, Xfce, or LXDE.

Lubuntu/LXDE is the most "lightweight" of the four, but I'll leave it to you to decide whether it's the "best" for your needs. :)

---

### Post by roffisserver on 2012-04-02
Thanks you really helped!

---

### Post by 3Miro on 2012-04-02
If you want to go really light-weight, you can check how to run a standalone Windows Manager (i.e. OpenBox or IceWM). Other than that, LXDE is probably the lightest. XFCE is almost as light, but it has more features and in my experience is more stable. Then Gnome and KDE are not light at all (compared to the others, otherwise they are OK).

---

### Post by 1clue on 2012-04-02
webmin.

There's really no reason for a window manager on a typical server.

---

### Post by roffisserver on 2012-04-02
I was checking out webmin earlier. It seemed pretty good!

---

### Post by 1clue on 2012-04-02
Webmin only gets better with age.

Nearly any service which is normally put on a Linux headless server can be easily configured with webmin.  The exceptions are IMO either not in common use or are commercial applications.

My only issue with it is that Debian (and therefore Ubuntu) doesn't like it very much, and keeps removing it from the distro at inopportune times.

I used to think it was a problem with a license, but it's not.  It evidently "touches" a whole lot of configuration files during installation of the software, and the guys who write standards like Sarbaines Oxley don't like that.  They consider it a security hole for that reason, and none other AFAICT.  Considering that its purpose is to write to configuration files for the entire system, I think that is incredibly stupid.

Long story short, your very best configuration tool for a Linux server is the command line, the next best is something like Webmin.

---

### Post by roffisserver on 2012-04-02
But I really want to manage it from another computer. How can I do that with command line?

---

### Post by snowpine on 2012-04-02
> **roffisserver said:**
> But I really want to manage it from another computer. How can I do that with command line?

Ubuntu Server Guide is a good place to start. :)

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

In particular check out Chapter 5 about openssh.

---

### Post by roffisserver on 2012-04-02
Thanks, I think I will use SSH with terminal and the Putty client.

---

### Post by snowpine on 2012-04-02
> **roffisserver said:**
> Thanks, I think I will use SSH with terminal and the Putty client.

Good choice! See ya next question. :)

---

### Post by 1clue on 2012-04-03
If you plan this server to be in public space (reachable from the Internet without a VPN) -- or even if you're not -- then you might consider going through the security basics on the wiki.

The reason there's no GUI on Ubuntu Server is because it's entirely unnecessary on Linux.  I've had far more headless Linux installs (with no keyboard, monitor or mouse) than I've had with.

FWIW though, if you have anyone who isn't dedicated to the idea of command line Linux, then it might be a good idea to use webmin or similar.  People are used to web-based interfaces to configure home routers and such, but many will balk at a command line.

---

### Post by markbl on 2012-04-04
> **roffisserver said:**
> Thanks, I think I will use SSH with terminal and the Putty client.
There is one more tool which is really handy to know about when working/administering remotely in an ssh terminal window. That is gnu screen (or tmux which is the new alternative). screen or tmux gives you multiple virtual consoles which you can switch between within the one physical terminal session/window. Every experienced linux developer/administrator uses, or at least knows about, gnu screen. It is the terminal user's "gui".

---

