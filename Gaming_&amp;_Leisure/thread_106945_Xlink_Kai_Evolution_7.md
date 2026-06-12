---
title: "Xlink Kai Evolution 7"
date: 2005-12-21
forum: Gaming &amp; Leisure
---

### Post by iAlta on 2005-12-21
Can I use Xlink Kai Evolution 7 on Ubuntu, it supports Linux.
I donn't wanna know HOW(well.. not yet, since I don't have a wireless broadband to my PC, and no ad-hoc games to my PSP...yet), but IF.

---

### Post by Samuli on 2006-07-24
Yes you can. :)

---

### Post by darkteckno on 2006-11-09
How??

---

### Post by social debiant on 2007-01-30
check out this link.

[http://www.teamxlink.co.uk/forum/viewtopic.php?t=23134&sid=740d2bf29b817aae11a8e9c712a48896](http://www.teamxlink.co.uk/forum/viewtopic.php?t=23134&sid=740d2bf29b817aae11a8e9c712a48896)

The part about seting up the gui (gkaiui or jkaiui) is not necessary if you run xbmc on your xbox because it will close the pc gui anyway.
basically put the kaid file in /bin and the kaid.conf in the /etc
you should edit kaid.conf to put your xlink id and password in first.

then cd to /bin and type "sudo ./kaid" in terminal to start. 

hope this helps

---

### Post by Uranium235 on 2007-06-03
I've got kaid in the bin folder, and kaid.conf in /etc, but I'm getting a UI socket error.

> code:

KAID: Kai Engine for Linux is initialising...
WARNING: Unable to open engine persist data file (/tmp/kaiEnginePersist.txt)
KAID: Kai Engine for Linux is starting...
THREAD: Engine thread started...
KAID: Failed to create UI socket...

is this meaning I need to forward the ports?

---

### Post by q_dmc12 on 2007-10-27
I hate to be a pest as I am not using ubuntu, however I am using fedora core 5 I have accomplished the following flawlessly - my question is what do I do now? No GUI pops-up and the only thing I get in the linux box is:

[root@localhost bin]# ./kaid
KAID: Kai Engine for Linux is initialising...
WARNING: Unable to open engine persist data file (/tmp/kaiEnginePersist.txt)
KAID: Kai Engine for Linux is starting...
THREAD: Engine thread started...
THREAD: Packet sniffing thread started...
THREAD: Orbital stream thread started...
THREAD: Datagram server thread started...
KAID: Kai Engine for Linux has started...

Heh, I just noticed that warning:oops:

---

### Post by archman on 2009-01-14
can someone help here?
i'm using kaid-7.0.0.7 engine
i start ./kaid with sudo and engine starts successfully
print:

KAID: Kai Engine for Linux is initialising...
WARNING: Unable to open engine persist data file (/tmp/kaiEnginePersist.txt)
KAID: Kai Engine for Linux is starting...
THREAD: Engine thread started...

and then i start jkaiui with java -jar jkaiuixxx.jar in other terminal.
print:

KAID: Kai Engine for Linux is initialising...
WARNING: Unable to open engine persist data file (/tmp/kaiEnginePersist.txt)
KAID: Kai Engine for Linux is starting...
THREAD: Engine thread started...
THREAD: Packet sniffing thread started...
THREAD: Orbital stream thread started...
THREAD: Datagram server thread started...
KAID: Kai Engine for Linux has started...
UI: UI Attached...
ORBSTREAM: Orbital stream established...

but then in the application when in arena mode my ping doesn't show up.
It keeps on saying 'Establishing link'

i'm on gutsy and trying to connect it with psp btw...

thanks!

---

### Post by archman on 2009-05-10
Anyone on ubuntu and having kai working willing to try Wipeout Pure or some other game with me, so that I see if I got it all working?
It recognizes my PSP (in browser), seems like I did everything working except that ping still won't show...

So, anyone interested, please PM me. :)

---

### Post by RealG187 on 2009-11-04
Can you use Kai with the XBox 360?

---

### Post by 5nak3 on 2009-11-05
technically you can, but because of the ping limitations the 360 have introduced to the xbox platform you have to live very very very close to your opponent making many games unplayable and essentially forcing you onto the xbox live system if you want real multiplayer online gameplay.

---

### Post by RealG187 on 2009-11-05
Why would you have to be very close to your oponent?

G***** Microsoft, I can't use Live because I don't wanna pay and I have a modded console. If they are going to ban modded consoles then they shouldn't stop them from using other (better) networks...

---

### Post by lanops on 2010-03-05
What is the ping limitation? 20ms, 10ms, more, less?

---

