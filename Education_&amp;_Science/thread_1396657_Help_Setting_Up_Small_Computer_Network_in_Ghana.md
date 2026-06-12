---
title: "Help Setting Up Small Computer Network in Ghana"
date: 2010-02-02
forum: Education &amp; Science
---

### Post by J Lugo on 2010-02-02
Hi everyone,

I'm working with an Engineers Without Borders group implementing a library/school in Ghana. We plan on acquiring about 30-45 netbooks (we have about 8 OLPC XO-1s donated so far, the rest will likely run Ubuntu Netbook Remix dependent on what is donated / what we purchase) to give the children some computer proficiency and access to the Internet. However, we have no experience with this area.

Additionally, we want the netbooks to be able to access one [eGranary Digital Library]("http://www.widernet.org/digitallibrary/") that we already have. Because of Ghana's very limited bandwidth (the computers would all likely share a 1-4 Mbps connection), we would like to have computers that try to access a website to first be routed to the eGranary. If the files exist there, they would just be given those. If not, they would proceed to be connected to the website online.

Could anyone give me a rough idea of what hardware and software is needed to implement this? We have limited funds so I am worried about purchasing something that will end up insufficient for our purposes.

In summary:

[LIST]
[*]30-45 netbooks in Ghana sharing a 1-4 Mbps connection.
[*]Able to search eGranary database for information before connecting to Internet.
[*]Servers? Routers? Software? A little confused!
[/LIST]
  Absolutely any starting information would be greatly appreciated!

Thanks for your time,
J Lugo

---

### Post by oldsam on 2010-02-02
As far as I understood, you do not use the netbooks as Thin Clients, but as standalone computers.
So you need the server just for caching websites?
If this is so, you don't need big hardware for the server. For example an Intel Atom processor would be far enough for that.
You could set up an Ubuntu Server and install Squid. Squid caches all content loaded from the web and stores it on the server (see Wikipedia for more information).
For that it is important to have enough RAM and a fast hard disk.
But here the requirements are also relatively low, for every GB of disk space you need 32MB RAM. You see, you could also use an old computer for your needs, if you need the server only for caching.

If you have any more questions, feel free to ask. I've gathered some experience last year as I had to set up 10 Thin Clients and the corresponding Server for a school in Uganda.

greetings,
oldsam

---

### Post by oldsam on 2010-04-24
> Hi oldsam,

Thank you so much for your help regarding the computer network in Ghana  (and sorry for taking so long to reply!). 

Thankfully, we have about 12 netbooks and 1 desktop computer to act as  the server. For using the computer to cache local sites and allowing the  computers to access them, would we just use a typical wireless router?  How would that connect to the computer to ensure websites always go  through there? We are a little unsure of what we need to purchase in  that regard.

Thanks again,
AndanteHi Andante!

You need to connect your Desktop computer (Server) to the internet (over a wireless router may be ok) and then connect all your Netbooks with the Server.
After you have installed and configured Squid (the cache proxy) on the server, you have to setup your clients to use the proxy on the server. 
Then you have to enter the Server address as Proxy in your Browser or other programs you want to use the proxy.

We have also connected the Server via Wireless to the Internet and the Thin Clients were connected to the Server (where also Squid was running) over Ethernet. We used a tool called Wicd to set up both Network cards, but if you are using a newer Ubuntu version the network manager from Ubuntu may do it also (We were using hardy).


oldsam

---

### Post by Andante on 2010-04-24
That sounds pretty straightforward. I'll update this thread when I get the chance to test it out in the coming week.

Thanks!

---

### Post by Andante on 2010-04-26
Regarding the wireless network, it's a bit unclear to me what type of router could share 12 connections at once. Since the actual DSL connection is low (I think 512kbps), would a standard wireless router suffice? Or would we need a more industrial strength one? I'm seeing some wireless routers that claim to support hundreds of connections, but also cautions that you shouldn't split it up between more than a few on one wireless router.

Thanks again!

---

