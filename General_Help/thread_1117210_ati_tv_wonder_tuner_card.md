---
title: "ati tv wonder tuner card??"
date: 2009-04-05
forum: General Help
---

### Post by broekskw on 2009-04-05
hello every one, was just wondering if there is a step by step guide on getting a tv tuner vard working in ubuntu 8.04; i have a ati tv wonder card that is working in windows xp, would like to get it to work in ubuntu, have looged and searched this site but not to sure on the correct guide to use.):P

thanks all

---

### Post by broekskw on 2009-04-05
ok anyone out there have this setup??
it's just a tv tuner card that i hook up my bell sat to and then out to my 21.5 monitor in my bedroom so i can watch sat tv on my monitor, it's not a dvb card just a tv tuner card?

help, i tried to install mythtv but i think thats for the dvb cards

:guitar:

---

### Post by Afkpuz on 2009-04-05
Mythtv is going to be your best bet in terms of support and ease of use.  It supports both analog and digital.  Your card is also supported in mythtv, just with a caveat: apparently, the color might be off which is fixable, but not convenient.  Here's the abridged version of how to set up myth.



1.) Install myth
```
sudo apt-get install mythtv
```

Don't change any settings during install except if you want other computers using mythtv.  Check that box because it'll save you headaches later when you want to expand to more than one box.  


2.) Configure your tuner
Mythtv has two main components: frontends and backends.  The backend is what talks to the tuner cards, while the frontend is what outputs an image.  You'll need to set up the backend before the frontend can do anything.  

Backend setup is in System>Administration>Mythtv backend setup (or similar name).  Click that and work from the top down.  Make sure to set the proper channel table frequency in the general section.  

3.) Watch in the frontend
It's in Applications>sound and video



That's not the whole process, but should get you started.  Here's the mythtv page for more info:
[http://www.mythtv.org/wiki/ATI_TV-Wonder](http://www.mythtv.org/wiki/ATI_TV-Wonder)

---

### Post by broekskw on 2009-04-05
thanks Afkpuz did the command as you said and at the end get this error code??
code
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on ntp | time-daemon | ntp-simple; however:
  Package ntp is not configured yet.
  Package time-daemon is not installed.
  Package ntp-simple is not installed.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ntp
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
broekskw@broekskw-desktop:~$ 
code
can you help me out on this one??

thanks
:guitar:

---

### Post by manuelg on 2009-04-05
You could use tvtime.  It's a lot easier to setup than mythtv

sudo apt-get install tvtime

or install it using the synaptic package manager.  I'm not sure if the card would be recognized, but in my computer I have a text file in /etc/modprobe.d named cx88[0] and in it there is...

options cx88[0] card=4 tuner=44

which are the options for the type of card and tuner that the cx88 chip has. I've had that setup since 7.04 and I just update the os as it comes out.  That's why I'm not sure if the card will be recognized.  Try it out anyway, it works fine with cable tv.

---

### Post by Afkpuz on 2009-04-06
Ok, then go use synaptic to install mythtv.  Yea, tv time will give you an easy setup, but I've had tuners work in mythtv that would not work in tvtime

---

