---
title: "Trouble with every sharing program"
date: 2005-10-31
forum: Desktop Environments
---

### Post by JeffBlouin on 2005-10-31
Hi

        Ive been using ubuntu for 3 weeks now and every thing is nice except for files sharing program...  DC++ and bittorent are slow (very slow!).  Here is my setup

Connecting to internet with a USR router 8054 And high speed internet

In bittornado the light is often yellow (I dont have a firewall and dont think im connecting to a proxy...)The speed is not very good (bittornado and azureus) if I compare it with the same torrent on Windows with azureus

In DC++ Im in passive mode... if I put it in active mode nothing is working... 
The speed is not that good

Thanks,  
Really wanting to get Ubuntu working!

---

### Post by Pathogenix on 2005-10-31
Have you got your router configured properly to forward the ports for DC?

---

### Post by JeffBlouin on 2005-11-04
No and this must be the problem... 

Do you know if there is a good HowTo for port forwarding and static IP
for bittornado and DC++

Thanks

---

### Post by psychicdragon on 2005-11-04
Who set up your router? The easiest way to get port forwarding working would be to ask them.

If you know the password to the router you just need to point your browser to [http://192.168.0.1/](http://192.168.0.1/) (or maybe [http://192.168.1.1/](http://192.168.1.1/)) and you can open the ports yourself.

Bittorrent uses ports 6881 - 6999 by default
I'm not to sure about DC ++

---

### Post by bionnaki on 2005-11-04
[http://www.portforward.com/](http://www.portforward.com/)

---

### Post by Saiboogu on 2005-11-04
Like the others said, forward your ports. Seems USR gives it an "odd" name .. Virtual Server. Here, link to the userguide...

[http://tinyurl.com/5xpkc](http://tinyurl.com/5xpkc)

---

### Post by JeffBlouin on 2005-11-05
Hi,

        I did open port 6881 (Im using azureus now).  Before that i had to setup a static IP adress. To do that I went to networking and enter the information about Ip adress, submask and gateway.  Do I need to do anything else on my router for setting this static IP

Nat test on Azureus say port 6881 ok

Before that (port opening and Static IP) I was able to download at slow speed, now I not even able to get a yellow face on health status...  

Any other tips
Thanks

---

### Post by Ocxic on 2005-11-15
[QUOTE=JeffBlouin]Hi

        Ive been using ubuntu for 3 weeks now and every thing is nice except for files sharing program...  DC++ and bittorent are slow (very slow!).  Here is my setup

Connecting to internet with a USR router 8054 And high speed internet

In bittornado the light is often yellow (I dont have a firewall and dont think im connecting to a proxy...)The speed is not very good (bittornado and azureus) if I compare it with the same torrent on Windows with azureus

In DC++ Im in passive mode... if I put it in active mode nothing is working... 
The speed is not that good

Thanks,  
Really wanting to get Ubuntu working![/QUOTE]


bittornado doesn't use the torrent protocol properly, most ppl i know won't use it

---

