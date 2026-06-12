---
title: "Evolution Exchange connector Issue with outside hosted exchange."
date: 2005-02-22
forum: Desktop Environments
---

### Post by djester on 2005-02-22
So after a long search, I have finally found the perfect distro for me.  I just have one seemingly little task and that is to connect my evolution client to my works exchange server.  Unfortunatly. we host our exchange with intermedia.net and when I asked them about using evolution they clammed up.  They use a nifty little downloaded app to configure the outlook 2002 and 2003 clients.

So I need some help to even know if this is possible.  From what I've read in the forums and novell.com and google.com in general it seems possible.

Here's the info that I have.  
Server Name is EHOST011-6 which is supposed to go to a specific IP address. Which their config app, puts in a hosts file.  
I know the fqdn: EHOST011-6.exch011.intermedia.net
My username and password of course.
the Domain is EXCH011
RPC over HTTP Settings:
Proxy Server URL owa11.intermedia.net
Use Basic Authentication

I've also found a lot of info for using Entourage X and 2004 for mac.  

My basic problem is that I have a lot of information and I don't know where it goes.  
In Evolution I selected Microsoft Exchange, but then what?
For the Exchange Server do I put the ip address? 

For the Windows Username I can think to put [email]username@email.com[/email] or Domain/username or just the username. (but I'm pretty sure that won't work)

Do I use SSL?
Then on the recieving options.... Is the GAL the LDAP server? and if so do I use the full URL. (i.e. LDAP://LDAP.Domain.com:389 ou= etc...)

Mailbox name I'm assuming is my email.
OWA path default seems to work.  Even though intermedia also has a dedicated host for that. owa11.intermedia.net

And I have no idea what the public folder server should be.  

I don't know if there is anyone out there who can help me with this problem or not, but I thought I would try.  If anyone has any suggestions let me know.

Thanks

---

### Post by WirelessMike on 2005-03-05
At least you seem to have a version of Evolution with Exchange that will allow you to enter all the necessary information.  You must be on Warty.

Hoary's version, Evolution 2.1x, is worthless.  There isn't enough config in the settings to actually connect with an Exchange server.  This has got to be a first for me.  A Linux app that actually degraded in development.

Anyways--  I hope you can figure out where to plug in your info.  Don't upgrade!

---

### Post by dolson on 2005-03-05
I have a problem with Evolution too. I tried a bunch of values, but I always get "The accout for dolson is not on this server" even though I can log in via the webmail page and in the status bar it shows my account as dolson... I don't get it.

---

### Post by justBE on 2005-03-11
djester,

I am not an intermedia.net user, but I had a closer look at them a couple times, and maybe these two pages contain all the necessary information and hosts for you:

[https://exchange.intermedia.net/asp/Common/HowToConnect.asp?clientName=MSEntourage2004](https://exchange.intermedia.net/asp/Common/HowToConnect.asp?clientName=MSEntourage2004)

[https://exchange.intermedia.net/asp/Common/HowToConnect.asp?clientName=MSEntourageX](https://exchange.intermedia.net/asp/Common/HowToConnect.asp?clientName=MSEntourageX)


[QUOTE=djester]So after a long search, I have finally found the perfect distro for me. I just have one seemingly little task and that is to connect my evolution client to my works exchange server. Unfortunatly. we host our exchange with intermedia.net and when I asked them about using evolution they clammed up. They use a nifty little downloaded app to configure the outlook 2002 and 2003 clients.

So I need some help to even know if this is possible. From what I've read in the forums and novell.com and google.com in general it seems possible.

Here's the info that I have.  
Server Name is EHOST011-6 which is supposed to go to a specific IP address. Which their config app, puts in a hosts file.  
I know the fqdn: EHOST011-6.exch011.intermedia.net
My username and password of course.
the Domain is EXCH011
RPC over HTTP Settings:
Proxy Server URL owa11.intermedia.net
Use Basic Authentication

I've also found a lot of info for using Entourage X and 2004 for mac.  

My basic problem is that I have a lot of information and I don't know where it goes.  
In Evolution I selected Microsoft Exchange, but then what?
For the Exchange Server do I put the ip address? 

For the Windows Username I can think to put [email="username@email.com"]username@email.com[/email] or Domain/username or just the username. (but I'm pretty sure that won't work)

Do I use SSL?
Then on the recieving options.... Is the GAL the LDAP server? and if so do I use the full URL. (i.e. LDAP://LDAP.Domain.com:389 ou= etc...)

Mailbox name I'm assuming is my email.
OWA path default seems to work.  Even though intermedia also has a dedicated host for that. owa11.intermedia.net

And I have no idea what the public folder server should be.  

I don't know if there is anyone out there who can help me with this problem or not, but I thought I would try. If anyone has any suggestions let me know.

Thanks[/QUOTE]

---

### Post by dolson on 2005-03-12
Weird.... I upgraded to Hoary and I set up my Exchange account, and it worked!

Here's to progress!

---

### Post by justBE on 2005-03-13
does anyone of you use any hosted exchange provider that does working with evolution? none of the bigger ones officially support it or mention it in their faqs/documentation, but I'd be interested in mail providers that do work with evolution...

---

### Post by mmHg on 2005-03-18
I too have found that Evolution 2.2.x is horrible at connecting to exchange.  It doesn't even ask for an exchange server!  Instead it asks for the OWA server?!  My account login credentials differ from my mailbox name and this version of Evolution does not even give me the option to set this manually!  This is the first, and hopefully the last time I have to witness a linux app downgrading itself.  Do not upgrade - you have been warned!

---

### Post by elasticwings on 2005-04-20
Does anybody know where I can find a package for the old version of evolution?  I am in the same situation where my account name and mailbox name differs on the exchange server.

---

### Post by elasticwings on 2005-04-20
Nevermind, I found them at packages.ubuntu.com

It took me a little, but I finally got it downgraded to the older version and it works with exchange again.

---

