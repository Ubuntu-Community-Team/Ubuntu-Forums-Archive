---
title: "Continued problems with connecting to repositories"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Rennie on 2006-06-30
Hi,

I am relatively new to Linux, so appreciate any help i can get.

I have a fresh install on a dual boot Dapper/XP notebook, and have finally got the linux platform to see the net (it was the IPV6 fix).

I am on adsl through a DSL-604G modem/router, using DHCP and wired connection at the moment (wireless not yet working).

I am having repeated problems with installing packages, and using the apt-get update command.. This is what I get..

[I]root@pduncan-laptop:/# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
root@pduncan-laptop:/# sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg
  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://www.beerorkid.com/automatix/apt/dists/dapper/Release.gpg](http://www.beerorkid.com/automatix/apt/dists/dapper/Release.gpg)  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]


I have tried to delete the line from etc/apt.conf but to no avail.  I can go directly to the http sites at archive.ubuntu.com via firefox no problems.

Also I have tried to install skype and other non core packages, but any 'add-on' libraries or other packages cannot be downloaded from anywhere.  Interestingly, this seemed to work for 2 mins, allowing the Synaptic manager to download the index of 90 updates, but wont let me download them!!

I believe it may be to do with the router??  I am bit worried about the 1.0.0.0 that it is attaching to the target sites.  Weird?

Any ideas??  I really want to convert to Linux, but without skype and some updates this may prove frustrating.

Much appreciated..  :D

---

### Post by nanotube on 2006-06-30
can you post your /etc/apt/apt.conf here, and also maybe /etc/resolv.conf?

---

### Post by Rennie on 2006-06-30
Ok, here is /etc/apt/apt.conf 

Acquire::http::Proxy "false";

And /etc/resolv.conf

nameserver 10.1.1.1

My router IP address changed from 192.168.0.1 about 6 months ago when i flashed it with some new firmware for WPA support.  XP has been using it with WPA encryption for around 6 months no probs.

Also, route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

Thanks!

---

### Post by nanotube on 2006-06-30
ok, well, 1st thing to try - completely remove the apt.conf file (well, you could mv it to your home dir for backup just in case), and try again

2nd thing to try - find your actual nameservers (through your router config page), and put those in instead of the nameserver line you have now, and try again.

---

### Post by snowdogdb on 2006-06-30
Hi - I am having similar problems.  No proxy here. Any help?

