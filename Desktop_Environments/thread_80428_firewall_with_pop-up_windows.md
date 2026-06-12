---
title: "firewall with pop-up windows?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by mulperi on 2005-10-22
I have been searching a long time for a firewall to Ubuntu that would feature a pop-up window each time a new application tries to call out. 

Is there anything like this available?

-=( Mulperi )=-

---

### Post by jamesford on 2005-10-22
ive been looking for this too ever since i started using linux (i used outpost in windows) there is nothing like that for linux unfortunately that ive been able to find :/ i miss it

---

### Post by rjwood on 2005-10-22
[quote=mulperi]I have been searching a long time for a firewall to Ubuntu that would feature a pop-up window each time a new application tries to call out. 

Is there anything like this available?

-=( Mulperi )=-[/quote] Why? Anything that goes on in ubuntu basically requires your permission anyway.
Using linux , or not using I.E. already secures your system way beyond any window's firewall would possibly want to.

Firestarter is plenty capable enough it seems. Or if your behind a router you have good protection as well

---

### Post by pmj on 2005-10-22
[QUOTE=rjwood]Why? Anything that goes on in ubuntu basically requires your permission anyway.
Using linux , or not using I.E. already secures your system way beyond any window's firewall would possibly want to.

Firestarter is plenty capable enough it seems. Or if your behind a router you have good protection as well[/QUOTE]
It seems you just have no idea how many Windows applications there are that phone home. It's a lot, I'll tell you. And I bet there are a whole bunch of Linux apps that do the same. To get info about new updates and such if nothing else. It makes sense to be able to stop this, especially when dealing with programs you don't fully trust, or just plain think shouldn't access the internet, because it has absolutely no valid reason to.

---

### Post by rjwood on 2005-10-22
[quote=pmj]It seems you just have no idea how many Windows applications there are that phone home. It's a lot, I'll tell you. And I bet there are a whole bunch of Linux apps that do the same. To get info about new updates and such if nothing else. It makes sense to be able to stop this, especially when dealing with programs you don't fully trust, or just plain think shouldn't access the internet, because it has absolutely no valid reason to.[/quote]

Relax, there are alot of things I don't know, especially about computing.

Isn't that why you have sources list??

I just haven't had the problems with ubuntu that I had with windows. I constantly had firewall permissions pop-up when I had xp. But that is the design of propritary sofware isn't it?

If I am incorrect then educate me. I don't have a problem with that at all.;)

---

### Post by pmj on 2005-10-22
Sorry, I meant no offense.

When I first installed a firewall on Windows a couple of years ago I was shocked to discover that I was using lots of programs that connected to the internet without notifying me and for no apparent reason, and up until then I had no idea about it. And of course I will never know what kind of info was sent.

Does some Linux software phone home? I really don't have a clue. But I'd like to find out.

---

### Post by bryan986 on 2005-10-22
Just look at the package popularity-contest for example...

---

### Post by rjwood on 2005-10-22
[quote=pmj]Sorry, I meant no offense.

When I first installed a firewall on Windows a couple of years ago I was shocked to discover that I was using lots of programs that connected to the internet without notifying me and for no apparent reason, and up until then I had no idea about it. And of course I will never know what kind of info was sent.

Does some Linux software phone home? I really don't have a clue. But I'd like to find out.[/quote]
I am sure they can if they are designed to, but I think if a source is trusted then your trusting them not be malicious.  Again , if you are behind a router you can configure it  to  prevent outgoing packets or at least restrict them. I think the fact that you have to use sudo to get updates and then can review what is updateing gives you alot more power over your system. Proprietery software is allow to take control of parts of your system thru IE and of course that's just a wink and a nod between them and good old microshaft.
I did some reading about this in my Linux-Bible. You can probable find that info from the authors if you google it. There is also alot of info on these forums if you search "firestarter" or "firewalls". Good luck;)

I hope this helps!!!!:smile:
btw no offense taken..

---

### Post by mulperi on 2005-10-22
[QUOTE=rjwood]
I did some reading about this in my Linux-Bible. You can probable find that info from the authors if you google it. There is also alot of info on these forums if you search "firestarter" or "firewalls". [/QUOTE]

Thank you for the suggestion, unfortunately I don't have that book... yet  :-({|=

Firestarter is not the answer, because it is just a GUI for iptables. That said, firestarter is an excellent program - it just does not offer the functionality I would like to have.

I remember reading somewhere on the net that you need to modify the kernel to support this kind of feature. Someone had made beta scripts but I would prefer a firestarter -kind of mature application.

Speaking of the threat I can live without this feature, but anyway it would be nice to be able to halt suspicious outbound network connections until getting a sniffer up and running. Back in the windows days I was able to find a new trojan that my antivirus did not catch that way.

-=( Mulperi )=-

---

### Post by Abandon on 2005-10-22
It's there allright, but not within Ubuntu. The latest release of Mandriva (2006) is using it. Its using Shorewall as Firewall but I' m not sure the extra's are made by Mandriva or if they are standard Shorewall features.

