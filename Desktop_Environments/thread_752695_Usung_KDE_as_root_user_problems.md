---
title: "Usung KDE as root user problems"
date: 2008-04-11
forum: Desktop Environments
---

### Post by nerver on 2008-04-11
Hi,

I am a complete Linux noob so there is probably a really easy solution to this that I am missing haha. 
The problem that I am having is that I have installed Ubuntu Gutsy and then I added the KDE desktop as well to try using the package manager. I can login as a normal user ok, but when I login as a root user under KDE i cannot access dolphin, any drives, or settings or menu's at all. No matter what I click on I just get the little bouncing K for a  couple mins and then stops and nothing happens. Is this because of the dual desktop environments installed?

Thank you in advance for helping.
Cheers,
-Sean

---

### Post by undecidable on 2008-04-12
I am surprised you can do it at all - when I try to log in as root (under feisty) I get a msg:
" Root Logins are not Allowed"

Ubuntu is set up to discourage graphical logins by root,
though of course you can change to a tty (Ctrl-alt-F1) and login as root there,
but no gui.  
You can also login as root in a terminal (eg Gnome Termina;) but again no gui.

However sometimes you need to do things as root,
and using command line tools is a pain.
Then simply start the graphical tool as root.
eg if you are in kde and want to start konqueror as root :
either from a terminal, or from alt-F2  type:
 kdesu konqueror

Under gnome the equivalent would be:
  gksudo nautilus

trust this helps.
mc

---

### Post by aysiu on 2008-04-12
There's no reason to log in as root.

Just log in as your regular user, and if you need a root file browser, press Alt-F2 and type ```
kdesu konqueror
``` If you use it a lot, create a launcher or keyboard shortcut for the command.

---

### Post by nerver on 2008-04-12
Thanks for the responses guys. That root file browser will be handy and make it so i do not need to log in as a root. But I'm just curious now about the kde thing. Is it just not possible to do it all? I can log in to Gnome as a root no problem, so it just seems weird to me that I can't do it in KDE (even though there isn't a need to do so).

Cheers :)

---

### Post by kellemes on 2008-04-12
> **nerver said:**
> Thanks for the responses guys. That root file browser will be handy and make it so i do not need to log in as a root. But I'm just curious now about the kde thing. Is it just not possible to do it all? I can log in to Gnome as a root no problem, so it just seems weird to me that I can't do it in KDE (even though there isn't a need to do so).

Cheers :)

A little more info.. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

I actually don't know what KDE's problem is with root.. you'll probably see some terminal-output when starting dolphin from a terminal window. This will shed some light on the issue..

---

### Post by nerver on 2008-04-12
Thanks for the link :)

---

### Post by undecidable on 2008-04-13
sean 

a question:  how are you logging in to Gnome as root?
do you mean from the initial login screen or from a terminal?
(and what vsn of Ubuntu are you running).

mc

---

### Post by onebadpenny on 2008-04-13
I have a related problem. At least I think it's related. I installed kde4 and it works great except that when I load KPackage  it repeatedly asks for my root password. As far as i can tell KPackage is the only app that has this problem. My root pwd works fine with Sudo and the synaptic package manager.

edit: nevermind. I changed the preferred command from su to sudo in preferences and all works great. :p

---

