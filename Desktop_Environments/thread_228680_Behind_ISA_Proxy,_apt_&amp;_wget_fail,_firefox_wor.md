---
title: "Behind ISA Proxy, apt &amp; wget fail, firefox works."
date: 2006-08-03
forum: Desktop Environments
---

### Post by pureliquidhw on 2006-08-03
I installed ubuntu 6.06 on a HP Pavillion dv1000 series laptop. everything (including WiFi) came up perfectly, but when I attempt to use apt-get, wget, and synaptic, i get the 407 authentication error.

I tried using export in the .bashrc file, adding the domain to that command, I even resorted to putting the password in plaintext in the command, just to see if the ISA server would recognize it.

Is there something i'm missing in the apt.conf file?

or is the solution a function that needs to be written in .bashrc?

I've read a few forum posts, but none of the methods seemed to work.  Also, the cryptic apt.conf man wasnt much help.

---

### Post by Thund3rstruck on 2006-08-03
I think you have to set your global proxy settings in System > Preferences >Network Proxy

---

### Post by pureliquidhw on 2006-08-03
I did that first.

Http proxy: 172.17.2.8:8080

<details button>

<checked use authentication>

retyped username and password.

still no luck.

---

### Post by pureliquidhw on 2006-08-03
problem solved.

If you are behind an ISA server and have any difficulties, just follow the second method in this link:

[URL="http://www.faqs.org/docs/Linux-HOWTO/Web-Browsing-Behind-ISA-Server-HOWTO.html"]http://www.faqs.org/docs/Linux-HOWTO/Web-Browsing-Behind-ISA-Server-HOWTO.html

[/URL]

---

### Post by true_friend on 2006-08-03
Hay buddy.
pureliquidhw is saying right. i struggled for a month to search this method now it is working on my linux box perfactly. only my messenger is not working which i think i have to download another software which will convert socks to http then i this http request will be fullfilled by NTLM proxy server.
All the details are given in the home page it is very easy to use and works fine.
Regards
True_Friend

---

### Post by true_friend on 2006-08-03
Remember
If u are behind an ISAserver Proxy as u are saying NTLM Proxy Server can not pass it. it is written in the readme clearly.

---

### Post by pureliquidhw on 2006-08-03
yes, you are right.  It is working for me, but not perfectly.  Something screwy is going on.  apt-get works, but not very well.  tit is transfering data @ ~630B/s, or in other words, really slow.  another fact is the maxxed proccessor.  Will be reloading ubuntu to start from scratch (not a solution) so i can identify what is going wrong.

note: firefox works great.  But google maps screwed up.  AND automatix downloaded all the install files, but failed to load them.  I have no idea what happened, but i blame it all on my proxy.

---

### Post by true_friend on 2006-08-05
i found automatix very bad on kubuntu. it was not installing even on kde. in gnome it works perfactly with NTLM proxy server. only thing is to change the proxy settings to 127.0.0.1:5865 in webget's  proxy configuration and ap-get proxy configuration.
now i am seeking to configure "socks via http" a software converts socks requests to HTTP which then be tunneled through NTLM proxy server. but no guide is available in this regard.
have u tried it???
"socks via http" keyword will give u the home page from google.

---

### Post by morelvj on 2006-08-22
I had the same problem but NTLM doesn't work for me. The last that i did was putting in the Network Proxy preference the IP with the username and pass. Ex. username:password@0.0.0.0. This work perfectly.

---

