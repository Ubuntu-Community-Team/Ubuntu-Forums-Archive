---
title: "gtk-gnutella, no search results! Help"
date: 2009-03-23
forum: General Help
---

### Post by jitup on 2009-03-23
I have ubuntu 8.10 and the newest version of gtk-gnutella, it installed no problem, but when I search nothing appears, what is wrong? please help!
Thank you

---

### Post by mlebaron on 2009-08-09
I'm having the same problem.  GTK-Gnutella doesn't work anymore.   0/3 connections and never any search results.  Using Ubuntu 8.04 (hardy.  GTK-G version 0.96.4.

I have removed and re-installed GTK-G.

I even forwarded a port and then set GTK-G to listen on that port.

GTK-G says I'm firewalled.  What is going on?

---

### Post by ram4 on 2009-08-10
> **mlebaron said:**
> I'm having the same problem.  GTK-Gnutella doesn't work anymore.   0/3 connections and never any search results.  Using Ubuntu 8.04 (hardy.  GTK-G version 0.96.4.

I have removed and re-installed GTK-G.

I even forwarded a port and then set GTK-G to listen on that port.

GTK-G says I'm firewalled.  What is going on?

No wonder, you're using a totally outdated version,  incapable of joining today's Gnutella network.

You should grab the latest version (0.96.6) and that should be a little bit better...  If that does not work, come back here and we'll see what we can do to get you connected.

---

### Post by mlebaron on 2009-09-20
It had nothing to do with the version of Gnutella.  The problem was that I hadn't provided any "seed" server URLs.  Once I found a post that had a link to a list of "seed" servers, I put one of them in my GTK Gnutella options and it started working perfectly.

---

### Post by ram4 on 2009-09-22
> **mlebaron said:**
> It had nothing to do with the version of Gnutella.  The problem was that I hadn't provided any "seed" server URLs.  Once I found a post that had a link to a list of "seed" servers, I put one of them in my GTK Gnutella options and it started working perfectly.

That's nice to hear, but still you shouldn't use such an old version as 0.96.4.  Try upgrading to at least 0.96.6 to get the latest Gnutella features.

---

### Post by starscalling on 2009-09-29
for the record got tired of the no search results, looking for the damn kickstart file, etc. I have since installed the karmic versions of 5 packages which gives the latest of this package:

1. [http://packages.ubuntu.com/karmic/libgpg-error0](http://packages.ubuntu.com/karmic/libgpg-error0)
2. [http://packages.ubuntu.com/karmic/libgcrypt11](http://packages.ubuntu.com/karmic/libgcrypt11)
3. [http://packages.ubuntu.com/karmic/libtasn1-3](http://packages.ubuntu.com/karmic/libtasn1-3)
4. [http://packages.ubuntu.com/karmic/libgnutls26](http://packages.ubuntu.com/karmic/libgnutls26)
5. [http://packages.ubuntu.com/karmic/gtk-gnutella](http://packages.ubuntu.com/karmic/gtk-gnutella)

vua la - latest gtk-gnutella in jaunty - no ill effects seen; worksforme!

---

### Post by Smiley Coyote on 2009-10-24
> **starscalling said:**
> for the record got tired of the no search results, looking for the damn kickstart file, etc. I have since installed the karmic versions of 5 packages which gives the latest of this package:

1. [http://packages.ubuntu.com/karmic/libgpg-error0](http://packages.ubuntu.com/karmic/libgpg-error0)
2. [http://packages.ubuntu.com/karmic/libgcrypt11](http://packages.ubuntu.com/karmic/libgcrypt11)
3. [http://packages.ubuntu.com/karmic/libtasn1-3](http://packages.ubuntu.com/karmic/libtasn1-3)
4. [http://packages.ubuntu.com/karmic/libgnutls26](http://packages.ubuntu.com/karmic/libgnutls26)
5. [http://packages.ubuntu.com/karmic/gtk-gnutella](http://packages.ubuntu.com/karmic/gtk-gnutella)

vua la - latest gtk-gnutella in jaunty - no ill effects seen; worksforme!

Where does one insert these URLs?  I am having the same problem and would love to finally access the Gnutella network after a year with Intrepid Ibex.

---

### Post by Smiley Coyote on 2010-10-28
> **starscalling said:**
> for the record got tired of the no search results, looking for the damn kickstart file, etc. I have since installed the karmic versions of 5 packages which gives the latest of this package:

1. [http://packages.ubuntu.com/karmic/libgpg-error0](http://packages.ubuntu.com/karmic/libgpg-error0)
2. [http://packages.ubuntu.com/karmic/libgcrypt11](http://packages.ubuntu.com/karmic/libgcrypt11)
3. [http://packages.ubuntu.com/karmic/libtasn1-3](http://packages.ubuntu.com/karmic/libtasn1-3)
4. [http://packages.ubuntu.com/karmic/libgnutls26](http://packages.ubuntu.com/karmic/libgnutls26)
5. [http://packages.ubuntu.com/karmic/gtk-gnutella](http://packages.ubuntu.com/karmic/gtk-gnutella)

vua la - latest gtk-gnutella in jaunty - no ill effects seen; worksforme!

STILL unable to access Gnutella with gtk-gnutella.  I now have Lucid Lynx, have put in at least a dozen url's that purport to be nodes to connect to that will hook me up with the network and it does not happen.

Over and over I see claims that gtk-gnutella works great AND in nearly two years of searching online I find tons of requests from folks for help in this matter and a resounding lack of help in response.

Am I the only one that thinks that there is a huge demand for this information?  A little help can go a long way.  Imagine if this issue were solved and people could find the solution in a Google search.  Just imagine!

Now, with other Gnutella clients and with torrent clients, the data I request is port forwarded or at least, it comes through at high speeds anyway.  If my system handles, automatically, forwarding in relation to apps like Limewire, Frostwire, Deluge, Transmission, etc., does it not stand to reason that port forwarding is not the issue as to why gtk-gnutella still won't work?  If not, perhaps someone could direct me to an Ubuntu based port forwarding tutorial.

If it is all a matter of hosts, then how about a lit of URLs to add in my hosts that actually are active.

Doesn't SOMEONE have a clue regarding gtk-gnutella that does not require I am adept with command lines?  I will use the command lines given me if I get them.  Too often, though, the help comes in the form of some intermediate to expert jargon.

I JUST did an hour and a half browse through the internet and this topic is still dominated by tons of requests for help with little actual problem solving on this to be found.

HELP?

---

### Post by gandaran on 2010-10-28
> **Smiley Coyote said:**
> STILL unable to access Gnutella with gtk-gnutella.  I now have Lucid Lynx, have put in at least a dozen url's that purport to be nodes to connect to that will hook me up with the network and it does not happen.

Over and over I see claims that gtk-gnutella works great AND in nearly two years of searching online I find tons of requests from folks for help in this matter and a resounding lack of help in response.

Am I the only one that thinks that there is a huge demand for this information?  A little help can go a long way.  Imagine if this issue were solved and people could find the solution in a Google search.  Just imagine!

Now, with other Gnutella clients and with torrent clients, the data I request is port forwarded or at least, it comes through at high speeds anyway.  If my system handles, automatically, forwarding in relation to apps like Limewire, Frostwire, Deluge, Transmission, etc., does it not stand to reason that port forwarding is not the issue as to why gtk-gnutella still won't work?  If not, perhaps someone could direct me to an Ubuntu based port forwarding tutorial.

If it is all a matter of hosts, then how about a lit of URLs to add in my hosts that actually are active.

Doesn't SOMEONE have a clue regarding gtk-gnutella that does not require I am adept with command lines?  I will use the command lines given me if I get them.  Too often, though, the help comes in the form of some intermediate to expert jargon.

I JUST did an hour and a half browse through the internet and this topic is still dominated by tons of requests for help with little actual problem solving on this to be found.

HELP?
maybe you are using an old version of gtk-gnutella which no longer connects to the servers, go [here]("http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html") and download the news't .deb package (unstable) gtk-gnutella, don't worry about being the unstable version it works very well.

update
this version isn't connecting too, limewire was shutdown so maybe the whole gnutella server network no longer works.

---

### Post by Smiley Coyote on 2010-10-28
> **gandaran said:**
> maybe you are using an old version of gtk-gnutella which no longer connects to the servers, go [here]("http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html") and download the news't .deb package (unstable) gtk-gnutella, don't worry about being the unstable version it works very well.

update
this version isn't connecting too, limewire was shutdown so maybe the whole gnutella server network no longer works.

I am using a new version but gtk-gnutella has never connected for me while Gnutella IS still operating via other clients.  I will try the latest version which is not listed as stable.

---

### Post by Smiley Coyote on 2010-10-28
> **gandaran said:**
> maybe you are using an old version of gtk-gnutella which no longer connects to the servers, go [here]("http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html") and download the news't .deb package (unstable) gtk-gnutella, don't worry about being the unstable version it works very well.

update
this version isn't connecting too, limewire was shutdown so maybe the whole gnutella server network no longer works.

Also, this page says to chmod a+x (make executable) start up gtk-gnutella and then run it.  What does that mean?

---

### Post by gandaran on 2010-10-29
> **Smiley Coyote said:**
> Also, this page says to chmod a+x (make executable) start up gtk-gnutella and then run it.  What does that mean?
just select the 32-bits or 64-bits ubuntu [COLOR="DarkRed"].deb[/COLOR] package for download and double click to install, it will remove the old version and install, you don't have to do anything else if in fact it connects to the servers, if it doesn't then download the kickstart.sh to your home/user directory, right click the file, go to properties » permission tab and check-mark the box permit to execute file then start gtk-gnutella and open terminal and type the run command
```
./kickstart.sh
```
I tried it and in fact it did connect to the limewire server but I was unable to obtain any search results, I dont know if it was because of my low bandwidth or limewire is really down?
also it should have connected to 2 more servers which it didn't so theres some problem with the servers, watch that site for a kickstart script update.

---

### Post by ryor310575 on 2010-12-13
My installation works as [follow]("http://ryorown.blogspot.com/2010/12/gnutella.html"):

Instal the unstable version 0.96.9u from [here]("http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html")
Scan the ports usin this [page]("http://www.whatsmyip.org/ports/p2p/").

Laptop Dell Inspiron 15
Description:    Ubuntu 10.04 LTS
Linux User 518016

---

