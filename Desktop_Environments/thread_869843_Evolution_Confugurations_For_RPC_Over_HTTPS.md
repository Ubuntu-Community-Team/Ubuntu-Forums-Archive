---
title: "Evolution Confugurations For RPC Over HTTPS"
date: 2008-07-25
forum: Desktop Environments
---

### Post by eltech on 2008-07-25
Does anyone have the absolute configurations?

I have tried it all and cannot get it to work at all.

Thanks in advance

---

### Post by eltech on 2008-07-25
Basically having the same issues as this poster

[http://ubuntuforums.org/showthread.php?t=549648](http://ubuntuforums.org/showthread.php?t=549648)

---

### Post by eltech on 2008-12-11
Almost 6 months later - is there any email client that will support rpc over https connections? AKA corporate email? The same way outlook does.

---

### Post by draconastar on 2009-02-02
I'll post here as well.  I'm wondering if Evolution can work with RPC over HTTPS, because at the moment I can't get it to work.  I read something about Evolution simulating it using OWA, but even then it has weird authentication issues, when I can use the same information to use the ACTUAL OWA through a browser.  

Anyone know anything about this?

---

### Post by njsanders1 on 2009-02-25
_**[color=red][size=7]bump!!![/size][/color]**_

---

### Post by codeseer on 2009-03-02
I am seeking the same ability. :(

---

### Post by eltech on 2009-05-08
It does work, you have to mess with the settings a bit, but it's possible. I've gotten it to work in my environment.

---

### Post by codeseer on 2009-05-08
> **eltech said:**
> It does work, you have to mess with the settings a bit, but it's possible. I've gotten it to work in my environment.

I've tried everything imaginable. It just doesn't work for my college's email. I thought, maybe if I got the certificates and installed them; but they're all incompatible formats designed for browsers and Mac.

---

### Post by elfede521 on 2009-06-30
eltech, can you post the configuration for evolution-mapi to conect with rpc/https?

---

### Post by codeseer on 2009-06-30
> **elfede521 said:**
> eltech, can you post the configuration for evolution-mapi to conect with rpc/https?

[http://www.ecu.edu/cs-itcs/email/upload/Config-Outlook2007-Home.pdf](http://www.ecu.edu/cs-itcs/email/upload/Config-Outlook2007-Home.pdf)

---

### Post by Chambers on 2009-07-08
So is the consensus that it's still not usable?  Do we need to wait for wine to fully support Outlook 2007??  Man, all the hype about this mapi connector and it seems like there's way too many problems with it still, should never have been announced as usable

---

### Post by spegru on 2010-01-24
I'm also interested in RPC over HTTPS
Has anyone got any info?
That weblink doesnt work.....

---

### Post by DiscGo on 2010-05-05
I also am desperate for RPC over HTTP (with an Exchange 2007 server)

---

### Post by Rebootkid on 2010-08-10
I'm in the same boat.

I'd settle for any native Linux client that can connect to Exchange 2007 using RPC over HTTPS. (Exchange Proxy)

Right now I'm connecting by running Outlook under Wine(Crossover Office) and using that, but it is a resource hog.

---

### Post by Rebootkid on 2010-08-10
So, I've got a bit of a hack solution to this.

I found a tool called "Davmail"

It's basically a wrapper tool. It takes standard protocols, and wraps them in the RPC/SSL stream.

You set it up, point it at your exchange server, and it will define local ports for the proper services.

Then you point Evolution at the local ports (e.g. IMAP, or LDAP)
[http://davmail.sourceforge.net/](http://davmail.sourceforge.net/)

It runs as a local tool with the same permissions as the logged on user, so keep that in mind. I haven't done a source code review, so keep the security of that in mind.

So far I've got email and calendar working. I do not have LDAP working for contact or GAL stuff. I'll continue to tinker with that. Here are the settings I used:

[Davmail Client]
(Main tab)
OWA (Exchange) URL: [https://owa.mydomain.com/exchange](https://owa.mydomain.com/exchange)
Local POP: 1110
Local IMAP: 1143
Local SMTP: 1025
Caldav HTTP: 1080
Local LDAP: 1389

Trash keep delay: 30
Sent keep delay: 90
Cal past events: 90
Idle folder monitor is blank.

(Proxy tab)
Use system proxy settings is checked. Modify if you need a proxy to get to the Internet / OWA URL

I left the other tabs at the install default.

[Evolution Settings]
You need to fill out a name for the account, I chose work. You also need to give it your name and email address.

Receiving type is IMAP
Server is localhost:1143
username: domain\username
No security/encryption
I chose "remember password" but you can do as you like

Sending type is SMTP
server is localhost:1025
Server requires authentication
no encryption
username: domain\username

The rest of the stuff is like where you want things delivered, sent items stored, etc. Choose where you'd like, or they default to local folders.

[Calendars]
Go to the calendar button, in the left hand nav pane, right click a blank area and choose "New Calendar"
The calendar type is "CalDav"
Choose a color you like
I checked "copy offline" and "Default" because I primarily use this system for work
The URL is:
caldav://localhost:1080/users/user@domain.com/calendar  (note the [email]user@domain.com[/email] is  your full email address, not your user name)
leave "SSL" unchecked
username is domain\username
refresh of 30 min seems to work just fine.


I still do not have LDAP working for access to the GAL, my contacts, or anything like that. I'll update this thread if/when I figure it out.

---

### Post by Rebootkid on 2010-08-10
Nevermind.. fat fingered this post.
Still working on the LDAP stuff

---

### Post by brokenromeo on 2010-08-10
I gave up 6 months ago trying to use Evolution with Exchange 2007 and just use owa webmail...you would have thought someone would have written an active sync mail client for exchange by now...

---

### Post by erikkll on 2010-10-01
This is THE feature i still need in ubuntu. I find it strange that so many companies (htc, google, nokia, etc) have been able to write a working rpc over https ('activesync') implementation and yet there seems to be no working solution for linux.

---

### Post by magowiz on 2011-04-29
Identical problem, same considerations: isn't this a major issue? I guess a hundred huge companies throughout the world have thousands of people accessing exchange via http like I and others do.

---

