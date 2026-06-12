---
title: "Battlefield 1942 Server Help?"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by tocleora on 2007-03-27
I've installed the Battlefield 1942 server in Ubuntu 6.06.  It works great as long as only one person is in it.  But if two people go into it, it kicks them both out with this error:

> 
You have been kicked via PunkBuster ... Duplicate GUID/CD Key


There are three of us, all three of us have legally purchased (from the store) copies of BF1942, but if any combination of the three get on it, we get this error.  Anyone have experience with BF1942 Server on Ubuntu (or Linux in general)?  I should mention we're all three trying from work so we have the same IP address externally, but we are able to go into other BF1942 servers without problems.

Also, we're trying to figure out how to admin the game, we got instructions from evenbalance.com but we try to enable admin from within the game it doesn't appear to work. Anyone know of any easy to follow instructions on how to do this?

Thanks in advance.

---

### Post by djdrsnuggles on 2007-06-10
That is very strange ... I'm a fresh noob with linux, I just installed Ubuntu Studio last weekend. I have used the bf1942 server in windows, with the exact network setup you have. I have never seen that. Have you tried to join your bf1942 server via the network games or internet games? Even with the same cdkey you should be able to join a network LAN game, and your server should show up in the LAN games list. Connect to the server using your LAN IP, instead of the WAN IP ??????

I hope you find a solution for this, as I want to run a bf1942 server too. LOL ... I havent been able to get past the EULA, when it asks me to accept or decline, I get:

Please type 'accept' or 'decline': accept
[: 19: ==: unexpected operator
[: 19: ==: unexpected operator
Please type 'accept' or 'decline': decline
[: 19: ==: unexpected operator
[: 19: ==: unexpected operator
Please type 'accept' or 'decline': 

Remember I have only been using linux for a week ... lol, but Ubuntu Studio pwns  !!

wO0t !!

---

### Post by barnydan on 2007-06-11
I have no solutions here.  I just wanted to say I tried installing bf1942 Linux server on 3 different computers running 3 different versions of ubuntu "Ubuntu studio, FeistyFawn and DapperDrake" and ran into the exact same problem. 

> Please type 'accept' or 'decline': accept
[: 19: ==: unexpected operator
[: 19: ==: unexpected operator
Please type 'accept' or 'decline': decline
[: 19: ==: unexpected operator
[: 19: ==: unexpected operator
Please type 'accept' or 'decline': 

I also installed bf1942 server on a Debian etch box and a Suse 10.2 box with no trouble at all. Exact same procedure.

One solution is to run a duel boot system with another distro of Linux.  It would be nice to get everything running in Ubuntu though.

---

### Post by tocleora on 2007-06-11
My problem was so simple it was too simple for tech support apparently... I don't remember exactly what it was called but there's an option to make it live and that was unchecked.  Once I made it live it worked perfectly.

I'm not sure why y'all are having that problem, I was able to install it without problems in Dapper (with the exception above obviously).  These are the instructions I followed, you might try and see if it works for you:

[http://www.sasklan.com/forum/index.php?showtopic=22148](http://www.sasklan.com/forum/index.php?showtopic=22148)

They are the official supporters as well (I believe) so you can ask them questions as well.  Also, If you'd like my help in any way let me know.

What file specifically are you downloading and having problem with? I'll see if I can test it from this side...

---

### Post by Blenderdan on 2007-06-11
Thanks tocleora!

The file is bf1942_lnxded-1.6-rc1.run  from [http://battlefield2.filefront.com/file/Battlefield_1942_Full_Linux_Server;23188x#1261011](http://battlefield2.filefront.com/file/Battlefield_1942_Full_Linux_Server;23188x#1261011)

I figured out our problem with some help from our fantastic Ubuntu community!  Thanks jrib

The script calls /bin/sh and has bashisms.

Ubuntu comes with Dash as the default shell, which is a trimmed down faster version that is a POSIX complaint shell.

The Solution is to uninstall Dash and leave Bash in its place. 

To do this type:
sudo dpkg-reconfigure dash
Select no

Now run the server again and it should run fine.

Thanks everyone.

---

### Post by Cheatsurfer on 2008-06-04
That certainly worked for me, and the install went fine. I had the server up and running for about a day, but now I'm getting this error:

> 2008-06-03 20:28:12 : Battlefield 1942 Server Manager v2.0 beta 4e
2008-06-03 20:28:12 : Started under Linux server652 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686
2008-06-03 20:28:12 : Couldn't bind server socket! Cannot assign requested address (99)

It crashed about two days ago, and now it won't run. I use the BFSMD (Black bag Ops Server Manager) to auto-admin, and configure the server, along with the BB Ops Remote Server Manager on my laptop. It all worked fine, then it crashed. I've tried Completely re-installing the server, to no avail. So whatever's happening, is coming from Ubuntu. I'm still a n00b with Linux as a whole, so I'm at a loss here.

The Server is roughly 4ghz, but the owner put the desktop version of Hardy on it, despite my warnings. Could it be a CPU/Networking functionality issue because of this?

---

### Post by BBQ'er on 2008-06-04
If you havent updated your pb (punkbuster) settings both server side and client side you're bound to run into trouble. Auto update works sometime  sometimes it doesn't. You can get more info about punkbuster and setup files here ... [http://evenbalance.com/index.php?page=support-bf1942.php]("http://evenbalance.com/index.php?page=support-bf1942.php") If you just plan on hosting it locally and playing locally just turn off pb. You wont need it (unless you think one of your buddies is hacking (8o|) 

G.L.

---

### Post by BBQ'er on 2008-06-04
Damn  My bad   didnt realize this was a yr old

---

### Post by Cheatsurfer on 2008-06-05
I already updated my Pb, that was pre-problem. So I'm still at a loss here.

---

### Post by Cheatsurfer on 2008-06-07
BUMP! C'mon Guys, I'm a n00b in distress! :(

---

### Post by BBQ'er on 2008-06-13
Sounds like you have firewall/port issues. A firewall Probably got installed with ubuntu and closed a port.

Take a look here and see if that will help you understand what ports to open. [http://portforward.com/cportsnotes/Battlefield1942/Battlefield1942.htm]("http://portforward.com/cportsnotes/Battlefield1942/Battlefield1942.htm")

---

### Post by drummingguy on 2008-06-25
If you still can't get to working go to your router ip (mine is 192.168.1.1 but it can be anything) type your username and pass and then click on games and apps and then DMZ find the server local ip and type that in the text box and click save now it should work it did for me.

Now I have a problem here I have the battlefield 1942 server running and my friends and everyone else can get on but when I get on it says "warring network problem" and  kicks everyone off the server (using the same ip). I used a proxy server still will not let me on is there a way to get another ip or allow the same ip on my server?

Thanks!

---

### Post by Jordysportracing on 2008-06-26
Does anyone know if Battlefield 2 works on ubuntu (i apologize i am almost a novice to ubuntu)

---

### Post by drummingguy on 2008-06-26
I'm not sure I all I heard is to use wine.

---

