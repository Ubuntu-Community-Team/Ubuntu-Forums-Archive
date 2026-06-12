---
title: "ubuntu doing a Windows...pls help me, lots of problems"
date: 2005-10-10
forum: Desktop Environments
---

### Post by iakudi on 2005-10-10
Hi,

Can someone please help me (I feel screaming or crying or both!) ??? Up until early this evening my Ubuntu (I somehow upgraded to 5,10) was working fine, I have been trying to configure my tablet (Acer C110) to read my wacom pen etc., I madea few changes listed below:

1) Updates xorg.conf - added pen details, modified keyboard/mouse entries, I do have lots of old configurations hashed out.
2) I created a serial.conf file and added the line            /dev/ttyS0 port 0x06f8 irq 6 autoconfigure
3) I installed gok and de-installed it (I thought this might be the reason)
4) I did a SMART update from synaptic, it updated a lot of things, but the only message I remember with distinction is it saying that xorg.conf had been modified so it would update it.

This is about it (as far as I can remember)...

Now I re-start my laptop, X starts up but it waits a few minutes before my login box appears. Once I have logged in and choose KDE, it takes afew more minutes before launching the Redmond login screen (my choice), however I notice that my HDD activity light only blinks rapidly in stutters. There is LONG pause at initilising peripherals and the rest of the messags (restoring panel) grind their way through, Once my desktop appears it does nothing for a few minutes, not even the toolbar appears. After a few more minutes things beging to appear very slowly, all the time my HDD activity light does not blink rapidly as it used to but s

---

### Post by mlomker on 2005-10-10
You might just want to try renaming your ~/.kde folder to something else and allow KDE to create a new one for you.  You'll have to re-do all of your preferences, but it'd serve as a good test to see what's going on.

Ctrl-Alt-F2 and login.

```

sudo killall kdm
cd ~
mv .kde kde
startkde

```

---

### Post by iakudi on 2005-10-11
[QUOTE=mlomker]You might just want to try renaming your ~/.kde folder to something else and allow KDE to create a new one for you.  You'll have to re-do all of your preferences, but it'd serve as a good test to see what's going on.

Ctrl-Alt-F2 and login.

```

sudo killall kdm
cd ~
mv .kde kde
startkde

```[/QUOTE]

Thanks for the info....but I managed to work out that some of my settings in xorg.conf were thr root cause, so I deleted it and re-installed the original version...now its all cool !

---

### Post by BIGtrouble77 on 2005-10-11
A small piece of advice... I've learned that i's very bad to configure xorg.conf more than one thing at a time.  Simply misconfiguring a mouse can result in X not loading, which, imho, is a huge problem.

---

