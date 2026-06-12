---
title: "How do I setup a Modem in Ubuntu 8.10?"
date: 2009-05-22
forum: General Help
---

### Post by random_hypocrisy on 2009-05-22
I am soon going to be ditching my AOL broadband account in favour of a cheap dialup package, but I really need to know how to set up a modem to connect!

---

### Post by random_hypocrisy on 2009-05-22
Bump.

---

### Post by lindsay7 on 2009-05-22
I have trid to set up the modem which is built into my laptop with no luck.  I have read on this forum that you need an external modem, I think a serial modem but I am not sure. I have seen modems at Staples and on the net that say they are compatable with Ubuntu or Linux but I do not need one very often and I have not bought one.  There does not seem to be much help out there on this subject.

---

### Post by nitehawk777 on 2009-05-22
1.  Most important!!!  You _must_ have an external modem compatable with linux.  Most all soft (or "winmodems") won't work in linux.  

2.  It's late,..and I'm trying to remember,...but
    Open terminal,..type: sudo pppconfig (give password)...
    fill in all the info (hit enter)
3.  type: sudo gedit /etc/wvdial.conf (fill in the correct info  inside of the symbols <> (such as your IPS phone# password, etc.
(save)
4.   type:  sudo adduser (your_user_name) dip
     (hit enter)
5.   type:  sudo touch /etc/resolv.conf (hit enter)
6.   type:  sudo touch /etc/ppp/options
7.   type: sudo wvdialconf (this will detect your external modem)

I usually re-boot after all this.

8.   type: sudo pon name_of_your_ISP (this should start modem dialing).
9.  once connected to internet,..I usually opened Synaptic, and hit the "reload" button.  After Synaptic reloads,.....go to the "Search" section and type: gnome-ppp
10. download gnome-ppp

It's very late here,...brain's numb,...but I think that's it.

Oh! Just saw the post about modems,...
I have an external "US Robotics" and an external "Trendnet" and a "Modem Blaster",...all of them connect to one of the serial ports. (and all of them work in Linux).

---

### Post by albinootje on 2009-05-22
> **random_hypocrisy said:**
> I am soon going to be ditching my AOL broadband account in favour of a cheap dialup package, but I really need to know how to set up a modem to connect!

Is it an internal or external modem ?
External modems are easier to configure in Linux.
There's several programs to talk to/via modems, like wvdial, minicom, kppp.

See here for more information :
[https://help.ubuntu.com/8.04/internet/C/modem-connect.html](https://help.ubuntu.com/8.04/internet/C/modem-connect.html)
[https://help.ubuntu.com/8.04/internet/C/modem-identify.html](https://help.ubuntu.com/8.04/internet/C/modem-identify.html)

---

### Post by albinootje on 2009-05-22
> **nitehawk777 said:**
> 1.  Most important!!!  You _must_ have an external modem compatable with linux.  Most all soft (or "winmodems") won't work in linux.  


You forgot about internal modems which are not "winmodems". 
I've worked with those years ago in Linux without problems.

It is more likely to find "winmodems" on recent laptops, but there's still desktops with older internal modems around, and of course second hand internal and external modems compatible with Linux.

---

### Post by random_hypocrisy on 2009-05-22
Its internal, the lspci readout for it is;

02:0b.0 Communication controller: Intel Corporation 536EP Data Fax Modem

Is there a way to get it to work, or am I forced back to Windows? :(

---

### Post by albinootje on 2009-05-23
> **random_hypocrisy said:**
> 
02:0b.0 Communication controller: Intel Corporation 536EP Data Fax Modem

Your modem is mentioned here :
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

And perhaps see also here :
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

