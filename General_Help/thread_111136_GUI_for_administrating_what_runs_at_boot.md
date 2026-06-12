---
title: "GUI for administrating what runs at boot"
date: 2006-01-01
forum: General Help
---

### Post by kwaanens on 2006-01-01
I remember Fedora has some tool like this, where you get a list of available apps that will run on boottime. I wish I knew the name and hope there's an installation candidate for Ubuntu. (And, a tool like this is really helpful for beginners, for example to give a sort of overview of what's happening at boottime)

- Ketil

---

### Post by kwaanens on 2006-01-01
Nevermind, found "bum" the boot-up manager. See: [http://www.linuxjournal.com/node/8322/print](http://www.linuxjournal.com/node/8322/print)

---

### Post by kwaanens on 2006-01-01
Sorry for this many posts...
Bum really doesn't take care of my problem. If I go advanced there is still a lot I would like to change, but can't.
Specifically, my computer is a laptop. When I'm at home, I'm using a wireless network connection and the boot process goes all fine. When I'm at my parents' house I have to plug in a cable to get online. When booting with cable the boot process hangs for a long time on what I'm assuming is "networking". I use network-manager, and would like to try if networking is necessary when I use that. Well, is it? And if it isn't necessary, how do I shut it down, to not run at boot?
Also, I know that NetworkManager runs at boot, but it's not listed anywhere in bum.

On this aspect, I actually miss Fedora :( , system-config-services is a great app 


- Ketil

---

### Post by kaamos on 2006-01-01
A quick solution: When the boot up process tries to wake up network interfaces you don't need, just press ctrl+c. At least gets rid of the waiting.

---

### Post by kwaanens on 2006-01-01
I know, I've been doing that for two weeks, and it sucks in the long run :)

- Ketil

---

### Post by saltydog on 2006-01-03
[QUOTE=kwaanens]Sorry for this many posts...
Bum really doesn't take care of my problem. If I go advanced there is still a lot I would like to change, but can't.
Specifically, my computer is a laptop. When I'm at home, I'm using a wireless network connection and the boot process goes all fine. When I'm at my parents' house I have to plug in a cable to get online. When booting with cable the boot process hangs for a long time on what I'm assuming is "networking". I use network-manager, and would like to try if networking is necessary when I use that. Well, is it? And if it isn't necessary, how do I shut it down, to not run at boot?
Also, I know that NetworkManager runs at boot, but it's not listed anywhere in bum.

On this aspect, I actually miss Fedora :( , system-config-services is a great app 


- Ketil[/QUOTE]


The only init scripts that BUM will not let you edit, are those in rcS.d, because, as the notice says, those are very system-critical and a safe GUI tool won't let you manage those scritps.
All the other runlevel init scritps can be started/stopped by BUM.
The reason why you can't find NetworkManager, is because it is not an init service started at a specific runlevel, but it is an applet managed by dbus and hal.

If you want to play with rcS.d init scripts, there is a text-tool for "experts", sysv-rc-conf. Just apt-get it, and with BUM and sysv-rc-conf you will not miss Fedora anymore.

I am using NetworkManager too (Dapper) and my laptop is not hanging on networking services at boot. If I am linked on a cable, it connects to the cable network.

---

### Post by hans796 on 2006-01-03
[QUOTE=kwaanens]I remember Fedora has some tool like this, where you get a list of available apps that will run on boottime. I wish I knew the name and hope there's an installation candidate for Ubuntu. (And, a tool like this is really helpful for beginners, for example to give a sort of overview of what's happening at boottime)

- Ketil[/QUOTE]
This is surely what you and I been looking for!

[http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf)

It helped me a lot and speeded up boot quite a bit.

---

