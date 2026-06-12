---
title: "TV Tuner Card"
date: 2009-02-20
forum: General Help
---

### Post by usmann on 2009-02-20
Hi guys how are you all

I am usman, new to linux and new to ubuntu i have a tv tuner card
Which i check by the lspci is 

05:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)


Can any one briefly in complete detail that how to install it on Ubuntu version is 8.04

Please Please help me

---

### Post by LowSky on 2009-02-20
what do you mean install, if it is showing up then it is intalled.

If you want to use it try a program called tvtime

---

### Post by usmann on 2009-02-20
> **LowSky said:**
> what do you mean install, if it is showing up then it is intalled.

If you want to use it try a program called tvtime

I Try TVTIME but it does'nt show any thing can any one send me the configurations

---

### Post by wolfen69 on 2009-02-20
see [here]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices").

---

### Post by usmann on 2009-02-20
I also try the following help but it also doesn't work it gives lot of errors like
in the beginning commands
like " rmmod saa7134_alsa saa7134_dvb saa7134 "

[http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux](http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux)

Can any one send me the brief solution how to cofigure the tv card 

Thanks

---

### Post by rbmorse on 2009-02-20
> **usmann said:**
> I Try TVTIME but it does'nt show any thing can any one send me the configurations

Open a terminal window and type:

tvtime

are any errors reported?

---

### Post by usmann on 2009-02-20
> **rbmorse said:**
> Open a terminal window and type:

tvtime

are any errors reported?

usman@us-home:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/usman/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/usman/.tvtime/tvtime.xml: Permission denied.

---

### Post by jester164 on 2009-02-20
> **usmann said:**
> usman@us-home:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/usman/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/usman/.tvtime/tvtime.xml: Permission denied.
I am also interested in the solution to this issue, I get the same error messages.  Any/all help is appriciated!

---

