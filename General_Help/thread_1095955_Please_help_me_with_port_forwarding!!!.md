---
title: "Please help me with port forwarding!!!"
date: 2009-03-14
forum: General Help
---

### Post by tahirih on 2009-03-14
I use Ubuntu Intrepid Ibex and I'm trying to install WOW BC and I've followed the instructions via this site:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Now I just did the firewall config but I'm having issues with the Router Config. If anyone can help me out with the port forwarding, thatd be really appreciated! Im going crazy with this!!!! I just wanna play my World of Warcraft and it seems I'm getting more problems than it's worth!

---

### Post by mikewhatever on 2009-03-14
Try this site [http://portforward.com/](http://portforward.com/). Forwarding a port is usually very simple, you enter the port through the router interface and voila. There might be a section in the router manual on that.

---

### Post by Darkade on 2009-03-14
> **mikewhatever said:**
> Try this site [http://portforward.com/](http://portforward.com/). Forwarding a port is usually very simple, you enter the port through the router interface and voila. There might be a section in the router manual on that.
That site is a great resource. Just look for a guide for your router model and you'll be ready to go

---

### Post by dhughes on 2009-03-14
Yup portforward has good info even walks you through your own router version.

 In a nutshell:

 [LIST=1]
[*]you enter 192.168.1.1 or 192.168.1.0 or something similar to that to get to your router's Setup screen

[*] Look for 'Applications & Gaming' (Linksys) or Virtual Server (D-Link)

[*] You need a port number, WoW uses 3724 TCP, so look for two boxes and put 3724 in both and choose TCP

[*] Also make sure you know your internal IP, e.g. like I said above may be 192.168.1.1 so your computer is probably 192.168.1.100 So next to the 3724 TCP you'll see you have to choose what IP 3724 is directed to...or from? (something like that)

[*] Check the box next to what you created and Save the new setup
[/LIST]

---

### Post by brianhardy on 2009-03-14
What type of router do you use.  I have a Belkin and its really easy to port forward.  But try [http://portforward.com/](http://portforward.com/) Its really good site

---

### Post by tahirih on 2009-03-14
I tried that port forward already but it only has windows instructions. Do I just do it in the linux terminal? And I have a Actiontec M1000

---

### Post by blackened on 2009-03-14
> **tahirih said:**
> I tried that port forward already but it only has windows instructions. Do I just do it in the linux terminal? And I have a Actiontec M1000

You need to do the setup for static IP through whichever means you're comfortable using. It can be set up through Gnome's network manager or through the terminal.

The router configuration is done using whatever web browser you prefer and is not operating system specific.

---

### Post by tahirih on 2009-03-14
Oh and I forgot to mention I don't have a router... its a DSL modem

---

### Post by thesavager on 2009-03-14
Hi, 

If you really dont get it to work , install Mason

[http://mason.stearns.org/](http://mason.stearns.org/)

cheers ...

---

### Post by Darkade on 2009-03-14
> **tahirih said:**
> Oh and I forgot to mention I don't have a router... its a DSL modem
well what's your modem model?

I have a 2wire DSL modem (Which is also a router, like most DSL modems) to access it's configuration I just go to [http://homeportal](http://homeportal) in any browser in any computer that's part of my network.

Portforwarding has not much to do with your computer. What you do is
>set up a service in your computer
>then that service will be available  to anyone in your network
>then you do portforwarding, that's telling your router/DSL modem that "when it's is asked for a service or a port it must redirect it to some computer within the network"

When they say windows instructions most times they reffer to the setup CD's for the routers or modems. But every single home router/modem I've seen has a config site (like the [http://homeportal/](http://homeportal/) I mentioned before)

---

### Post by mikewhatever on 2009-03-14
> **tahirih said:**
> Oh and I forgot to mention I don't have a router... its a DSL modem

In this case, no port forwarding should be needed.

---

### Post by blackened on 2009-03-14
I'm pretty sure this unit has router functionality built in. From everything I've seen, it's meant to come as a base unit that supports modular add-ons.

You should first open your browser and go to 192.168.0.1 and check if there is a browser interface for it. The port forwarding settings should be located in the "Advanced Setup" tab.

As I mentioned earlier, port forwarding will likely not work if you are using DHCP to assign addresses. You should set up a static address for the machine you're planning to forward to.

---

### Post by tahirih on 2009-03-15
Ok well I did have to do the port forwarding. The reason it didnt work before is because I was off one number on my IP addy. oops :oops: I feel ignorant for that. But as soon as I configured my modem on my IP website, the download went so fast. I successfully downloaded the upgrades and new patch and even upgraded to WOTLK. 

Now when I go to the log in screen it shows the boxes and the words, just not the graphics. When I had wow on my old computer a year ago my friend told me to do some command that I don't remember now. But it was something like "compiz - replace metacity". I don't know...

---

### Post by tahirih on 2009-03-15
Scratch that last post... I just had to restart my computer and it's working just fine! I think I'm going to go play right now. 

Thanks for your help, everyone! ):P

---

