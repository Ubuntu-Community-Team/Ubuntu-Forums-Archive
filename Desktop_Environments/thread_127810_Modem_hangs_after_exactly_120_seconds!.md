---
title: "Modem hangs after exactly 120 seconds!"
date: 2006-02-09
forum: Desktop Environments
---

### Post by alfotis on 2006-02-09
Hi all,

My internet connection is ISDN 64K and my modem is USB Intracom NetMod.

Everytime I connect with wvdial, connects fine but then, after exactly two minutes, pppd dies with error code either 16 or 15 (one day dies with 15, the other with 16!!!!)

Here is my /etc/wvdial.conf. I don't have any .wvdialrc

```

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1
#Init3 =
Area Code =
Phone = 8962407070
Username = my_username
Password =
Ask Password = 1
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 300
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1

```

Plz help! It is extremely annoying, and I know this isn't my ISP's problem because when I reboot Windows, connection works just fine...

---

### Post by alfotis on 2006-02-09
anyone? anything? please??

---

### Post by alfotis on 2006-02-12
anybody?????!!!!!!

---

### Post by Mustard on 2006-02-12
Hmmm..I'd love to jump in and help, but I'm not sure where to start.  Have you looked through your logs for any other error messages?  What is error 15 and 16?  Are they wvdial errors?

---

### Post by alfotis on 2006-02-12
Yes, checked logs. Only thing that says is Modem Hangup ppp died with error code 15 or 16 (which means that they are ppp errors). 
Is my wvdial.conf OK? Is there anyone more user friendly way to connect?

---

### Post by alfotis on 2006-02-12
Here's the wvdial termination...
```
--> Connect time 2.0 minutes.
--> Disconnecting at Sun Feb 12 16:54:33 2006
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
```

and here's /var/log/messages

```
--> Connect time 2.0 minutes.
--> Disconnecting at Sun Feb 12 16:54:33 2006
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
```

---

### Post by alfotis on 2006-02-12
Anyone? Heeeeeelp!!!! Please!

---

### Post by alfotis on 2006-02-13
somebody? even the networking forum doesn't answer. Is this too difficult?

Googling didn't lead anywhere

---

### Post by SQuIDers on 2006-05-07
Yeah... this is a common problem. I have read some topics regarding this problem, and people would usually give some instructions on how to solve it, and the instructions would lead to nowhere in most cases. Note that the problem is not Ubuntu specific (slackware.. etc). Some dude said that he made the modem work on SuSe 8.0. In fact, he said that he just used some SuSe`s wizard to configure his ISDN connection... but for other distribution, that problem (and mine with the same modem [http://ubuntuforums.org/showthread.php?t=130003&highlight=netmod](http://ubuntuforums.org/showthread.php?t=130003&highlight=netmod)) still remains unsolved....

I hope that the Ubuntu community will help solve these two problems with Intracom`s Netmod ISDN modem.

---

### Post by Mustard on 2006-05-07
It might be worth looking to see if a bug report exists for this problem on [http://launchpad.net](http://launchpad.net)  .

---

### Post by SQuIDers on 2006-05-07
Ok, this is weird. I decided to change init2 command to ATB0KAS0 (both channels), and it worked?!?!?

I`m writing this post from ubuntu, and still cant believe that this changed my problem (and will increase my telephone bill ^_^ )

as for the 120 seconds problem, try my vwdial config

```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud  = 115200
Init1 = ATZ
Init2 = ATB0KAS0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
ISDN = 0
Phone = ispphone
Username = yourusername
Password = yourpass
```

---

