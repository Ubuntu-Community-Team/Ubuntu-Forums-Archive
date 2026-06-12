---
title: "Help With Web Server"
date: 2005-12-10
forum: General Help
---

### Post by Yoda_Oz on 2005-12-10
Hi,
this is my setup:
* wireless AP router connected to broadband - ISP Tiscali
* wireless connection to my ubuntu box - works perfectly!

i have apache2, php5 and mysql installed properly and everything works fine when i type in [http://localhost](http://localhost) in my browser as my offline web page loads perfectly.

want i want to be able to do (if possible) is has other people outside of my LAN access my "offline" web page. can this be done?

i have my own domain name (christianbrooker.com). can i redirect the domain name servers to my own ipaddress? how do i do this?

cheers!

---

### Post by Mujaheiden on 2005-12-10
Find yourself a DNS server ;)

---

### Post by luibh on 2005-12-10
for a dns server, i use [http://freedns.afraid.org/](http://freedns.afraid.org/) - its pretty easy to setup a domain you own. i know there are several other free dns servers out there, but this is the one i found to work pretty well.

---

### Post by Yoda_Oz on 2005-12-10
thanks...
but i'm still not sure as to to what i need to do to let other people access my computer's website.
im behind a nat router. how does dns work? anyone with any tutorials?
thanks

---

### Post by jabber on 2005-12-11
Hi,

You will need to set up port forwarding on your router. Assign a static ip to your web server, and set your router to forward port 80 (default for http) to the web servers ip address.

If you google port forwarding and your router model you should find a guide quite easily.

---

### Post by Yoda_Oz on 2005-12-12
done that already... thanks anyway. ive got a static ip on my server of 192.168.0.2 and i have port forwarding of port 80...

how do i set up the dns so that when people type in the domain name christianbrooker.com they get my computer's server?

---

### Post by luibh on 2005-12-12
like Mujaheiden said, you need a dns server. just google free dns or try [http://freedns.afraid.org](http://freedns.afraid.org) or [http://soa.granitecanyon.com/](http://soa.granitecanyon.com/) - the dns server sites will have lots of info on setting up their service. ive tried both. freedns.afraid.org, i think, is more user friendly. if you were more experienced then granitecanyon would work for you. also, you will have to edit your domain's dns assignment server. this is usually done through your registrar. that will most likely be outlined in the dns services docs or forums.

over all, its really easy to set up, especially with a user friendly service.

---

### Post by Yoda_Oz on 2005-12-13
right im having problems letting the outside world access my computer.

localhost works fine and i can type in my ip address from another computer on my LAN and the website comes up fine.

i cant test my outside ip address because my router doesnt support loopback. however i asked someone to type in my ip address: 88.108.68.11 and they said it came up with connection refused. i have port 80 already forwarded so i tried to forward port 8080 and also 20800 and then getting them to type in 88.108.68.11:8080 and then 88.108.68.11:20800 to no avail.

i then came across a website that had a port scanner called sheilds up on [http://www.grc.com](http://www.grc.com). that scan told me that ports 80, 8080 and 20800, in fact all ports! were marked as "stealth".

can anyone explain to me what this means and why those ports aren't "open"??? i can see that maybe my ISP is blocking 80 and 8080 but 20800 is so random, surely they cant be blocking that too...

have i set up apache wrong. actually... all i did was apt-get install apache and then it worked straight away. are there any config files that i need to edit to allow access to port 80? is there anything in the ubuntu that i need to change to allow port 80 access?

cheers in advance for any help!

---

### Post by zukakog on 2005-12-13
Your ISP is probably blocking incoming request on port 80, 8080, and 21.  Call and ask them.  I know for a fact that COX does.

You'll have to change your domain from [www.whatever.com](www.whatever.com) (which is infact [www.whatever.com:80](www.whatever.com:80)) to [www.whatever.com:185](www.whatever.com:185) (or some other open port) and then configure your router to send all request to port 185 from the WAN  to port 80 on your server box.

---

### Post by luibh on 2005-12-13
sorry, didnt quite catch what you were saying originally. zukakog is probably right. once the router listens to the new port you probably will have it. again, when you set up the dns, you can direct it to that new port and visitors will only have to enter [www.whatever.com](www.whatever.com) - try the new port to see if the ISP is blocking it. can the ISP block all incoming ports, is that possible?

---

### Post by LoclynGrey on 2005-12-13
You should be able to get your domain name to redirect to your static IP address which is in the settings of your domain name.
For example my domain name is with register direct (NZ) and via their web based system I configured anything that hits my domain name to be redirected to a static IP address. Once at that IP address my router then port forwards internally to my local networked box which contained the Webserver.

My router is a Dlink 704P and i just enabled a virtual server setting on port 8080.
Sometimes ISPs don't like the loop back thing so you might have to set a web browser on one of your internal networked machines to go via a proxy server.

I've found in the past that anti virus and firewalls blocked my own hosted webserver. (until i reconfigured)

---

### Post by Yoda_Oz on 2005-12-13
> 
You'll have to change your domain from [www.whatever.com](www.whatever.com) (which is infact [www.whatever.com:80](www.whatever.com:80)) to [www.whatever.com:185](www.whatever.com:185) (or some other open port) and then configure your router to send all request to port 185 from the WAN to port 80 on your server box.
i have a netgear dg834gt wireless modem/router. i have to create a new service and i have named that service "webserver" on port 20800. i have then, in the firewall section, created a rule for that "webserver" service to be used and to forward all stuff from port 20800 to my LAN ip address. there is no option to forward to LAN port 80. how can i do this?
do i have to change something in apache to say that http requests are on port 20800 rather than 80? if so how do i do this?

---

### Post by nietpiet on 2006-01-05
well, 
apparently there is this:
[INDENT]sudo gedit /etc/apache2/ports.conf[/INDENT]
there you can configure apache to listen to a different port.

however, i have your same problem!
i have set TCP port forwarding on my router to port 1234,
and have apache listen to part 1234
and now these ips work in my browser:
[INDENT]
[http://localhost:1234/](http://localhost:1234/)
[http://192.168.1.8:1234/](http://192.168.1.8:1234/)
[/INDENT]
however, if I use the IP address of my router, 
[INDENT][http://0.0.0.0:1234/](http://0.0.0.0:1234/)[/INDENT]
then i get an "connection is refused" error.

anybody any idea?

---

### Post by Yoda_Oz on 2006-01-05
i actually got a reply back from my ISP (tiscali UK) and they said that they dont block any ports at all. i found out the reason that i couldnt connect, is because my router doesnt support loopback.
i downloaded and installed LAMPP and everything works perfectly.

---

### Post by nietpiet on 2006-01-05
something called Loopback eh?
ok! i'll look into my modem specs.
so, if my modem also doesn't support loopback, then this LLAMP that will fix this?

Thanks! i'll look into that too!

---

### Post by Yoda_Oz on 2006-01-06
if your modem doesnt support loopback i dont think there is anything you can do about it short of going to a friend's house to test it.

LAMPP is actually XAMPP, which is software that you install which gives you a complete set of apache, mysql, php and perl. everything you need to run a web server. you have to get rid of all of the above before installing otherwise there will be clashes and stuff... im onlu new to this too so somebody correct me if im wrong.
XAMPP took 2 minutes to install and after reading the manual and getting a few tips from the website i had my server up and running properly within 30 minutes.

the url for XAMPP is this:
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by nietpiet on 2006-01-10
Thanks you for your help!
it worked all along, however i couldn't see it!

it is a problem with the router.
(posting the results, for other people's info)

i have this versatel provider, (in the netherlands) with a Davolink DV-201AMR modem.
apparently it won't let you access the webserver using the WAN IP of the modem if you are inside the network.

so, i just ssh'ed to my work, started lynx,  and presto!
it was working all along, however i couldn't see it!
see [http://forum.versatel.nl/viewtopic.php?t=10751&postdays=0&postorder=asc&start=25](http://forum.versatel.nl/viewtopic.php?t=10751&postdays=0&postorder=asc&start=25)

---

### Post by Yoda_Oz on 2006-01-10
yeah, that feature is called LOOPBACK... for anyone who's looking to buy a new modem!

---

### Post by nietpiet on 2006-01-11
LOL! :p  
I went round the wrong way to solve the problem!
i was looking at the specs of the modem, and didn't find anything called 'loopback'!
while i should've looked at the meaning of the word loopback, and then tested my modem!

even after the problem is solved, i keep learning!

thanks!

---

