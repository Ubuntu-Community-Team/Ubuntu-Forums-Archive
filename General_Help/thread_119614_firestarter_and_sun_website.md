---
title: "firestarter and sun website"
date: 2006-01-19
forum: General Help
---

### Post by ashokpappu on 2006-01-19
Hello All,

I am having a issue with fire starter.  the minute I start firestarter I am unable to browse any of sun's website (like wwws.sun.com,java.sun.com...)  Every other website seems to be working.  Infact I can see that the sun website is being blocked by firestarter as I can see the the firestarter log.  Pretty much all the websites seem to work other than sun.   Any ideas on how to resolve this issue.

---

### Post by linuxfan on 2006-01-22
Hi,

I have a similar problem too although I can access java.sun.com. For me, I just can't access [www.zdnet.com](www.zdnet.com)  or  [www.cnet.com](www.cnet.com). A pop appears and states that the site returned no data. I can access the same site perfectly well with FireFox running on Win98SE. I use a DSL modem-router and hence share the same Internet IP for my home network. Something's happenning???

Wierd problem ... and 18 views of this post has still not provided a clue :-(

Can any guru(s) online revert?

Cheers

---

### Post by mikkelwe on 2006-01-23
Open the firestarter window and click the events tab. Then visit the web page in firefox or whatever browser you use. Next look for the event that caused it to be blocked in the firestarter window. Now you should be able to right click the event an create an appropiate rule.

---

### Post by skaboss on 2006-01-23
I had the same problem : couldn't access some sites (java.sun.com), couldn't listen to some shoutcast streams, had low ids on amule (although i opened the required ports), and so on...
I tried guarddog and firestarter, and the 2 were fooling around, opening some ports, closing others, instead of what i wanted them to do.
I then installed kmyfirewall, and my problems are gone ! ;) 
kmyfirewall is a bit tricky, since it's a direct front end to iptables (actually, it helps you creating a custom iptables script), and you won't be able to play with it as easy than with firestarter, but at least, it works great and without surprises !

---

### Post by ashokpappu on 2006-01-24
[QUOTE=skaboss]I had the same problem : couldn't access some sites (java.sun.com), couldn't listen to some shoutcast streams, had low ids on amule (although i opened the required ports), and so on...
I tried guarddog and firestarter, and the 2 were fooling around, opening some ports, closing others, instead of what i wanted them to do.
I then installed kmyfirewall, and my problems are gone ! ;) 
kmyfirewall is a bit tricky, since it's a direct front end to iptables (actually, it helps you creating a custom iptables script), and you won't be able to play with it as easy than with firestarter, but at least, it works great and without surprises ![/QUOTE]
if any one is using firestarter can they please post the log I will try to compare notes and see if Iam running into same issue

---

### Post by ashokpappu on 2006-01-24
[QUOTE=ashokpappu]Hello All,

I am having a issue with fire starter.  the minute I start firestarter I am unable to browse any of sun's website (like wwws.sun.com,java.sun.com...)  Every other website seems to be working.  Infact I can see that the sun website is being blocked by firestarter as I can see the the firestarter log.  Pretty much all the websites seem to work other than sun.   Any ideas on how to resolve this issue.[/QUOTE]


Can some one Please post the firestarter log so that I can see what is going on.
Thanks
Ashok Pappu

---

### Post by linuxfan on 2006-01-24
[QUOTE=mikkelwe]Open the firestarter window and click the events tab. Then visit the web page in firefox or whatever browser you use. Next look for the event that caused it to be blocked in the firestarter window. Now you should be able to right click the event an create an appropiate rule.[/QUOTE]

I realised that I didn't describe my scenario as soon as I posted my previous post. Wanted to post again but couldn't even go to the ubuntuforums (not sure if the site was down for maint?). 

Well, when I tried zdnet and cnet, there was absolutely no events logged into the "Events" tab of FS. The FS icon was still blue only ... means that there were  no blocked events.

Amazing things is that the sames sites are accessibile today and I hvn't done anything !!! God knows what the problem was !!! May be the network access to these sites including ubuntuforms site was probably having problems?

---

### Post by linuxfan on 2006-01-24
[QUOTE=ashokpappu]Can some one Please post the firestarter log so that I can see what is going on.
Thanks
Ashok Pappu[/QUOTE]

Does your ISP have a proxy? If yes, try adding proxy to your FireFox settings. When I was encountering a similar problem, my FS log did not log any blocked events so I can't post any.

---

### Post by ashokpappu on 2006-01-24
[QUOTE=mikkelwe]Open the firestarter window and click the events tab. Then visit the web page in firefox or whatever browser you use. Next look for the event that caused it to be blocked in the firestarter window. Now you should be able to right click the event an create an appropiate rule.[/QUOTE]


I did that but it was no help.  I also added java.sun.com to allow incoming and out going connections.  When I look at connections it seems that the ip 72.5.124.55 seems to be trying to make inbound tcp connections on port 37653 and that is not what is being liked by firestarter.  a who is command seems does confirm that the ip is sun
$ whois 72.5.124.55
Internap Network Services PNAP-09-2004 (NET-72-5-0-0-1)
                                  72.5.0.0 - 72.5.255.255
SUN MICROSYSTEMS INAP-SFO-SUN-4000 (NET-72-5-124-0-1)
                                  72.5.124.0 - 72.5.125.255

# ARIN WHOIS database, last updated 2006-01-24 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

Why on earth sun seems to be making inbound connections to my PC.  I dont think this is the regular TCP SYN/ACK thing because practically every other website seems to be working

Any Help will be appreciated

---

### Post by moopere on 2006-01-24
[QUOTE=ashokpappu]I did that but it was no help.  I also added java.sun.com to allow incoming and out going connections.  When I look at connections it seems that the ip 72.5.124.55 seems to be trying to make inbound tcp connections on port 37653 and that is not what is being liked by firestarter.  a who is command seems does confirm that the ip is sun
$ whois 72.5.124.55
Internap Network Services PNAP-09-2004 (NET-72-5-0-0-1)
                                  72.5.0.0 - 72.5.255.255
SUN MICROSYSTEMS INAP-SFO-SUN-4000 (NET-72-5-124-0-1)
                                  72.5.124.0 - 72.5.125.255

# ARIN WHOIS database, last updated 2006-01-24 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

Why on earth sun seems to be making inbound connections to my PC.  I dont think this is the regular TCP SYN/ACK thing because practically every other website seems to be working

Any Help will be appreciated[/QUOTE]

Hi Guys,

Saw this thread and thought I better reply to let you know that [www.sun.com](www.sun.com) and [www.java.com](www.java.com) seem to work fine from here - using breezy firestarter to NAT my network.

No weird stuff in events and no problems with the sites that I can see.  Are you sure you are not having some bizarro ISP related problem?

Cheers,
Craig

---

