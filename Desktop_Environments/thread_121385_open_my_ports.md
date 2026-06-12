---
title: "open my ports"
date: 2006-01-25
forum: Desktop Environments
---

### Post by jabb0 on 2006-01-25
Tryin to get the whole port forwarding thing to work - i got my router set up methinks - not 100% on that, i did what i was told but it still wont happen.

Running LAMP on ubuntu - and want to access a site im developing from outside my LAN.

Now i think, im not sure, but i think that it might have something to do with Ubuntu having no ports open by default.

How do i go about opening one to access my local webserver from outside?

plz help 
cheers

---

### Post by dcstar on 2006-01-25
[QUOTE=jabb0]Tryin to get the whole port forwarding thing to work - i got my router set up methinks - not 100% on that, i did what i was told but it still wont happen.

Running LAMP on ubuntu - and want to access a site im developing from outside my LAN.

Now i think, im not sure, but i think that it might have something to do with Ubuntu having no ports open by default.

How do i go about opening one to access my local webserver from outside?

plz help 
cheers[/QUOTE]
AFAIK, unless you have iptables installed, Ubuntu does not "close" any ports.

You should focus on setting your router to port translate to Port 80 of your system's IP address (assuming your system has a web server running on that port).

---

### Post by cwaldbieser on 2006-01-25
[QUOTE=jabb0]Tryin to get the whole port forwarding thing to work - i got my router set up methinks - not 100% on that, i did what i was told but it still wont happen.

Running LAMP on ubuntu - and want to access a site im developing from outside my LAN.

Now i think, im not sure, but i think that it might have something to do with Ubuntu having no ports open by default.

How do i go about opening one to access my local webserver from outside?

plz help 
cheers[/QUOTE]

"Having no ports open by default" really just means Ubuntu has no servers running by default.  There are no default firewall rules built in to drop traffic to specific ports since there is no need.

Your router is the key to accessing your internal web server.  It has to forward traffic it receives on port 80 to your internal machine.

If you plug into a DSL modem, they can sometimes be configured to block ports, too.

---

### Post by jabb0 on 2006-01-25
Heya, thats handy info thx.

I wonder if you could perhaps help me a lil further.

I have a netgear router which is acting up - i have remote management turned off yet connect to my static ip without specifying a port number and you can login to my router and change stuff (course u need the password). Howeer if you specify port 80 it lets u in too.

Specify a port number (even that one specified in the disabled remote management settings :8080) and the connection is refused.

I dunno wot to make of this. Why is the router accepting remote management on port 80 (whther u specify port# or not), when it definitly turned off?

---

### Post by linuxfan on 2006-01-26
If you have turned off remote mgmt, you *MUST* not be able to login remotely. Check Netgear website for any firmware upgrades ... you may be in serious trouble if your Netgear is leaking. Netgear also recommends you to change the default "admin" account user id ... check if your Netgear supports this feature. If you must use remote admin, make sure your password is *STRONG* and your user id is other than "admin".

To enable you to connect to your webserver inside your LAN from outside, you will first need to "port forward" on your Netgear. By default, your Netgear will not listen and forward traffic [ just like base ubuntu install ;-) ]. Logon to your Netgear via browser interface and do the following ...

1) Go to "port forwarding" and choose the HTTP service (usually port 80).
2) Enter the private ip of your internal host running webserver (ex: 192.168.1.22) and the port number you're running webserver (usually also 80, unless you have changed it to run on another port).
3) By default no programs listen on any ports in your ubuntu. Hence, use Firestarter GUI to create a policy to allow incoming HTTP (port 80) traffic.

If you don't have Firestarter, search forum for this and you'll see several messages. I used "Automatix" to install Firestarter.

---

### Post by jabb0 on 2006-01-26
I think this was all my fault - somewho i managed to convince my self that i could use my compo as a webserver - then use the browser on this compo to type in my ip address -- i thought there was somehing fishy about what i was doing but i carried on regardless tearing my hair out and shouting obscenities at the screen.

But when i got a mate to do the same thing, from a compo comepletely seperate from my LAN they got it to work, folowed by 2 other mates.. so YEY - i guess :cool:

I was creamin it yesterday i thought i had a dud router that wanted to string me up by the balls - no matter what i told it to do!!!

Thanx a million for your help folks

to go one step further, ill need to keep this setup for a few months, which is ample time for a cracker to make my lil linux box explode (or something), i have set things up so that my root web dir is empty - then i have a folder in my home dir which i use for local development (phpMyAdmin is in here), i link this using the alias file - then in this dir i have another called public, but i have used the alias file to make it look like its on the same level as the dir i is in.

1) can someone find out my dir paths specified in the alias file?
2) have i painted a big red target on my forehead for crackers to aim at?

As i said i only need this until June - and there will be a max of 6 trusted ppl knowing the actual details.

3) do u have any other thoughts that might be useful?
4) can google find me? I defo don want that

again THANX A MILLION

---

