---
title: "Problems setting up Azureus"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Barts_706 on 2006-07-02
Hi,

I have just installed Azureus, but I have problems with ports forwarding. I don't know where or how I can allow Azureus to use Incoming TCP Listen Port (whatever the number). I tried a few things and google, but still am getting ¨Testing port 65034 ... NAT Error¨ (which I don get under Windows on the same machine, so it is not something related to my network connection). I would be grateful if someone could even point me out to some How To or tutorial on this.

Also, error boxes in lower right hand corner refuse to disappear, and I cannot force them to (?).

Barts

---

### Post by kinematic on 2006-07-02
error boxes not wanting to disappear is very annoying.
[http://torrents.aelitis.com:88/files/Azureus2403-B51.jar](http://torrents.aelitis.com:88/files/Azureus2403-B51.jar)  is were you can get the latest cvs snapshot
download the azureus jar file and rename it to azureus2.jar.
open nautilus as root with the gksudo nautilus command and goto /usr/share/java and replace the azureus2.jar with the new one.....that should do it.
as far as portforwarding goes....if you have firestarter(or guarddog)running open a port for azureus in it(preferably in the 50.000 range...isp's tend to throttle lower ports).
if you're behind a router i don't know ;) 
and might i suggest using bittornado...it works a treat on ubuntu.

---

### Post by Barts_706 on 2006-07-02
[QUOTE=kinematic]
as far as portforwarding goes....if you have firestarter(or guarddog)running open a port for azureus in it(preferably in the 50.000 range...isp's tend to throttle lower ports).
[/QUOTE]

That is exactly my point - I do not know how to open a port.

I don't think I have firestarter or guarddog enabled. I do not see them on the process list. I have pretty much the fresh and basic Ubuntu installation, which I am now shaping up. 

So if someone could tell me how do I open these ports, it would be very nice.


[QUOTE=kinematic]
and might i suggest using bittornado...it works a treat on ubuntu.[/QUOTE]

Okay, I might give BitTornado a try...

---

### Post by kinematic on 2006-07-02
if it's a fresh install you don't have a firewall and any port should result in nat ok.
go to tools(or configuration.....don't remember) and select nat/firewall test and use port 54378(i used to use that one)for example and hit the test button.
if it's ok click on apply.

---

### Post by Barts_706 on 2006-07-02
The problem is, these ports are not okay - NAT test fails. And this is the thing that makes me wonder, especially since Azureus doesn't have problems on the same machine under Windows XP.

Any suggestions?

---

### Post by fordfan753 on 2006-07-02
Maybe on Windows UPNP or whatever that setting is that automagically opens ports for you was on. Is UPNP (or whatever it's called) turned on?

NOTE: I don't actually think it's called UPNP, I think that's something else, someone correct me....it definitely starts with a U....UNAT maybe...meh, I dunno, anyway, find out what it is and turn it on. Only works if your router supports it.

---

### Post by kinematic on 2006-07-02
If it just doesn't work i don't know what the problem is.
I've never been able to get Azureus to work the way it should on Debian or any Debian derived distro(including Ubuntu)but it works fine on PCLinuxOS(and other rpm based distro's i've tried).
I just gave up on trying to get it to work and now i use Bittornado on Ubuntu wich works just as well.

---

### Post by FLeiXiuS on 2006-07-02
Are you behind a router of some sort?  Have you installed a firewall preventing access to that port?

---

### Post by Thund3rstruck on 2006-07-02
I have given up on Azureus as well. I've found that uTorrent via Wine works very well

---

### Post by Barts_706 on 2006-07-03
Hi again,

Sorry it took me so long to reply, but I went to sleep in the meantime (sometimes you have to...).

So, to provide you with more information - I am connected to a local network in my building. The local network IS behind a firewall of some sort BUT the same ports are not blocked if you use Windows on the same terminal SO I think the issue is not there.

---

### Post by blissend on 2006-07-14
For some reason I had to forward the ports on Ubuntu to get it working for me. You can configure Ubuntu's ports using firestarter (in the repositories I believe). You can also check your forwarded ports via the command...
```
sudo iptables -L
```

---

### Post by Barts_706 on 2006-07-14
Okay, I'll check that. And when I already check - how do you actually forward the ports? 

(I have googled a little but didn't find anything useful, so it is enough if you just give me the name of command in question and I'll handle it from there)

---

### Post by Griff on 2006-07-14
A few things:

1) I suggest installing firestarter to deal with iptables; it's a nice and easy to use gui and you'll have to open more ports eventually for other apps.  Ports are generally not open on a fresh ubuntu install for security reasons and this little app will allow you to easily open the ones you need and monitor traffic.
```
sudo apt-get install firestarter
```

2) In firestarter window:
  -click policy tab
  -click in the 'allow service' area and click on add rule
  -enter the required info and your comp should be good

3)In regards to port forwarding you'll need access to that router; here's a couple good links from the azureus wiki to tell you a little about port-forwarding and the like
[http://www.azureuswiki.com/index.php/Port_forwarding](http://www.azureuswiki.com/index.php/Port_forwarding)
[http://www.azureuswiki.com/index.php/NAT](http://www.azureuswiki.com/index.php/NAT)

4)When you have Azureus up, try this link out with your port number instead of the one that's there (in case you change it)
[https://www.grc.com/x/portprobe=65034](https://www.grc.com/x/portprobe=65034)

Post back where you get stuck or with more specifics about what kind of network you are on.  Stick with it, Azureus is definately worth any trouble you are having. :mrgreen: 

Good luck,
Griff

---

### Post by Barts_706 on 2006-07-14
Thanks a lot!

---

### Post by Griff on 2006-07-14
Oh, and you'll want to have firestarter on startup from now on.  To do this go to:
System > Preferences > Sessions
Click the 'Startup Programs' tab
Click 'Add' and enter: gksudo firestarter

---

