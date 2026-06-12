---
title: "Install and Configure Webserver"
date: 2009-03-04
forum: General Help
---

### Post by Sojurner on 2009-03-04
I assume since there is not web section that i saw, that this would be a  good place to ask these questions.


Preface: I installed apache2 web server. It seems to be working mostly ok. I am using webmin to administer it.

1. Why can i access it from home when i type in the IP number but not when im out on another computer somewhere else.

2. How can i change the port number that it is running on. My IP seems to block me from broadcasting on port 80, and since im making this website for a personal reason, accessing it on another port is not a major issue.

3. How do i go about making a Domain for cheap. (ie. Is there a way to make my Domain something like mysite.athome.com (or .whatever), for cheap or FREE?) I guess how do i give myself a domain that resolves to my ip.
  3A. I just found a site that does free redirection with is all i beleive i will need since i can just redirect it to my ip. I just need help figuring out how to broadcast on another port.


4.Since im using Webmin. Does anyone know how to secure it. It keeps allowing me to "Add exceptions" from any computer in order to access it. Granted u still have enter your password and user name but id like to make it more secure if at all possible.

---

### Post by bostonaholic on 2009-03-04
> **Sojurner said:**
> I assume since there is not web section that i saw, that this would be a  good place to ask these questions.


Preface: I installed apache2 web server. It seems to be working mostly ok. I am using webmin to administer it.

1. Why can i access it from home when i type in the IP number but not when im out on another computer somewhere else.
**You need to setup your router to direct all incoming traffic on port 80 to your webserver.**

2. How can i change the port number that it is running on. My IP seems to block me from broadcasting on port 80, and since im making this website for a personal reason, accessing it on another port is not a major issue.
**incoming http traffic by default comes in via port 80.  if your ip is not allowing inbound port 80 traffic, you can change what port your webserver listens to in the setup (I'm guessing you can also change this from you webserver admin pge).  But make sure to reflect the new port number changes in your router as stated above**

3. How do i go about making a Domain for cheap. (ie. Is there a way to make my Domain something like mysite.athome.com (or .whatever), for cheap or FREE?) I guess how do i give myself a domain that resolves to my ip.
**there are plenty of places to 'buy domain name' search for that on the google.  Since you'll be hosting your site from home, no need to buy a hosting package.**

4.Since im using Webmin. Does anyone know how to secure it. It keeps allowing me to "Add exceptions" from any computer in order to access it. Granted u still have enter your password and user name but id like to make it more secure if at all possible.
**sorry, can't help you here**.

---

### Post by Sojurner on 2009-03-05
you keep mentioning setting up my router right. While iunderstand how to do that since i used to use a rounter i am not anymore. Its just my computer directly connected to the modem. Is there a software you would reccomend for this?

---

### Post by bostonaholic on 2009-03-05
> **Sojurner said:**
> you keep mentioning setting up my router right. While iunderstand how to do that since i used to use a rounter i am not anymore. Its just my computer directly connected to the modem. Is there a software you would reccomend for this?

If you have no router there is no need for port forwarding.  All incoming http traffic will be directed to port 80.  As far as I'm aware there is no way to get around this, so make sure your webserver is listening on 80.

**Now, to totally contradict the above statement...**

From my understanding, if someone wants to visit [www.something.com](www.something.com), they are actually visiting [www.something.com:80](www.something.com:80) which in turn (from the dns) is actualy 123.45.6.7:80.  So unless you want to use a different port number like 8080 for instance, to reach your site outside of your network one would need to visit [www.something.com:8080](www.something.com:8080).

Again, if I am not mistaken, when you buy your domain name, something.com, you may be able to set a port number in there.  The dns servicer will grab your ip 123.45.6.7 and will correlate that with something.com.  I'm not sure about this next part but... if maybe you told the dns your ip was 123.45.6.7:8080 it may automatically redirect inbound http traffic to your webserver listening on 8080.

I may be way off but... does that make any sense?

---

### Post by strife242 on 2009-03-05
I feel we missed probably the most important question.

Does your ISP provide you with a public or private IP address?
If you are uncertain, you can always post it here for an answer.

---

### Post by Sojurner on 2009-03-05
i assume when you say public or private you mean dynamic or static? I would imagine its a dynamic one but ive never seen it change.

If you really mean public or private its a 96.25.?.? . im really not sure if its public or private. I wouldnt imagine its public since the private ones i know of are 192.168.?.? and 172.016.?.? and 10.?.?.? but i dont know.

I can ping it but im not really sure of that means anything tho since its me.

---

### Post by strife242 on 2009-03-05
> **Sojurner said:**
> i assume when you say public or private you mean dynamic or static? I would imagine its a dynamic one but ive never seen it change.

If you really mean public or private its a 96.25.?.? . im really not sure if its public or private. I wouldnt imagine its public since the private ones i know of are 192.168.?.? and 172.016.?.? and 10.?.?.? but i dont know.

I can ping it but im not really sure of that means anything tho since its me.

No, I meant Public or private just as I said :)

