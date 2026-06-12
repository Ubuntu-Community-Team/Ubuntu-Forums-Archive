---
title: "eth1 no private ioctls.  ????"
date: 2008-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x3Ith on 2008-05-27
hello I am new here, so I'd like to say hi to everybody.
 
well, and yes I have a little problem.

every time I log in or shut down or re-log I  get this error message:

* running local boot script (etc/rc.local) 
eth1 no private ioctls.

I have no idea what it means, I already asked in an german forum a week ago, but seems nobody knows anything there. however, when loggin in it throws me back so I allways have to login twice. its really odd. 

I'm running ubuntu 8.04 on an dell inspiron 6400 with ati grafic.

google didnt help me much, maybe here somebody knows.

pre-thnx

x3

---

### Post by x3Ith on 2008-05-27
hmm?

---

### Post by x3Ith on 2008-05-28
some more info:

iwpriv and iwconfig says

x3@bo:~$ iwpriv 
lo        no private ioctls.

eth0      no private ioctls.

wmaster0  no private ioctls.

wlan0     Available private ioctls :
          param            (8BE0) : set   2 int   & get   0      
          get_param        (8BE1) : set   1 int   & get   1 int  

x3@bo:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ShunjaRouting"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:1E:3A:00   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=55/100  Signal level=-75 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

well my wireless is working.. but there is no eth1

---

### Post by x3Ith on 2008-05-29
but how do I get rid of this error message??????

---

