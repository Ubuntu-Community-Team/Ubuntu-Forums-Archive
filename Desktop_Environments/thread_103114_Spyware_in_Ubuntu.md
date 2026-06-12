---
title: "Spyware in Ubuntu?"
date: 2005-12-13
forum: Desktop Environments
---

### Post by vtechstu on 2005-12-13
Everyone says spyware can't be on linux, etc.  Well I started getting a lot of spam mail from this particular email address( 10 times or so today).  So I went to send my Professor an email and I get an error that my Domain is blacklisted.  This only happens to due spyware sending out something on my computer.  So I checked the schools list of blacklisted IP's and low and behold mine is one of them.   So, how is spyware on my computer? How can I get rid of it?  Thanks.

---

### Post by earobinson on 2005-12-13
Contact the school admins ask them why you where baned and explain that you run linux.

I was banned from res nex due to running linux because the software they had to detect viruses on the network decided since my computer wasent windows / mac My computer must have a viruse. After I told the admins they quickly fixed the problem.

U of T FYI

I can tell you 100% that there is no spyware in the offical repos so unless you have been installing shady programs its not spyware

---

### Post by peteyp666 on 2005-12-13
are you running a mail server that is not behind a firewall?

---

### Post by leech on 2005-12-13
Yeah, that sounds like he has an open relay.  It's not so much the mail server not being behind the firewall, it is that authentication is needed to be set up for the mail server, otherwise spammers can use it for relayingn all their viagra ads.

Leech

---

### Post by vtechstu on 2005-12-13
Thanks everyone.  I contacted them as I made this post.  Once I told them I was on linux the lady forwarded my message to the people who control the list.  

In any event, how do I do go about this authentication.  All I'm running is Thunderbird for my school account.  I didn't think that needed anything extra.  Thanks anyway for all the help.

vtechstu = Virginia Tech Student, some people thought i was referring to honda engines :)

---

### Post by az on 2005-12-13
[QUOTE=vtechstu] All I'm running is Thunderbird for my school account.[/QUOTE]

Then, no, you are not running a mail server.  Never mind.

---

### Post by Ferrat on 2005-12-13
Any why would Linux be unable to run spyware ect? 

Trust me all OS are capable of running spyware, in linux it would be pretty simple.. 

1. Create a program (mail or whatnot) and insert a few extra lines of code ect. and say that the program needs sudo to run or something like that.. 

or

2. Take your spyware code and insert it in to a well known program sourcecode, complie or just let your "victim" do that and tada.. (yeah you would probably need to change a few things in the program to)

Sure Linux may not be as targeted as Windows but it can have spyware, its just a matter of code, windows spyware dont work on linux *doh* nither do windows exe but linux can run programs all the same the code is just diffirent, i even be able to integrate it to the kernel would be my guess, if one really wanted to.

---

### Post by az on 2005-12-13
[QUOTE=Ferrat]Any why would Linux be unable to run spyware ect? 

Trust me all OS are capable of running spyware, in linux it would be pretty simple.. 

1. Create a program (mail or whatnot) and insert a few extra lines of code ect. and say that the program needs sudo to run or something like that.. 

or

2. Take your spyware code and insert it in to a well known program sourcecode, complie or just let your "victim" do that and tada.. (yeah you would probably need to change a few things in the program to)

Sure Linux may not be as targeted as Windows but it can have spyware, its just a matter of code, windows spyware dont work on linux *doh* nither do windows exe but linux can run programs all the same the code is just diffirent, i even be able to integrate it to the kernel would be my guess, if one really wanted to.[/QUOTE]

Sure, but there are also a lot more people looking at the code.  Your malicious addition would not last long.  Not to mention that not just anyone can upload a patch to a project's source.  You have to get known and even then, your patched will  be auditted before being included in the application.

The fact that the software in Ubuntu comes from an official repository prevents/discourages people from installing things willy-nilly.

What you are describing is the equivalent to a windows .bat file named RunMe.BAT which contains the line

format c:

---

### Post by earobinson on 2005-12-13
if you only install stuff from offical repositories I can tell you 100% no spyware, it would be found very fast

---

### Post by astoltz on 2005-12-13
I got blacklisted once.  It turns out the dude that had my IP address before I did (dynamic IP) did the spamming.

Just something to consider.

---

### Post by silex on 2005-12-13
I'm surprised they would just block IPs when everyone is on a dynamic IP.  My school's IT admins tend to block by MAC address.  I guess you can still get around it, but its an inconvenience.

---

### Post by JoshHendo on 2005-12-13
Normally spyware can't AFFECT linux, though linux can be a CARRIER.

---

### Post by Ferrat on 2005-12-13
Sure linux code is more closely watch ect. but thinking that linux can't get subjected to spyware/adware/viruses and so on is naiv and very very bad since ppl stop looking for it then, sure it can't get windows based shit but it can still get shit :P 

Never fully trust code you haven't written youself and even then, be suspicious ^^

---

### Post by az on 2005-12-14
[QUOTE=Ferrat] is naiv and very very bad since ppl stop looking for it then, sure it can't get windows based shit but it can still get shit :P [/QUOTE]

Professional support means in great deal security infrastructure.  I highly doubt anyone would use an OS that had lax security.  The FLOSS developmental model is seen as a benefit to securoty, and not a liablility.  "Security by obscuroty" does not work as well as the open approach.

[QUOTE=Ferrat]Never fully trust code you haven't written youself and even then, be suspicious ^^[/QUOTE]

So, you wrote the OS you are using from the ground up?

---

### Post by linbetwin on 2005-12-14
[quote=azz]So, you wrote the OS you are using from the ground up?[/quote]After inventing the language in which he wrote the OS.

---

### Post by briancurtin on 2005-12-14
[QUOTE=silex]I'm surprised they would just block IPs when everyone is on a dynamic IP.  My school's IT admins tend to block by MAC address.  I guess you can still get around it, but its an inconvenience.[/QUOTE]
mine school uses VLANs. if your box fails a scan, which they run on the systems once a week i think, you get moved into a quarantined VLAN until you can pass their little virus/spyware/etc test

---

### Post by peteyp666 on 2005-12-15
[QUOTE=vtechstu]Everyone says spyware can't be on linux, etc.  Well I started getting a lot of spam mail from this particular email address( 10 times or so today).  So I went to send my Professor an email and I get an error that my Domain is blacklisted.  This only happens to due spyware sending out something on my computer.  So I checked the schools list of blacklisted IP's and low and behold mine is one of them.   So, how is spyware on my computer? How can I get rid of it?  Thanks.[/QUOTE]

What Domain is blacklisted?  What mail server are you connecting to, to send the mail?

---