Basically, public IP addresses are able to be advertised over the internet and can be used to access resources worldwide.

Private addresses (for instance addresses out of these scopes 10.0.0.0/8, 172.16.0.0/12 or 192.168.0.0/16) are to be used on LANs and is not routed on the internet.

You appear to get a public IP address to your computer and should be able to reach your webserver from the internet (as long as it listens to port 80, your ISP does not block port 80, your computer / personal firewall / router does not block port 80).

If your ISP block incoming packets on port 80 you can set your server up to listen to any available port, in that case when you surf to it just enter [http://xxx.xxx.xxx.xxx:newport](http://xxx.xxx.xxx.xxx:newport) in the browser.

In order to tie your IP address to a domain name you can, if using a dynamic IP (assigned by ISPs DHCP server) use a service like dyndns.com or no-ip.org, or if static use any domain registrant available and tell them to point your domain name to your IP address.

---

### Post by insineratehymn on 2009-03-05
1) Get a router. Today.

2) Your IP is a class A public, and I bet its dynamic. (although I have no idea of the relevance).

3) No-Ip.org/DynDNS will get you started with a domain name for free that will come back to your own computer.

Your computer should take any incoming web traffic and give it to Apache automatically, but I cannot stress enough the importance of you getting a router to do that for you. 

You can import PGP key rings into Webmin, they explain how on their website. No matter how secure you make Webmin, your computer has a GAPING HOLE if there is no gateway.

---

### Post by Sojurner on 2009-03-06
yea i know i need a router. i need one bad. i just cant afford to go out and get one right now. i will soon tho. 

Do any of you now where in webmin or in the apache config file i need to edit to make it listen on a different port. Say 8080 or something not used by other services.

---

### Post by dereknashvilleff on 2009-03-10
I may not bre much help here since i am just a newbie myself. Two months in, but i believe when you login to webmin there is an option under configuration tab on left. That should allow you to specify port settings.

---

### Post by loudog23 on 2009-04-20
Humm, 
Ok, i cant help you with the webmin but...

(this work fine for me with ubuntu HARDY, dyndns, apache2)
_In this example i will use the port to 65080_

-If you have an dynamic IP, get DYNDNS.COM, create a domain name (free). (if not already done)
-Install ddclient (sudo apt-get install ddclient)
-edit the ddclient.conf (sudo gedit /etc/ddclient.conf), it sould llok something like this : ```
 
#**process id**
pid=/var/run/ddclient.pid 

#**time in seconds for renewing redirection of your IP**
daemon=600 

#**if you use a domain from dyndns.com**
protocol=dyndns2 

#**Used to verify your current IP**
use=web, web=checkip.dyndns.org/, web-skip='IP Address' 

#**dydns servers**
server=members.dyndns.org 

#**replace * by your username at dyndns.com** 
login= * 

#**replace * by your password at dyndns.com** 
password= * 

#**replace * by your domain name at dyndns.com ** 
#(if you have more than 1 domain, add an , and your 2nd domainname
#firstdomain.dyndns.org,seconddomain.dyndns.org 
*

```

This sould solve your Dynamic, Domain name and re-directing issue.
At dyndns, you can create an 2nd domain that is redirected to the second one on a different port. -> [http://www.dyndns.com/services/webredirect/](http://www.dyndns.com/services/webredirect/)
This might be useless if its for your personal use since you simply have to type [www.yourdomain.com:usedport#](www.yourdomain.com:usedport#) ([www.yourdomainname.net:65080](www.yourdomainname.net:65080))

--------------------------------------------------

To make you apache listen to another port, simply edit the yourdomain.conf files found in (sudo gedit /etc/apache2/sites-avaialable/yourdomain.conf) and change the port (these sould be your 2 first line in the file)
```

NameVirtualHost *:65080
<VirtualHost *:65080>

```
and in your ports.conf files (sudo gedit /etc/apache2/ports.conf)
```

Listen 65080

```
if im wrong, please someone tell us (as i still consider myself a newbie)

Hope this help you a bit. I suggest you type apache in the search box of this forum and read through the post. I know it's a long lecture but you will learn how to make yourself a nice server in little time. About 2 week ago i didn't have a clue what i was doing, and now i have it running smooth and clean thanks to the forums.

:popcorn:

---