When I run apt-get update, this is what I see:
sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg                                             
  Connection failed [IP: 146.137.96.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release                             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg    
  Connection failed [IP: 85.133.25.8 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 146.137.96.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources 
  Connection failed [IP: 146.137.96.15 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 146.137.96.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nanotube on 2006-06-30
if you have no apt.conf, then just try step #2 (with the resolf.conf)

---

### Post by Rennie on 2006-07-01
Hi, 

I have tried both fixes and no difference..

Could it have something to do with the reference to 1.0.0.0 for the IP address that the update is trying to access??  this doesnt sound right to me.

Ideas??

Should i reset my dsl router to try and resolve this?? i will lose my WPA settings, but no big problem i suppose..

Cheers

---

### Post by nanotube on 2006-07-01
[QUOTE=Rennie]Hi, 

I have tried both fixes and no difference..

Could it have something to do with the reference to 1.0.0.0 for the IP address that the update is trying to access??  this doesnt sound right to me.

Ideas??

Should i reset my dsl router to try and resolve this?? i will lose my WPA settings, but no big problem i suppose..

Cheers[/QUOTE]
yes, that 1.0.0.0 for IP does not sound right to me, either. that's why i told you to try and play with the resolv.conf...

what do you get if you try from commandline
nslookup archive.ubuntu.com

also, what happens if you connect directly to your dsl modem, without using your wifi router? (just to try and see if this problem is due to the router, or not?)

---

### Post by stonefeet on 2006-07-03
i'd like to weigh in on this subject
first off i've been a life long windows user, i got sick of their stupid live update thing and decided to give ubuntu a try, it's tough to get used to that's for sure, these forums have helped me along greatly so far with solving the minor issues i've had

i had this problem for the first few days i used ubuntu

i got rid of the apt.conf and then edited the resolv.conf and that completely shutdown my internet connection, then i just re-edited it again and the updates came through without a problem. kinda weird way to fix the problem but that's what worked for me

hopefully it helps someone else and gets them off windows

well upon further review
i was able to get to and download the packages i needed from the repositories, but the software updates is giving me the same message as above
ah well, the battle continues

new update
so i was off to try to see if i could get gaim to connect, i found a trick on here by pinging the aol login ip and it worked, then i tried the updates and they now work 100%
odd

---

### Post by Rennie on 2006-07-07
Hi all, 

Thanks for the responses.. 

nanotube - currently resolv.conf is blank.  i cleared it as a result of earlier advice.
This is what i get with the shell..

pduncan@pduncan-laptop:~$ nslookup archive.ubuntu.com
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   archive.ubuntu.com
Address: 85.133.25.8
Name:   archive.ubuntu.com
Address: 85.133.25.7

Does that help?? Doesnt mean much to me.

And i cant connect directly.  Its a combined modem/router.  I havent been able to connect wirelessly, so i am currently connecting through a ethernet connection, which is all i can do.  any other ideas?

also, the apt.conf has been deleted (moved) to my home folder, so it cant be seen.  contents of this are

Acquire::http::Proxy "false";

this doesnt look good to me either.

Stonefeet, thanks for your reply.  this sort of trial and error (why things work once after not working before) doesnt give me much confidence in linux, after all the great things i hear at work (we run dual XP/SuSe systems).

Can someone please show me what sucessful resolv.conf and apt.conf files look like?? then maybe i can find out why mine done work?

Also, my ADSL router is a D-link DSL504, which may be the cause of some of these problems. I thought i had an old DSL500 modem which i could try to see if it was the router settings.

thanks for your ideas.

Rennie

---

### Post by nanotube on 2006-07-07
hey rennie
well, trying the other version of a modem might be a good idea, because i can't think what else it could be.

for the record, by apt.conf does not exist (has not existed in breezy, and still does not exist after upgrade), and by resolv.conf has just one line in it, with the nameserver set to my wireless router my dhcp, like this:
```
nameserver 192.168.2.1
```

so.. nothing fancy.
so try the other modem, and see :)

---

### Post by terrapin on 2006-07-07
Removing /etc/apt/apt.conf did it for me.  Thanks!8)

---

### Post by stonefeet on 2006-07-07
> **Rennie said:**
> Hi all, 

Thanks for the responses.. 

nanotube - currently resolv.conf is blank.  i cleared it as a result of earlier advice.
This is what i get with the shell..

pduncan@pduncan-laptop:~$ nslookup archive.ubuntu.com
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   archive.ubuntu.com
Address: 85.133.25.8
Name:   archive.ubuntu.com
Address: 85.133.25.7

Does that help?? Doesnt mean much to me.

And i cant connect directly.  Its a combined modem/router.  I havent been able to connect wirelessly, so i am currently connecting through a ethernet connection, which is all i can do.  any other ideas?

also, the apt.conf has been deleted (moved) to my home folder, so it cant be seen.  contents of this are

Acquire::http::Proxy "false";

this doesnt look good to me either.

Stonefeet, thanks for your reply.  this sort of trial and error (why things work once after not working before) doesnt give me much confidence in linux, after all the great things i hear at work (we run dual XP/SuSe systems).

Can someone please show me what sucessful resolv.conf and apt.conf files look like?? then maybe i can find out why mine done work?

Also, my ADSL router is a D-link DSL504, which may be the cause of some of these problems. I thought i had an old DSL500 modem which i could try to see if it was the router settings.

thanks for your ideas.

Rennie

no problem, i'm STILL actually having similar problems to yours
i was able to nab a free pc (minus HDD) from work to play around with ubuntu and see if i could get it to work, after about a week of searching high and low my problem continues

an easy example
when trying to update repositories i have to do an nslookup of all of the addresses it has to access to update
archive.ubuntu.com
us.archive.ubuntu.com
security.ubuntu.com
and so on
then the repositories work with no problem, for a bit, then it's back to the ole 101 network unreachable
sometimes the nslookup doesn't return a response after it's worked once
i even have to do it for torrent trackers to get them to work, or connect to aim
all the while firefox can browse away no problem

i've tried just about everything i can think of, connecting directly to modem, same problem, static ip....same problem
messing with resolv.conf and apt.conf

real strange

---

### Post by Rennie on 2006-07-09
Hi Stonefeet,

I agree, these problems are quite strange and I am frustrated that the standard build doesnt explain nor deal with a problem that many users seem to have.

I will push ahead, but also do some research on finding a different Linux platform to build.. 'fraid my patience with ubuntu is running out.

Cant run skype, cant update packages, not much use running pc in ubuntu.

Rennie

---

### Post by lazyrussian on 2006-07-09
I actually had a similar problem.
I was installing on my laptop while traveling. When I got home I tried updating and nothing worked.
I tried doing a fresh install (without being jacked into the net....same problem).

Then I turned on my wireless and did another fresh install and eveyrthign started working. No clue why. Bt it seems to me that If I install dapper without being online, nothing is able to update.

---

### Post by Rennie on 2006-07-09
Hi all,

quick update.. I decided to do a fresh install, while connected by ethernet (i think i was originally on wireless with 1st install.)

what do you know?? it works!! WOW

No idea why, maybe it could configure itself while building apt during install..

Im happy!  Thanks for all your ideas.

Now, to get skype to work...

---

### Post by Rennie on 2006-07-09
Hmm, another update.. doesnt actually work afterall!!

During the install it noted that it couldnt contact any of the repositories, so it commented them out.

So when i do a apt-get update, it doesnt see any sites to update with!! haha

So im back to square one.  

time to get a new router/modem me thinks

rennie

---

