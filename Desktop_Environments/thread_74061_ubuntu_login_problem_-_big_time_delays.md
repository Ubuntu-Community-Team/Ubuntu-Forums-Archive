---
title: "ubuntu login problem - big time delays"
date: 2005-10-10
forum: Desktop Environments
---

### Post by iakudi on 2005-10-10
Hi,  I crashed whilst trying to send my last post (ubuntu doing a Windows...pls help me, lots of problems)

Can someone please help me (I feel screaming or crying or both!) ??? Up until early this evening my Ubuntu (I somehow upgraded to 5,10) was working fine, I have been trying to configure my tablet (Acer C110) to read my wacom pen etc., I madea few changes listed below:

1) Updates xorg.conf - added pen details, modified keyboard/mouse entries, I do have lots of old configurations hashed out.
2) I created a serial.conf file and added the line            /dev/ttyS0 port 0x06f8 irq 6 autoconfigure
3) I installed gok and de-installed it (I thought this might be the reason)
4) I did a SMART update from synaptic, it updated a lot of things, but the only message I remember with distinction is it saying that xorg.conf had been modified so it would update it.

This is about it (as far as I can remember)...

Now I re-start my laptop, X starts up but it waits a few minutes before my login box appears. Once I have logged in and choose KDE, it takes afew more minutes before launching the Redmond login screen (my choice), however I notice that my HDD activity light only blinks rapidly in stutters. There is LONG pause at initilising peripherals and the rest of the messags (restoring panel) grind their way through, Once my desktop appears it does nothing for a few minutes, not even the toolbar appears. After a few more minutes things beging to appear very slowly, all the time my HDD activity light does not blink rapidly as it used to but stops and starts........

This is as bad as my XP partition, until this evening logging in was so sweet and rapid...what can I produce for this forum (logs of sort -how and where are they) from laptop so that someone can help me. If I can get my "speed" back I promise NOT to try anything anymore, just leave the tablet as a laptop (sniff!).

Sorry if this is long, I wanted to make sure everything is ok.

many thanks for you help and patience in reading this.

---

### Post by aysiu on 2005-10-10
I don't know the exact answer to your question, but aren't logs usually stored in the /var/log directory?

---

### Post by iakudi on 2005-10-10
[QUOTE=aysiu]I don't know the exact answer to your question, but aren't logs usually stored in the /var/log directory?[/QUOTE]


I'm just trying to guess here that the logs might have information that makes sense to someone...

Any ideas why the login process takes so log? Why does it pause on the initialising peripherals bit and then "freeze" for a while when my desktop appears? It has never done this before.

---

### Post by HermanAB on 2005-10-10
Hi there,

A slow start is usually caused by a bad network connection.  Check your network setup and ensure that the DNS in /etc/resolv.conf makes sense, then restart and see if it goes any better.  During startup, keep an eye on the log to see where it gets stuck - Ctrl-Alt-F1.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by iakudi on 2005-10-10
[QUOTE=HermanAB]Hi there,

A slow start is usually caused by a bad network connection.  Check your network setup and ensure that the DNS in /etc/resolv.conf makes sense, then restart and see if it goes any better.  During startup, keep an eye on the log to see where it gets stuck - Ctrl-Alt-F1.

[/QUOTE]

How do I get back to the KDE gui after pressing ctl+alt+F1?

I disabled my wireless network and it made no difference,in fact detecting and bringing up my wireless connection is pretty quixk. I saw some error messages regarding Wacom trying to do somethething continually, so I uninstalled wacom, but I am still having problems...

---

### Post by HermanAB on 2005-10-10
You have eight virtual consoles, F1 till F8.

Ctrl-Alt-F7 is the graphical display!

Cheers,

Herman

---

### Post by iakudi on 2005-10-10
Well I think I have solved it, I luckily kept a virgin copy of my xorg.conf, which I have restored...

I dont understand why it had these problems, I simply followed the instructions that a numb of people have established already regarding installing wacom and my tablet pen...

this has taught me not to meddle and try to improve things !!!!

A word of advice ALWAYS back up ORIGINAL copies of files  !!!!!!!!!!!!!!!!

thanks for your help

---

### Post by HermanAB on 2005-10-10
Regarding configuration file backups, see this easy solution:
[http://www.aerospacesoftware.com/rcs-howto.html](http://www.aerospacesoftware.com/rcs-howto.html)

It can save you from a lot of head-aches!

Cheers,

Herman

---

