---
title: "Problems running game Crossfire"
date: 2005-06-06
forum: Gaming &amp; Leisure
---

### Post by gusjones on 2005-06-06
Installed all the Crossfire game packages from the Synaptic package manager. (I think from the universe/multiverse repositry) The game won't run when I go into console and run it from there I can see the following:

[B]rob@ubuntu:~$ crossfire
Unable to open /var/log/crossfire/logfile as the logfile - will use stderr instead
Welcome to CrossFire, v1.6.0
Copyright (C) 1994 Mark Wedel.
Copyright (C) 1992 Frank Tore Johansen.
error on bind command: Address already in use
error on bind command
rob@ubuntu:~$
rob@ubuntu:~$[/B]

Can anyone help me get this game running? I'm not a complete newbie but it is best to assume so. Managed to get games like Quake 3 and Cube running so far with a bit of trouble shooting, but on this one I'm stuck.

Can anyone help?  :-?

---

### Post by mrastas on 2006-05-11
Hi did you solve this bind problem somehow. I am getting the same result running crossfire in kubuntu dapper drake beta. I installed crossfire packets trought apt-get.

[B]Initialize new client/server data
error on bind command: Address already in use
error on bind command
[/B]

It seems to be something to do with sockets, but that doesnt tell me anything...

---

### Post by lemino on 2006-05-19
Hi, had the samt problem you guys been having. The solution was as simple obvious: you don't start the game with the command "crossfire", but with "gcfclient" (if you have installed the gtk-client). Try that. You might have to modify the command if you're on the X-client. Good luck, see you in the dungeons!

---

### Post by Zyphrexi on 2006-06-26
crossfire starts the server, afaik it starts each time you boot up ubuntu.
if you want to restart it do:
```

sudo killall crossfire
sudo /usr/games/crossfire
```

that'll restart the server if you want to refresh the map (i.e. powerlevelling)

---

