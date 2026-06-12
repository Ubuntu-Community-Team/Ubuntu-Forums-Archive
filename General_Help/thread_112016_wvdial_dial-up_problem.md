---
title: "wvdial dial-up problem"
date: 2006-01-03
forum: General Help
---

### Post by ivan cherevko on 2006-01-03
Hi!

I have such a problem. When I connect to my ISP through wvdial, there is always some problems: sometimes wvdial does not correctly identify prompts, sometimes starts waiting for prompts only after username query has been already set etc.

is there any way to manually respond to queries and send usernames, passwords etc. by hand?

Thanks.

P.S.: No, I'm not using a winmodem.

---

### Post by ivan cherevko on 2006-01-04
won't anybody help poor soul?

---

### Post by ivan cherevko on 2006-01-04
doesn't anybody want to help me?

---

### Post by nigelo on 2006-01-04
Hi Ivan,
Have you edited the file: wvdial.conf to enter your isp details - I'm guessing you have as you've got online (it gets created when you run in a terminal: wvdialconf). I've had a lot of trouble with dialup - a winmodem didn't help - but since have found out about gnome-ppp (installed from the Ubuntu 5.10 CD using Synaptic) which seems to do all the work with wvdial with a graphical frontend. I needed the "stupid mode" enabled but looking at the logs it's still have trouble negotiating the connection but it is working :-)
hth, nigel

---

### Post by ivan cherevko on 2006-01-04
Thank you, nigelo.

Yes, I did edited wvdial.conf both automatically and by hand, trying almost every option which got listed in man page.

I've installed gnome-ppp too, but when I enter stupid mode in g-ppp, it sends pppd command at the very beginning, and there is no sending of neither username, neither passwords.

---

### Post by nigelo on 2006-01-05
Ivan,

I'm at the limit of my knowledge and am sorry not to be of any more help.
I would expect our g-ppp (wvdial) logs to be similar so here's the first part of mine - I hope it may give you a clue as to what is wrong: 

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT[my ISP's phone number]
--> Waiting for carrier.
ATM1L3DT[my ISP's phone number]
CONNECT 115200 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Jan  5 18:50:29 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> pid of pppd: 10676
--> Using interface ppp0
--> pppd: TZ
[and so it continues with IP addresses etc]

Good luck,

Nigel

---

### Post by ivan cherevko on 2006-01-06
thank you nigel, but problem was in the ISP, so I moved to a more expensive one and things got ok :) But I've got different problem - I can't set up a callback now :(

---

