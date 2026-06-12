---
title: "Parental Controls : Automatix anyone ... please?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by christmasisland on 2006-06-11
Hi,

So I want to switch from Microsoft/Apple to Linux. I have two children 10 and 14, they are responsible, adept, and computer savvy. I do not want to censor but protect them from the content we, as a family, agree is unsuitable.

I currently use Blue Coat K9 Web Protection on Windows, a free filtering product to accomplish the above goals.

I have tried ... really, really tried, to get DansGuardian working by following this and other forums without success. The last try the internet stopped working completely and since I was blindly following a list of todo's, I didn't know what I was doing and didn't know how to fix the problem and I had to reinstall.

Why isn't there an "Automatix" type solution to time restrictions, content filtering, IM restrictions and other parental filtering options available in Ubuntu?

Just based on the number of thread views for a parental control search shows a big interest in this problem.

Thanks for listening ... Mike

---

### Post by matthew on 2006-06-11
[quote=christmasisland]Why isn't there an "Automatix" type solution to time restrictions, content filtering, IM restrictions and other parental filtering options available in Ubuntu?[/quote]Automatix was written by a volunteer who had a personal interest in creating it. If someone wants to step up and write something like you are requesting I'm certain it would be welcome.

---

### Post by NeghVar on 2006-06-11
I'm not sure what comes with EUbuntu as I've never used it but does it come with this type of thing already installed in some fashion? I would imagine that since it is developed mostly for schools and younger people it would have some kind of overly archaic censor idea.

---

### Post by christmasisland on 2006-06-11
[QUOTE=matthew]If someone wants to step up and write something like you are requesting I'm certain it would be welcome.[/QUOTE]

How do I make a request like that?

---

### Post by matthew on 2006-06-11
[quote=christmasisland]How do I make a request like that?[/quote]If no one responds in this thread in the next few days (which I still hope someone will), head over to the [programming talk forum]("http://ubuntuforums.org/forumdisplay.php?f=39") and start a new thread...title it something like "anyone interested in helping with parental controls?" and in the text of your post describe what you want and politely ask if anyone there is able/willing/interested in creating such a thing. You might want to provide a link to this thread as well so people have a little background as to what you have tried.

---

### Post by christmasisland on 2006-06-11
I'll do that ... thank you very much for your guidance.

Mike

---

### Post by leech on 2006-06-11
Ever looked into Dan's Guardian?  Basically it's just a proxy (you can run it on the local system too) that you could lock all the accounts that you want to control the content for web browsing at least.  It works quite well, is free for non-commercial use and wasn't all that hard to set up.  I set it up on an OpenBSD system, which is normally a pain in the butt to set ANYTHING up on (but then that's why it's so secure.  Nothing is installed by default.)

Also apparently there is a Bounty for this already.

