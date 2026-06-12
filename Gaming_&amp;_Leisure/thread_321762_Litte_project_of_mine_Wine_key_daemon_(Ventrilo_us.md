---
title: "Litte project of mine: Wine key daemon (Ventrilo users, look here)"
date: 2006-12-19
forum: Gaming &amp; Leisure
---

### Post by blueCommand on 2006-12-19
Greetings!

A couple of days ago I got really really annoyed with the push-to-talk feature in Ventrilo while running Wine.
For those who doesn't know about it, it doesn't work if you don't have another wine app focused which is very unlikely if you're like me and only use Ventrilo and rest native.

"Very well" I thought, "Let's solve this".
My solution might not be the best, but it's really cool in my oppinion. What it does is that it provides a CLI to the keybd_event API for Wine, which sends events that a key was pressed.
It even supports autofocusing a window when the key is pressed :cool: 

This works splendid with xbindkeys which will make it work like a charm with little (almost none) stuck keys and very low latency, which brings me to the other point. Sockets

Since I'm on x64 platform, wine runs under 32-bit chroot which xbindkeys didn't. So I simply made it a server-client architecture with UNIX sockets in /tmp/winekeyd-uid.

I leave no garantues but it works very well for me so I thought I would share it. It's not built so you will need the dev packages as well as libsocket++. Sorry for the hassle but debs seems to be a pita to make with my wierd chroot setup.

Download source here:
socket++ - [http://www.linuxhacker.at/socketxx](http://www.linuxhacker.at/socketxx)
winekeyd-0.2 - [http://blue.cmd.nu/pkg/winekeyd-0.2.tar.bz2](http://blue.cmd.nu/pkg/winekeyd-0.2.tar.bz2)

Deb: [http://blue.cmd.nu/pkg/](http://blue.cmd.nu/pkg/)

Happy compiling!

---

### Post by hikaricore on 2006-12-19
This could be a step in the right direction :)  I'll be using this if I ever use vent again lol.

---

### Post by YaseenKriel on 2006-12-20
how exactly do i compile/install your fix, please? really need to use ventrilo.

---

### Post by ins0mniac on 2007-03-06
Great little program but I cant seem to get it to work.

With all due respect (you have much more knowledge as evidenced by the fact you can produce this app) I think you are approaching this from the wrong angle.  You are sending a keyboard event into a fake windows process which then sends a message to the program run in fake windows.

Would it be simpler to build some sort of hotkey that unmutes the mic input in alsa when pressed and restores mute afterwards?  This could have benefits to all games with built in coms, ventrilo and teamspeak.

---

### Post by Cappy on 2007-03-06
I'm not trying to put down this program but I use ventriloctrl and it works for me. 
[http://np1.pp.fi/ventriloctrl/ventriloctrl-0.3.tar.gz](http://np1.pp.fi/ventriloctrl/ventriloctrl-0.3.tar.gz)

---

