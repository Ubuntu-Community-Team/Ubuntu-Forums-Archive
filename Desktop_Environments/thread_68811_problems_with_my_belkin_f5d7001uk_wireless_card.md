---
title: "problems with my belkin f5d7001uk wireless card"
date: 2005-09-24
forum: Desktop Environments
---

### Post by tmmuk on 2005-09-24
My belkin f5d7001uk wireless card is not recognised by kubuntu 5.04

I installed ndiswrapper-utils which I found in the uninstalled software section in kynaptic. I am guessing that it came on the kubuntu cd and just wasn't installed by default.

after that, I followed the guide here: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

however, I got a few errors and It is still not working:

(copied from a post of mine on linuxquestions.org - see here: [http://www.linuxquestions.org/questions/showthread.php?s=&threadid=338947&perpage=15&pagenumber=4](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=338947&perpage=15&pagenumber=4))


> on my belkin driver cd there were 2 drivers called bcmwl5.inf and bcmwl5a.inf

bcmwl5.inf was bigger (1.2meg instead of 40k) so i used that in the first command

i typed in command:

[QUOTE]

sudo ndiswrapper -i /home/<myusername>/bcmwl5.inf


it gave the following:

> 

Installing bcmwl5
Forcing parameter RadioState|0 to Radiostate|1

that seemed to go ok, until I did this:

> 

sudo modprobe ndiswrapper


and got this:

> FATAL: Error insterting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net
/ndiswrapper/ndiswrapper.ko): Operation not permitted



Then, finally I typed:

> ifup wlan0


and got:

> ifup:failed to open statefile /etc/network/ifstate: Permission denied



Just in case, I tried:

> sudo ifup wlan0


but got:

> Ignoring unknown interface wlan0=wlan0.



it looks as if i dont have enough access priveliges or something, allthought i typed sudo before every command and put in my password when it told me to.

any ideas?

EDIT: i also tried with the driver bcmwl5a.inf, as well as a combination of both, but it still doesn't work.[/QUOTE]


can anyone here help me? I couldn't get a solution from linuxquestions and someone sent me here.

---

### Post by GeneralZod on 2005-09-24
```

 FATAL: Error insterting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net
/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

That's going to prevent it from working quite nicely :)

Are you 100% positive you did 

```

sudo modprobe ndiswrapper

```

The "sudo" (plus entering your password if prompted) are critical.

Edit:

```

 ifup wlan0

```

You'd definitely need a sudo here, too (which I see you tried later on).  But in nay case, it won't work until the "sudo modprobe ndiswrapper" has been executed successfully :)

---

### Post by tmmuk on 2005-09-24
I did do sudo modprobe ndiswrapper, as I said above but it didnt work

---

### Post by GeneralZod on 2005-09-24
[QUOTE=tmmuk]I did do sudo modprobe ndiswrapper, as I said above but it didnt work[/QUOTE]

Did it ask you for a password?

---

### Post by tmmuk on 2005-09-24
no

Edit: even when I when into Run Command... and selected run in terminal window and run as root (and i put in the password) as well as putting sudo before I still got the error

---

### Post by tmmuk on 2005-09-25
so any ideas?

EDIT: got it working now using a bcmwl5a driver from dell

(see list of supported devices on ndiswrapper (f5d7001))

---

### Post by tmmuk on 2005-09-29
It actually now seems it isnt working
after a reboot, kwifi manager doesnt think there is an interface
after typing sudo modprobe ndiswrapper, Kwifi manager finds the interface and everything looks good. however, when I scan for networks it finds none even though there is an access point within 3 metres that other pcs have had no trouble connecting to. also, the lights on the back of the card do not light up

when I go into control center, and click Internet & Network>Wireless Network, everything is greyed out. when I click administrator mode, it says loading for about 5 seconds then goes to the main Internet & Network menu. The same happens for Internet & Network>Network Settings


can anyone help?

ps - i am using the dell driver found in the list of supported devices and their drivers on the ndiswrapper website

EDIT: I managed to get into the administrator mode by first doing sudo kcontrol, now what do I need to configure to get into my network?

---

### Post by tmmuk on 2005-10-03
so any answers?

---

