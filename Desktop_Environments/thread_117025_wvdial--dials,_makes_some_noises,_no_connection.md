---
title: "wvdial--dials, makes some noises, no connection"
date: 2006-01-14
forum: Desktop Environments
---

### Post by batholith on 2006-01-14
After finally getting the lucent modem drivers loaded, I thought I had everything ready to go...

I configured wvdial with the following (per the DialupModemHowto):

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Carrier Check = no
Stupid mode = on"From wvdial.conf"
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ"From wvdial.conf"
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Phone = 8724638
Username = rztaylor@tds.net
Password = ****************
```

The modem dials the number, starts receiving the signal (the good ol' modem noises), and then it sits there for about 20-30 seconds and spits out the following:

```
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT8724638
--> Waiting for carrier.
ATDT8724638
CONNECT 45333 NoEC
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jan 13 16:29:46 2006
--> pid of pppd: 15304
--> Using interface ppp0
--> Disconnecting at Fri Jan 13 16:30:11 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


```

I have also been given "exit code+10"...  I've looked up the code meanings in the wvdial manual pages, but it is all beyond my expertise.  I've also tried connecting via gnome-ppp but I get the following message there (slightly different but with the same outcome...it doesn't want to connect):


```
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT8724638
--> Waiting for carrier.
ATM1L3DT8724638
CONNECT 49333 NoEC
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT8724638
--> Waiting for carrier.
NO CARRIER
ATM1L3DT8724638
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Fri Jan 13 16:37:00 200
```

Sorry about the long post, but I need some help!

---

### Post by towsonu2003 on 2006-01-14
[QUOTE=batholith]
```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Carrier Check = no
Stupid mode = on**"From wvdial.conf"**
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ"From wvdial.conf"
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem

```
[/quote]
should have been ```
Stupid Mode = on
``` the stuff in quotes shouldn't be there, as far as I know... Also, if dual booting, can you connect from Windows? also, *if* you got help from linmodems.org mailing list, they might be able to offer some explanation?

---

### Post by batholith on 2006-01-14
Sorry, but the quotes around the "From wvdial" was an artifact of my cut and paste, it's not in my wvdial.conf

I followed the directions from the ubuntu wiki at:
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

not from the linmodem site... but if you think I should turn there I give it a shot.

---

### Post by batholith on 2006-01-14
OK, so nobody seems to want to take up my cause at linmodem.org.  So I'm back here again trying to find some help.

Please.

Pretty please?

---