[http://qa.mandriva.com/twiki/bin/view/Main/InteractiveFirewall]("http://qa.mandriva.com/twiki/bin/view/Main/InteractiveFirewall")

---

### Post by mulperi on 2005-10-23
Thanks Abandon! Mandriva interactive firewall looks promising, however I understand that it does not feature any protection against proprietary programs that "call home", i.e. I want to make sure my ATI display drivers and Acrobat reader are not communicating out without my knowledge.

Actually we could forget about the pop-up first... is it possible to define which programs are allowed to make outbound connections and get a log-file on any other attempts? If this would be possible, a pop-up would not be too difficult I guess.

-=( Mulperi )=-

---

### Post by Bitmastro on 2005-10-23
maybe lsof -i is what you are looking for... try it in a command line.
i also googled this for an introduction for lsof
[http://www.akadia.com/services/lsof_intro.html](http://www.akadia.com/services/lsof_intro.html)

bye

---

### Post by mulperi on 2006-02-10
Is there a port to Ubuntu for Mandriva Interactive firewall? I think it could do the job just fine...  The point is not to create iptables rules interactively but to get pop-ups on applications trying to make egress network connections.

Could anyone estimate how hard it is to port that application to Ubuntu?

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=mulperi]I have been searching a long time for a firewall to Ubuntu that would feature a pop-up window each time a new application tries to call out. 

Is there anything like this available?

-=( Mulperi )=-[/QUOTE]
Couldn't you just use firestarter and switch the Outbound Traffic Policy to "Restrictive By Default"?  The tray icon turns red with a lightning bolt through it when the firewall blocks/drops a connection.  I think that is a little less obtrusive than a pop-up.

---

### Post by mcduck on 2006-02-11
[QUOTE=mulperi]
Actually we could forget about the pop-up first... is it possible to define which programs are allowed to make outbound connections and get a log-file on any other attempts? If this would be possible, a pop-up would not be too difficult I guess.
[/QUOTE]As cwaldbieser already mentioned, Firestarter allows you block all outbound connections by default and only allow those that you set yourself. OPen firestarter, go to Policy tab and Outbound Traffic Policy, and set it to 'Restrictive by default, whitelist traffic'.

You'll then see all blocked connections in firestarter's Events-tab, ans well as in some log files like /var/log/messages. Running firestarter all the time is IMHO a bad idea. I don't like to have any extra apps running with root privileges.. But you could find some thread about transparent terminals on desktop, and set one to run 'tail -f /var/log/messages' for example ;)

---

### Post by mulperi on 2006-02-14
While I want /usr/bin/firefox to be able to make outgoing connections to port 80 I don't want /usr/bin/acroread to make any connections on any port. Guess iptables just cannot provide that functionality... but I might be wrong :D 

Thanks for suggestions anyway

---

### Post by cwaldbieser on 2006-02-14
[QUOTE=mulperi]While I want /usr/bin/firefox to be able to make outgoing connections to port 80 I don't want /usr/bin/acroread to make any connections on any port. Guess iptables just cannot provide that functionality... but I might be wrong :D 

Thanks for suggestions anyway[/QUOTE]
That is true-- iptables cannot control things at the process table level.  You might want to consult the Linux Advanced Routing HowTo:
[http://lartc.org/howto/]("http://lartc.org/howto/")
It is not really an application, but it does explain how to use existing tools to achieve some rather specialized firewall results.

Edit:
I may have spoken too quickly--  iptables has an "owner" match that is effective in the OUTPUT chain (but not for ICMP requests-- e.g. ping).  It can be used to filter on user ID, group ID, process ID, and the command used to create the process.

You might be able to use this match to do what you want.  For example, if you matched the acroread command, you could effectively block that program from initiaing any outbound traffic (except ICMP traffic).

Here is a simple example that blocks the ftp command line client:
```

$ sudo iptables -A OUTPUT -m owner --cmd-owner ftp -j DROP

```

---

### Post by yota on 2006-02-17
Hi guys,

I totally agree with mulperi, firewalling in linux has an enterprise server philosophy, with plenty of strong solutions, but lacks on the field of personal/application firewall.
If it was all free software I could trust applications by (eventually) looking at source code, but since I run prorpietary software too (crappy-ati-drivers(tm), acrobat reader and nero, for instance) and I don't trust it, I would like to have control on what applications are trying to do with network.

Tuxguardian:

[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

AFAIK is the only solution available (other than handmade iptables rules), and it is beeing packaged on debian ([http://www.debian.org/devel/wnpp/being_packaged)](http://www.debian.org/devel/wnpp/being_packaged)), although it seems that it's taking forever...

If you find other info please post them here!

---

### Post by mulperi on 2006-04-23
I noticed tuxguardian 0.5 was released on 8th of April 2006. I am sure some of you guys have tried to compile it for Ubuntu 5.10. Any luck?

---

### Post by mulperi on 2006-06-19
I succeeded in compiling and installing tuxguardian 0.5 with the new Dapper. Was very easy actually. 

It seems to do what I'm looking for but is still too much "beta" to keep on running. By beta I mean, it does not startup automatically but needs manual tweaking.

I sincerely hope tuxguardian will be further developed.

---

### Post by komputes on 2007-10-12
I completely agree with mulperi. I'm thinking that a program like this is needed to be a "safe" user. Linux lovers have a lot of faith in their systems because only programs from the main repositories are used. Although this may be safer, there are still programs that may come with bugs or security holes that allow the flow of internet traffic. Not to mention the possibility that WINE users bring.  

So I am also looking for a "pop-up bubble" taskbar utility that keeps a table of the applications that try to call out. It would also be useful to warn of any incoming or outgoing attempts (should it be TCP, UDP, ICMP, some other P). 

Question: What would it take to recommend a project to perfect tuxguardian by adding a better GUI, custom levels of protection (presets) and more options to stop incoming and outgoing packets from flowing unnoticed.

This is not something you would want to install on a server, ever....e v e r.



Yes, I want to be prompted every time I try to call out or someone tries to connect to me. :popcorn:

---