[https://launchpad.net/bounties/eric.duveau](https://launchpad.net/bounties/eric.duveau)

Good luck, I'm curious about this myself.

Also check this out [http://www.glaxstar.com/](http://www.glaxstar.com/) Profile extensions for Firefox.

Leech

---

### Post by christmasisland on 2006-06-12
[QUOTE=leech]Ever looked into Dan's Guardian?  Basically it's just a proxy (you can run it on the local system too) that you could lock all the accounts that you want to control the content for web browsing at least.  It works quite well, is free for non-commercial use and wasn't all that hard to set up.  I set it up on an OpenBSD system, which is normally a pain in the butt to set ANYTHING up on (but then that's why it's so secure.  Nothing is installed by default.)

Also apparently there is a Bounty for this already.

[https://launchpad.net/bounties/eric.duveau](https://launchpad.net/bounties/eric.duveau)

Good luck, I'm curious about this myself.

Also check this out [http://www.glaxstar.com/](http://www.glaxstar.com/) Profile extensions for Firefox.

Leech[/QUOTE]
I've been following the bounty and the threads on this forum (eric.duveau listed a howto in one) and I couldn't get them to work.

Glaxstar.com doesn't fit my needs, DansGuardian or Willow is perfect if I could get it to work easily with a proxy and with or without iptables. 

The problem is there doesn't seem to be a Ubuntu HOWTO that is clearly written. In a perfect world I could run a script that does everything for me while allowing me to select the options I need.

Maybe it's just me, but this situation is why people stay with Windows and why I can't get my friends to migrate to Linux, yet.

Mike

---

### Post by chago on 2006-06-13
Maybe this will help: [http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

---

### Post by christmasisland on 2006-06-13
[QUOTE=chago]Maybe this will help: [http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)[/QUOTE]

I followed his directions a few weeks ago and found problems. They are documented at the end of the page in the comment section. It turns out the directions are wrong and haven't been fixed yet.

Mike

---

### Post by greenstar on 2006-06-21
I usually don't use Automatix, but have a few times in the past when I need to get a desktop box up and running *fast*. 

However, I'd love to have an application to help parents put limits on children's internet access. 

I have many customers who are parents and want to have more control over their box, but don't know how. There are multiple solutions I can recommend to users of that *other* commercial OS, any of which I have no trouble helping my customers install, configure and administer. However, I don't currently know of a solution that I can recommend and implement for my customers that use Ubuntu. I'd love to have an answer to this problem as it's one of the few things I don't know how to set up for my Ubuntu customers. 

It's amazing how far Ubuntu has come in the last 2 years. What started out as a good, sturdy, basic OS has turned into a highly polished, extremely useable and endlessly configurable OS that has software packages available for just about any purpose, with very few exceptions.

greenstar

---

### Post by lindyslack on 2006-06-21
This is not Ubunt but still Linux so... We use a smoothwall router in our house for this...

Basicly it's just an old computer with two network cards in it (I recomend using two different cards like a realtek and a 3com).

The directions are pretty clear in the homebrew section of their site for setting up a smoothwall firewall / router with Dansguardian and clam a/v. Scans all files coming into the network for virus infection and block content we do not find appropriate for our household.

I have also implmented this same smoothwall solution for several companies who want to control the content and files accessed via the internet...

[http://www.smoothwall.org/]("http://www.smoothwall.org/")

and here is detailed directions.

[http://community.smoothwall.org/forum/viewtopic.php?t=8741]("http://community.smoothwall.org/forum/viewtopic.php?t=8741")

There are links in this post for DansGuardian with Clam A/V as well as DansGuardian GUI so you can admin the system from the web based interface..

Just need an old 233 (or smaller - or faster) and a few network cards...

---

### Post by greenstar on 2006-06-22
lindyslack:

Thanks for the great info. I'll be looking into this.


greenstar

---

### Post by cazinpa on 2006-06-23
I am working on a custom edubuntu live cd for this. I have a downloadable ISO if you are interested. I just have to figure out how to get it to you ;-P Anyone have a good place to upload it?

It is edubuntu with a few things removed, and dansguardian/tinyproxy added to it. I have also locked down firefox to keep anyone from changing the proxy settings.

It also uses the Dapper live installer which configures your system for you. It is as easy as installing Dapper!

It is stil a work in process. I have to lock down a few more things, and the only thing using the proxy at the moment is firefox.

Please contact me if you are interested!

I am calling it Edubuntu-Guardian at the moment. I did it for my own uses - and to give to friends and family who ask me about how to keep their kids safe on the internet.

Thanks,
Andy Zook

---

### Post by stychman on 2006-06-24
When you find a place to host it let us know.  I'd love to give it a try and let you know how things work!

---

### Post by Hairy_Palms on 2006-06-24
have you checked out procon?
[http://procon.mozdev.org/](http://procon.mozdev.org/)
its a firefox extension that filters things quite well
also if you want to make it imposible to disable/uninstall just take away write access to the extensions directory and it cant be uninstalled/disabled.

---

### Post by cazinpa on 2006-06-24
Check it out here-

[http://home.pdqlocks.com/guardian/](http://home.pdqlocks.com/guardian/)

I will find another place to host it if your guys slaughter my server ;-P

Let me know what you think!

Andy

---

### Post by cazinpa on 2006-06-27
Hey all,

I have done some more work on this. It now has Tinyproxy for the proxy server, dansguardian to filter, and I have installed Apache and SRG along with a cron job that creates a web history list from the Dansguardian logs.

Ideally I meant it for something that parents can use for their kids, but it also works quite splendidly on a company network to filter and view internet traffic.

I know a few people have downloaded it already - what did you think? Comments? Suggestions?

Thanks!

Andy Zook

---

### Post by eric.duveau on 2006-07-06
Seems very interesting. To Share it you can have a look at [http://gshare.info](http://gshare.info)
Other wise I would like to test it. Could you tell me where I can download it

eric.duveau

---

### Post by eric.duveau on 2006-07-06
From Where can we download it?
[QUOTE=cazinpa]Hey all,

I have done some more work on this. It now has Tinyproxy for the proxy server, dansguardian to filter, and I have installed Apache and SRG along with a cron job that creates a web history list from the Dansguardian logs.

Ideally I meant it for something that parents can use for their kids, but it also works quite splendidly on a company network to filter and view internet traffic.

I know a few people have downloaded it already - what did you think? Comments? Suggestions?

Thanks!
Andy Zook[/QUOTE]

---

### Post by Appolusionist on 2006-07-06
[QUOTE=christmasisland]I followed his directions a few weeks ago and found problems. They are documented at the end of the page in the comment section. It turns out the directions are wrong and haven't been fixed yet.

Mike[/QUOTE]

I have TinyProxy/DansGuardian working correctly with Dapper. Let me back track the steps I took and give you my configuration. I have included the specific changes I made in the config files.

Install dansguardian, tinyproxy, and firehol

```
sudo apt-get install dansguardian tinyproxy firehol
```

Edit /etc/dansguardian/dansguardian.conf...

```
sudo nano -w /etc/dansguardian/dansguardian.conf
```

and leave everything at default. You will just need to comment out the UNCONFIGURED line

```
# Comment this line out once you have modified this file to suit your needs
#UNCONFIGURED
```

Next, you will need to edit the tinyproxy.conf

```
sudo nano -w /etc/tinyproxy/tinyproxy.conf
```

and make the following changes

```
##
## tinyproxy.conf -- tinyproxy daemon configuration file
##

#
# Name of the user the tinyproxy daemon should switch to after the port
# has been bound.
#
User nobody
Group nogroup

#
# Port to listen on.
#
#Port 8888
Port 3128
```

Now the last file to be edited is /etc/firehol/firehol.conf

```
sudo nano -w /etc/firehol/firehol.conf
```

and here is my entire firehol.conf file

```
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "nobody root"

# Accept all client traffic on any interface
interface any world
	policy drop
	protection strong
	client all accept
```

Then restart the services

```
sudo /etc/init.d/dansguardian restart
sudo /etc/init.d/tinyproxy restart
sudo /etc/init.d/firehol restart
```

You should now have a working internet filter without any changes being made to the proxy settings.

---

### Post by christmasisland on 2006-07-26
I followed your directions and it did not work.

---

### Post by christmasisland on 2006-07-26
I followed this thread [http://ubuntuforums.org/showthread.php?t=218906&highlight=dansguardian+proxy]("http://ubuntuforums.org/showthread.php?t=218906&highlight=dansguardian+proxy") and it worked ... I think it was here:
> 4. Edit: sudo gedit /etc/default/firehol

START_FIREHOL=YES

This is to allow restarting of the firewall.

The firehol default is START_FIREHOL=NO

It has taken a long time to get this to work ... ](*,) 

Thanks,
Mike

---

### Post by kikinovak on 2006-07-26
If you want to filter web content, then squid is your friend.

When I was the age of your kids, things were much easier. My parents hid The Complete Henry Miller or Alex Comfort's "Joy Of Sex" behind the "Brockhaus Enzyklopädie" high up on the shelves, so it only took me a ladder to grab them. But then, that stuff was nothing compared to what you can find on [http://www.rotten.com](http://www.rotten.com) or similar sites. 

I've been working as a teacher for some time in a public school in France. If you want to see a list of the worse sites the Internet has to offer, check the browser's history list after a class of 14-year old youngsters has made their visit.

Cheers.

---

### Post by eric.duveau on 2006-07-27
> **leech said:**
> Ever looked into Dan's Guardian?  Basically it's just a proxy (you can run it on the local system too) that you could lock all the accounts that you want to control the content for web browsing at least.  It works quite well, is free for non-commercial use and wasn't all that hard to set up.  I set it up on an OpenBSD system, which is normally a pain in the butt to set ANYTHING up on (but then that's why it's so secure.  Nothing is installed by default.)

Also apparently there is a Bounty for this already.

[https://launchpad.net/bounties/eric.duveau](https://launchpad.net/bounties/eric.duveau)

Good luck, I'm curious about this myself.

Also check this out [http://www.glaxstar.com/](http://www.glaxstar.com/) Profile extensions for Firefox.

Leech


Please have a look at the attached file

To install the package (built by nanomad), you have to:
1) extract it to a directory
2) directory#./run_me.sh

This package is designed to work on a fresh dapper install.

If you find some bug please report to the designer:
condellog (at) gmail.com

---

### Post by cre8ivgil on 2006-07-28
Excellent idea, however after installing I was not able to connect to about 99% of all web sites. I know it has to do with the settings, so my question is this..Are you going to post some type of guide on how to fine tune this puppy? Hopefully it would stop blocking all my everyday legitimate sites. I would also like to personally thank you for putting in the effort to bring something like this to linux for all the newbies like myself.

---

### Post by cre8ivgil on 2006-07-29
> **christmasisland said:**
> I followed this thread [http://ubuntuforums.org/showthread.php?t=218906&highlight=dansguardian+proxy]("http://ubuntuforums.org/showthread.php?t=218906&highlight=dansguardian+proxy") and it worked ... I think it was here:

The firehol default is START_FIREHOL=NO

It has taken a long time to get this to work ... ](*,) 

Thanks,
Mike

I've changed the YES to NO as suggested above and now I am connecting. Thanks for all the help in this forum.

---

### Post by eric.duveau on 2006-08-03
> **cre8ivgil said:**
> Excellent idea, however after installing I was not able to connect to about 99% of all web sites. I know it has to do with the settings, so my question is this..Are you going to post some type of guide on how to fine tune this puppy? Hopefully it would stop blocking all my everyday legitimate sites. I would also like to personally thank you for putting in the effort to bring something like this to linux for all the newbies like myself.

One thing you need to know is the configuration files are under _/etc/dansguardian:_

Use your favorite text editor to change them

for examples:
[LIST]
[*]**exceptionsitelist:** allow all sites in this file
[*]**dansguardianf1.conf:** where you can increase 
naughtynesslimit (now = 50)
[/LIST]

I hope this hints can help you. Tell me if you need more information.
:grin:

---

### Post by saxaphone_man on 2006-11-26
I have a similarish problem, can anyone help me at [http://ubuntuforums.org/showthread.php?p=1809536](http://ubuntuforums.org/showthread.php?p=1809536) ?

Can I use SmoothWall to do what I want there?

---

### Post by prezbedard on 2007-01-29
Will this configuration work in a network setting or are there some addtional steps I need? Say I build this and set the machine as the proxy server/ default gateway? I am currently using something that is not as flexible and can only filter urls. I would like to implement this since I now have a better knowledge of ubuntu. 

Thanks,

> **Appolusionist said:**
> I have TinyProxy/DansGuardian working correctly with Dapper. Let me back track the steps I took and give you my configuration. I have included the specific changes I made in the config files.

Install dansguardian, tinyproxy, and firehol

```
sudo apt-get install dansguardian tinyproxy firehol
```

Edit /etc/dansguardian/dansguardian.conf...

```
sudo nano -w /etc/dansguardian/dansguardian.conf
```

and leave everything at default. You will just need to comment out the UNCONFIGURED line

```
# Comment this line out once you have modified this file to suit your needs
#UNCONFIGURED
```

Next, you will need to edit the tinyproxy.conf

```
sudo nano -w /etc/tinyproxy/tinyproxy.conf
```

and make the following changes

```
##
## tinyproxy.conf -- tinyproxy daemon configuration file
##

#
# Name of the user the tinyproxy daemon should switch to after the port
# has been bound.
#
User nobody
Group nogroup

#
# Port to listen on.
#
#Port 8888
Port 3128
```

Now the last file to be edited is /etc/firehol/firehol.conf

```
sudo nano -w /etc/firehol/firehol.conf
```

and here is my entire firehol.conf file

```
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "nobody root"

# Accept all client traffic on any interface
interface any world
	policy drop
	protection strong
	client all accept
```

Then restart the services

```
sudo /etc/init.d/dansguardian restart
sudo /etc/init.d/tinyproxy restart
sudo /etc/init.d/firehol restart
```

You should now have a working internet filter without any changes being made to the proxy settings.

---

### Post by silentvirus on 2007-03-13
Heard of [Ubuntu Christian Edition]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html")? Sounds like a good fit for you and your family. I don't use it personally as I like the use of Tor, but we use it at my church and it has filtering installed and running by default.
[URL="http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html"]
http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html[/URL]

---

### Post by mysteryous on 2008-05-19
I wanted to relate that I used iptables instead of firehol to get a proxy and DansGuardian to work.

The first command I used was to allow only *root,* *dansguardian,* and the *proxy* user (for Squid in my setup) to be able to access port 80 and the rest to be redirected to port 8080:
```
sudo iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -m owner ! --uid-owner proxy -m owner ! --uid-owner 118  -j REDIRECT --to-ports 8080
```
Of course, there may be no use in putting the Dansguardian user.  Remember to write in the specific users on your system.  The "-m owner ! --uid-owner root" attributes check for and relates not to redirect the root user's packets.

The second prevents access from a browser directly to the proxy on port 3128:
```

sudo iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j REJECT --reject-with icmp-host-prohibited
```

I used some ideas from:
Joe Bolin [http://www.linux.com/articles/113733]("http://www.linux.com/articles/113733")
Olli Savolainen [http://www.pilpi.net/journal/item-985.php]("http://www.pilpi.net/journal/item-985.php")

---

