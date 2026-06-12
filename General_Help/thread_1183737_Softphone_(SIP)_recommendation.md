---
title: "Softphone (SIP) recommendation?"
date: 2009-06-10
forum: General Help
---

### Post by UranUtan on 2009-06-10
Hi,

I have just signed up with a VoIP Service and begin palying with softphone. I have tried a few but due to my inexperience, either I failed to install the software (XLite, QuteCom) or could install but didn't configure properly (Ekiga, Zoiper). 
 
To accelerate my discovery phase, can you please recommend me a good SIP softphone. Requirements are:

- Must run under Ubuntu 9.04 x64
- Must be SIP compatible and independent from any specific VoIP provider
- Gnome if possible
- Stable and well supported.

So far I have heard of: Ekiga, Twinkle, Wengophone/QuteCom, X-Lite, Zoiper. But it will take me quite a while to learn/review each of them.

Can you please give some advices? Thanks very much in advance.

---

### Post by Engineer.Abdalla on 2010-05-07
I think xlite is good, and to install see:
[URL="http://abdallao.blogspot.com/2010/05/how-to-install-xlite-20-on-ubuntu-910.html"]http://abdallao.blogspot.com/2010/05/how-to-install-xlite-20-on-ubuntu-910.html
[/URL]

---

### Post by sylvester_0 on 2010-05-07
Good luck - I've tried doing the same thing and decided to just use my hard phone. I always experience audio problems (stuttering etc) when using soft phones on Linux. I don't know if it's a Pulseaudio issue or what but I've given up.

The general consensus out there from what I've gathered is that Ekiga is the best. I've used Twinkle in the past and mostly liked it. It looks like it hasn't been updated for over a year tho :/

---

### Post by tlacuache on 2010-05-07
I've personally had very good luck with Twinkle. I've had a few problems with Ekiga playing nicely with Pulse, although I haven't used it since early Karmic days.

---

### Post by koanhead on 2010-05-07
Over the course of several years, six different machines, and many different Ubuntu versions and flavors of Linux, Ekiga has never, ever worked for me.
I currently use Gizmo5 but I don't recommend it to others since it was non-free last I checked and they don't provide a 64bit binary. This may have changed since the company was acquired by google, I will find out soon.

---

### Post by sylvester_0 on 2010-05-07
Yea - Ekiga is a mystery to me. I've also tried to use it on many stock Asterisk installs (it'd be nice to have a registration on each of my client's PBXs) over the years but I always experience random freezes and audio problems.

---

### Post by UranUtan on 2010-06-02
Hi,

I have made some progress since the time I made the post. I have tried Xlite, SJphone, Twintlke and Ekiga. Ekiga works better than the others which I have voice quality issues. But Ekiga is slow and complex.

Recently I upgraded to Ubuntu 10.04 x64. In the Software center, there is Linphone 3.21. It is simple, convenient and works perfectly. My quest for a Linux softphone is now over. If you use Linphone, Here are the config you will likely use:


- Your SIP Identity: sip:(the user account ID when you signed up)@(SIP Server of your VoIP provider)

Example: with VoIP.ms provider. As I am in Canada, VoIP.ms proposes a proxy server in Toronto named "toronto.voip.ms" 

- Your SIP Identity:123456@toronto.voip.ms
- SIP Proxy Address: sip:toronto.voip.ms
- Route (optional): (leave empty)

- Behind NAT/Firewall (Specify Gateway IP below)
Public IP Address: 192.168.0.1 (this is the IP of your router)

The format of the phone number to call must be sip:14161112222@toronto.voip.ms

NOTE: replace toronto.voip.ms by the SIP Proxy of your own VoIP provider.


EDIT: using Linphone 3.21 for about a few hours and I notice a something quite annoying. The contact list is not manageable. Contacts can not be grouped and cannot be sorted. If you have a big contact list this will be a totally messy list. The phone feature is good however.

---

### Post by YannBuntu on 2010-07-05
Dear all,
on Lucid, there is a PPA for Ekiga that solves some NAT issues : [http://wiki.ekiga.org/index.php/HowTo_install_Ekiga_packages#10.04_Lucid_Lynx_.28Long_Term_Support.29](http://wiki.ekiga.org/index.php/HowTo_install_Ekiga_packages#10.04_Lucid_Lynx_.28Long_Term_Support.29)

---

### Post by set321go on 2011-07-27
this is an old thread but i thought it would be handy to update it.

I am running ubuntu 11.04 with unity. 
I am running linphone without any problems
I tried twinkle but couldnt get it to work, i think these drawbacks were most likley due to configuration rather than incompatabilty with ubuntu

---

