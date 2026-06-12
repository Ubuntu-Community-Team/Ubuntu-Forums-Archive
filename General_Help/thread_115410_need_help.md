---
title: "need help"
date: 2006-01-10
forum: General Help
---

### Post by Chrno on 2006-01-10
i need help to solve my internet problems.

my download speed on torrents have gone done from 100 -300 KB/s to 1-10 Kb/s and i load internet sites in about 10 min

we just switched our internet company and got a much better connection.

the problems started before the weekend.


this however is only on Ubuntu, on my win (same pc) i get the normal speed, web sites load 10 sec++ 

i updated Ubuntu today before school and stil i didn't have any effect.


is the problem my pc, my internet compay or me???


currently using (hate to say it) win on same pc

thanks for your time

---

### Post by bonzodog on 2006-01-10
Have changed your router?
If you have, it could be that the router is attempting to use a protocol called IPv6, which slows your normal (IPv4) connection down.
Go to this thread, and try out a few of the ideas in it:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Re-post again if this doesn't solve the problem. A quick indicator that this is the problem is by disabling IPv6 in firefox.
Open firefox, and in the address bar type:

```
about:config
```

This will list ALL of the configuration options in firefoxes backend. just below the address bar will be a blank box with the word 'filter' next to it. type 'IP' in there, and firefox will automatically single down the IPv6 connection options. One of those will be called:

```
network.dns.disable.ipv6
```, and will be set to 'false'.

RIGHT click on that option and a little menu will pop up. 
Click 'toggle' and the option will change to 'true'. You don't need to worry about saving this as firefox remembers it. 

Then, just try going to this website or something, and see if it loads faster. If it does, go to the thread, and disable IPv6 as recommended in there, and then bittorrent should speed up as will all other net connections.

---

### Post by Chrno on 2006-01-10
yea we did get a new router i forgot to say that

i connected with 1 switch that im sharing with my Xbox and then to the router

the guide helped alitle but iv found another problem

i can't use my bit torrent program (azureus) and at the same time use firefox for som reson.  when i do use them togheter i get realy bad speed like 10 min or timed out on sites (like this site) and my torrent speed din't change that much, but im gonna look it more to it tomorrow.



oh and you you know how to easy open ports for bittorrent that whould be great:


the info on my router is: 

Allied telesyn

AT-RG634

Residential Gateway


info on switch:

Jensen 

Fast Ethernet Switch 5 port




thats all that stands on them

thanks for your time

---

