---
title: "Getting online without having to issue root commands"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jnoreiko on 2005-10-26
I have a USB modem. I can connect with it using [eciadsl]("http://eciadsl.flashtux.org/").
The problem is that eciadsl-start has to be run as root. Every time I start up my PC I have to run a root terminal, enter my password, and find the command in the history. This is pretty much my #1 annoyance with linux. I want to either click a button and connect (like on OS X, where there's a menu bar icon) or have it connect automatically when I ask for a URL (like on windows).

To make this a little simpler, I've tried adding a launcher to my panel, with the command sudo eciadsl-start.
This appears to work, but right at the very end of output (eciadsl produces a lot of messages) I see an error message that I don't have time to read before the terminal window shuts.

Am I going the wrong way about this?
What's the right way?

---

### Post by psychicdragon on 2005-10-26
I've never used eciadsl before but I have a somewhat hackish solution.

Run this command to edit the sudoers file:
```
sudo visudo
```

Add this line:
```
ALL ALL=(root) NOPASSWD: **/path/to/eciadsl-start**
```This makes it so that you can run eciadsl-start as root without entering your password.

Just add 'sudo eciadsl-start &' to your session and it will run automagically when you start Gnome.

---

### Post by jnoreiko on 2005-10-27
I don't always have my modem plugged in, so I'd rather have it as a panel launcher.

I've read the sudoers manual and added this to the sudoers file:

```
joachim ALL=(root) NOPASSWD: /usr/bin/eciadsl-start

```

Clicking the launcher gives an error message about privileges.

---

### Post by eyal_allweil on 2005-10-30
I am in a similiar situation. I want a non-administrator account to be able to go online, but in order to connect I need to run a script which needs root privileges. I, too changed my sudoers file much like jnoreiko, and it didn't work for me, either.

I'm continuing to toy with this, but if anyone knows the correct sudoers entry, it would certainly be nice.

---

### Post by eyal_allweil on 2005-10-30
Ok, I got it to work. The command I used was:

US ALL= NOPASSWD: /usr/sbin/cable-start

where my internet script is in /usr/sbin, and called cable-start, and US is the group containing endusers

Eyal

---

### Post by jnoreiko on 2005-10-31
I'm still getting errors.
This is the end of what I get when I try "eciadsl-start" in a non-root terminal:

> /etc/eciadsl/gs7470_synch03.bin: Permission denied
ERROR eciadsl-synch: failed 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

nice: cannot set priority: Permission denied

---

