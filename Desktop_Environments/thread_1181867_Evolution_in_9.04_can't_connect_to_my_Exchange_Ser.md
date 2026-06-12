---
title: "Evolution in 9.04 can't connect to my Exchange Server"
date: 2009-06-08
forum: Desktop Environments
---

### Post by texastwister on 2009-06-08
Since upgrading to Ubuntu 9.04 I’ve been unable to reconfigure Evolution for the same level of functionality I had working in 8.04.   I’m trying to get send/receive and address book functionality to an Exchange server (Exchange 2003, I believe).

In this release of Evolution there are two options for connecting to exchange – I have different problems in each:

·         Using Server Type “Microsoft Exchange” uses the older “connections” plug-in which utilizes the exchange OWA interface.  This is what I had working in 8.04.

o   Now, with a configuration apparently identical to that I had on 8.04, it appears unable to even reach the server (address above) even though I can connect to it with no problem in firefox.  I have accepted a certificate for the server in Firefox – I exported it from Firefox and imported it to Exchange to no effect.  So… bottom line: Using this option, I can’t do anything with my mail at all.

·         Using Server Type “Exchange MAPI” uses a newer MAPI plug-in.  This is brand new and likely still a bit buggy.

o   With it, I can read my mail.  But internet reports suggest this plug-in is unable to make use of the Global address book (even though it has config entries for it) and that has been my experience.  It attempts to connect, but does so as with no recognition of the domain, nor any way to provide the domain so far as I can see.

o   When I try to send mail to external recipients and use the full email address, it works.  But when I try to send internally, it strips the “@mycompany.com” from the address and the exchange server rejects the message.


I’m not particularly committed to either way of configuring it and would welcome any assistance anyone can provide.  


Thanks,

 

Scott Purcell

[email]Scott@texastwister.info[/email]

---

### Post by Freaky_Llama on 2009-06-09
I can confirm the same issues as the OP with Exchange 2003. In 8.10 Exchange via the OWA connector worked great. In 9.04, it gives a bad URL, username or password error. 

The MAPI connection doesn't work at all, with it completely crashing the configurator upon trying to authenticate.

---

### Post by shaneburton on 2009-07-12
Hi I am VERY VERY new to linux to so please bare with me.  I have install Mint 7 and ran sudo apt-get evolution.  When I try to configure it, I cannot connect to EITHER of my exchange servers.  Both are Exch07, but one is running owa.domain.com and the other is running webmail.domain.com/exchange.  When I try to connect to owa, I get the "unable to connect to server...check password...blah blah".  When I try to connect to the other it says that the server is Exch 5.5.  WTH?  

I have tried to install the newer bits 2.26.3 from the evolution site, but it keeps yelling at me about not having the evolution server components installed.  However if I run apt-get on those components, it says they are already installed and up to date. 

I have search hi and lo in the forums and it seems this is a continual issue.  Does ANYONE know how to work around this other than installing wine or crossover or virtualbox.  I would prefer to just run everything natively in linux otherwise I will just stick to Windoz.

Thanks.

---

### Post by analog_G on 2009-07-30
My network uses a proxy server:
I used evolution in 8.04 to connect to an Exchange server.  After switching to 9.04, I was always get errors scanning the Exchange folder.. blah blah and constant requests to enter my OWA password.  What finally worked for me was to go to Edit->Preferences->Network Preferences...
It was set to 'Use system defaults'.
I changed it to 'Manual Proxy Configuration' and entered my companies proxy server and port.  Now it works.  I've specified my Proxy settings in Gnome (System->Preferences->Network Proxy) and these settings work in apps like Firefox.  I wonder why Evolution needs explicit info?

---

