---
title: "Linux and Exchange 2007"
date: 2009-08-11
forum: Desktop Environments
---

### Post by knight187 on 2009-08-11
I have been crawling through google for months trying to find a way to have my Linux (Ubuntu) PC connect to our company Microsoft SBS 2008 server running exchange 2007. Finally I have a working solution. I am using a program called DavMail ([http://davmail.sourceforge.net](http://davmail.sourceforge.net)). This little application is absolutely fantastic!!! I can run Thunderbird from my Ubuntu workstation with access to exchanges email, calendar, tasks and contacts.

DavMail uses Exchanges OWA to retrieve email, calendar, tasks and contacts. Its available Linux or Windows. The first time I set it up I installed it on my Ubuntu workstation. It worked well but was quite slow to retrieve information. If you don't have admin access to your windows server installing it locally would be your only option. I, on the other hand have admin access to our company SBS server so I installed the windows version on SBS and found the experience much more responsive, I guess the bottle neck is when DavMail accesses OWA.

Anyway I though I would document the steps I have takes to setup my workstation access to exchange 2007 because it was quite frustrating trying to find a solution that works as well as this.

Step 1. Install Thunderbird with the Lightning extensions.

Step 2. Download and install DavMail.

    Option 1) Install DavMail on your local PC, this option works but is not recommended because the speed is a bit slow. If you don't have admin access to your windows server and your windows sysadmin is a tool, then this is the only way I have found to access exchange reliably from Ubuntu. (there is an exchange 2007 add-on for evolution but I couldn't get it to work, just kept crashing and I'm not a huge fan of evolution).

    Option 2) Install DavMail on your Exchange Server, I found that this works a lot faster and if you have more then 1 workstation wanting to use DavMail then they can all connect to the one instance of DavMail running from your Windows server.

When DavMail is installed and run as an application the only thing you need to do is configure the URL for your exchange OWA, if your running it from your workstation the the URL would be something like [https://excahnge.server.local/owa](https://excahnge.server.local/owa). If your setup is like mine I used the URL of [https://localhost/owa](https://localhost/owa) because I am running DavMail from our Exchange server so other non windows users can access their exchange calendars, tasks, contacts, etc. We even have 2 guys running OSX and they can access their calendars etc. from their workstations. (I think exchange support for OSX will be built into the OS in the next major release).

After you have configured the URL the next thing to do is to configure the ports that each of the services will run from, I like to try and leave things as simple as possible so I left the defaults in place but after undergoing one of the many reboots our SBS Server needs DavMail refused to to start saying that port 1025 was in use by another process, so I had to change the port to 1125. I would recommend unticking any of the unwanted ports, for example I have no use for POP3 or IMAP as exchange supports these protocols by default and the end user experience is better using the exchange version of these protocols. If you don't have access to your exchange server to enable these protocols then your left to use the DavMail ports which work but are a bit slow if you have a lot of email. My exchange mailbox if over 2gig so sucking that down through OWA was painfully slow, however using the native exchange IMAP it was fine.

Step 3. Configure Thunderbird

Email.
I am using native exchange IMAP for my email in Thunderbird, there is no tricks to setting this up, its pretty standard, I am using ssl on port 993 so my email is sent encrypted over the company network (if the security is their you should use it).

In my config I am using IMAP for my email on my workstation and using the exchange (activesync) protocol to access my mailbox from my iPhone. The problem I was having was when I deleted an email from my workstation (IMAP) the email would still show as being in my inbox on my iPhone until I purged my email from Thunderbird. This is not a hard thing to do just right click on the folder you have deleted the email from and select compact. But really... Who is going to remember to do that every time they delete an email or leave there PC. So I went back and asked Google for a solution and sure enough Google has the answer...

In Thunderbird:
Edit -> Account Settings -> Server Settings -> "when i delete a message" Move it to the Trash folder.

Then:
Edit -> Preferences -> Advanced -> Config Editor -> mail.imap.expunge_after_delete = True

then when you delete an email from your inbox it will be moved to the Trash and deleted from the inbox. Perfect.

Note: I keep only emails that I am currently working on in my inbox so I never really have more then about 20 emails in my inbox at any one time, I think doing this make working with IMAP a little more friendly. If you have a few years backlog of email in your inbox your Thunderbird seems to run a bit slow (but I am using an old POS PC).


Calendar.
Ok this is where it get interesting, to add a calendar to Thunderbird is really easy just click Calendar from the file menu and select "New Calendar" then "On then Network" then CalDav and in the Location enter

"http://exchange.server.local:1080/users/user@example.com/calendar"

It took me a few days to figure out that who ever setup our exchange server setup my email address with a capital letter for my email address eg. [email]User@example.com[/email] instead of [email]user@example.com[/email]. The CalDav location string is case sensitive so be sure to type it all correctly or it won't work.

Now you should have Email, Calendar and Tasks working in Thunderbird. All that is left is contacts.


Contacts.
So far I can't get contact to display but I can search for them and the auto complete when typing email address in the to, cc, etc section works. To setup contacts in Thunderbird goto

Edit -> Preferences -> Composition -> Addressing -> Directory Server -> Edit Directories -> Add

Name: (I called mine exchange)
Hostname: excahnge.server.local
Base DN: ou=people
Port Number: 1389
Bind DN: domain\user

Then OK.

ALL DONE. you should now have a pretty nice user experience connecting to exchange 2007 from Linux.

---

### Post by Xirtambus on 2009-08-14
It WORKED!

I cannot tell you how long I struggled with evolution to try make that ******* evolution plugin work with MAPI over SSL. This works around it. Thank you. So much! Goodbye evolution!

If I could formally thank you for this post I would, but I can't find the button...

---

### Post by jctweb on 2009-08-17
> **knight187 said:**
> I have been crawling through google for months trying to find a way to have my Linux (Ubuntu) PC connect to our company Microsoft SBS 2008 server running exchange 2007.
Same here - can't find anything solid that actually works
> **knight187 said:**
> If you don't have admin access to your windows server installing it locally would be your only option. I, on the other hand have admin access to our company SBS server so I installed the windows version on SBS and found the experience much more responsive, I guess the bottle neck is when DavMail accesses OWA.
I, on the other hand, do not have admin access.

I will keep looking and see what I can find.  I think my problem is that I'm trying to access the exchange server through an exchange proxy (outlook anywhere) and it just doesn't want to play nice :(

---

### Post by knight187 on 2009-08-17
> **jctweb said:**
> Same here - can't find anything solid that actually works

I, on the other hand, do not have admin access.

I will keep looking and see what I can find.  I think my problem is that I'm trying to access the exchange server through an exchange proxy (outlook anywhere) and it just doesn't want to play nice :(

My Exchange skills are pretty poor, in fact almost non-existent but I will try and understand your problem and offer a solution.  From my understanding (and feel free to tell me I am wrong) is that Outlook Anyware uses RPC over HTTPS so port 443 should be open to your exchange server, if this is the case then you "should" be able to access OWA (Outlook Web Access) if your windows admins have set it up. I would have thought that if you install DavMail on your Linux desktop then you can configure Davmail to access [https://exchange.fqdn/owa](https://exchange.fqdn/owa). But I haven't tried to access OWA through an exchange proxy (I don't even know what an "exchange proxy" is)

Anyway if this is no help at all the DavMail author runs a mailing list and is pretty good at answering questions and is quite quick to respond.

Please let us know if you figure it out. Good Luck,
Cheers.

---

### Post by jctweb on 2009-08-17
I think I'll check out DavMail.

In case you're curious...

My company's exchange server is accessed via our LAN; you're supposed to be authenticated against Active Directory prior to accessing email..

On the other hand...there's a feature called "Outlook Anywhere" which allows us to access our exchange server from home - without using a VPN connection into the corporate network.

The way it works is through what's called an exchange proxy

PC -> exchange proxy (public) -> AD authentication -> exchange server

Interestingly enough, our OWA subdomain is also acting as the proxy.

My problem is that when I set up Evolution's Exchange MAPI connector (not related to this thread, per se) using the OWA address, it times out and doesn't quite work.  When I try to get to the pseudo-public IP and/or DNS name of the actual exchange server, it also times out.

In a nutshell, I'm willing to bet that I could access Exchange using my Ubuntu machine if I was hooked into the company network directly.  Since I'm not, I fear that I may be stuck using webmail (OWA) or a virtual machine w/Office 2k7 installed.

---

### Post by mr_raider on 2009-08-23
Anyone found a way to sync contacts? Not just lookup in the GAL.

---

### Post by Xirtambus on 2009-08-25
> **jctweb said:**
> Same here - can't find anything solid that actually works

I, on the other hand, do not have admin access.

I will keep looking and see what I can find.  I think my problem is that I'm trying to access the exchange server through an exchange proxy (outlook anywhere) and it just doesn't want to play nice :(

To clarify, I used the local install option and it worked. You don't need to make any changes to your company's box. :)

---

### Post by Amilo1718 on 2009-09-09
Thanks I will try the Thunderbird/DavMail instead of the non-working Evolution...

---

### Post by pcarneiro on 2009-09-10
Hello all!

I was thinking if anyone could help me understand some problems and how to solve it.
first off all, I started using Ubuntu a couple weeks ago. Used windows for more than 15 years! 
Just loving Linux.

The thing is, our company has a SMBS 2008, with OWA 2007. 
so, in ubuntu the email options would be Evolution or Thundirbird.
First tried Evolution, but I got some problems sending e-mail and it got bloqued frozen times. (used Evolution MAPI Exchange protocol)

Now I started trying thindirbir conected to OWA 2007 with DAVMAIL (great tool), but the thing is, some times it works, other times i get all kind of errors from davmail, ssl error, 404 error, etc. by no reason it works again, and after a couple minutes e stops working and i get the errors again. 

its not stable.

other thing I notice, many times davmail just loses al the setings, and i have to configure it all again: url, smtp, imap, etc.

any ideas?

i'am really stucked with this, and this is the last step for me to leave windows and go for linux.

Apreciate any help,

Best regards,
pcarneiro

---

### Post by !nkubus on 2009-10-16
Wow It worked.

You made my day, I was tired of the ugly webmail, and always found Evolution Clunky.


It would be awesome if ths would support ISA/RSA auth forms, This would allow me to take my emails everywhere, since outside of my work the webmail is protected with an RSA/ISA vpn form.

---

### Post by TimJ on 2009-11-08
I hope this isn't bumping an old thread but I've been using davmail and thunderbird happily under 9.04. I recently upgraded to 9.10 and the only problem is davmail now doesn't work as before. If I click on it nothing appears on the toolbar and in Thunderbird the gal lookup doesn't work but it's receiving and sending email. 

If start davmail in terminal I get the following: 

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at javax.swing.plaf.basic.BasicLookAndFeel.initialize(libgcj.so.10)
   at javax.swing.UIManager.setLookAndFeel(libgcj.so.10)
   at javax.swing.UIManager.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at davmail.ui.tray.SwtGatewayTray.init(SwtGatewayTray.java:172)
   at davmail.ui.tray.DavGatewayTray.init(DavGatewayTray.java:230)
   at davmail.DavGateway.main(DavGateway.java:65)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.10)
   at java.lang.Runtime.loadLibrary(libgcj.so.10)
   at java.lang.System.loadLibrary(libgcj.so.10)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...7 more

I'm not clueful enough in Linux to know quite what to do next, my best guess is I'm missing some dependencies (?) but I'm not sure which ones. Any help appreciated and apologies if I've missed a thread on this elsewhere, I looked but didn't find.

---

### Post by jctweb on 2009-11-10
Got it working with DavMail - thanks!

---

### Post by Dreamer Zero on 2009-11-12
Wow, this is an amazing program, i talked my boss into letting me install Ubuntu on my production machine, but because of Exchange 2007, i've had to run Vista in a virtual machine which is killing my machine more than Vista did, and i have been trying to find XP to setup in VM to replace it.

anyways, i had a overwhelming sense of joy when i saw my Exchange folders appear, then overwhelming sadness when i got a error that i fear is host side.

----------------------------------

Date:			Thu Nov 12 14:08:26 CST 2009 (1258056506097)
Thread:		ImapConnection-55905
Message #:	41
Level:		DEBUG
NDC:			
Category:	davmail
Message:		> 3 BAD unable to handle request: org.apache.commons.httpclient.HttpException
Location:	davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:91)
Thrown:
-----------------------------------


if anyone can help me out here, then i know i can get 4-5 more people in my office to join me in doing away with Windows altogether.

Thanks.

edit: looks like this error comes in at the same time:
------------------------------------

Date:			Thu Nov 12 14:08:26 CST 2009 (1258056506096)
Thread:		ImapConnection-55905
Message #:	40
Level:		ERROR
NDC:			
Category:	davmail
Message:		org.apache.commons.httpclient.HttpException
Location:	davmail.ui.tray.DavGatewayTray.displayMessage(DavGatewayTray.java:108)
Thrown:
org.apache.commons.httpclient.HttpException
	at davmail.http.DavGatewayHttpClientFacade.buildHttpException(DavGatewayHttpClientFacade.java:391)
	at davmail.http.DavGatewayHttpClientFacade.executeMethod(DavGatewayHttpClientFacade.java:324)
	at davmail.http.DavGatewayHttpClientFacade.executePropFindMethod(DavGatewayHttpClientFacade.java:287)
	at davmail.exchange.ExchangeSession.getFolder(ExchangeSession.java:1026)
	at davmail.imap.ImapConnection.run(ImapConnection.java:164)
---------------------------------------

---

### Post by bioteseo on 2009-12-02
If start davmail in terminal I get the following: 

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
......


try this ([http://ivkin.net/2009/11/using-thunderbird-to-access-exchange-mail-calendar-global-address-book/):](http://ivkin.net/2009/11/using-thunderbird-to-access-exchange-mail-calendar-global-address-book/):)
sudo update-alternatives --config java
you must chioce:
java-6-sun/jre/bin/java
I supposed you had installed it.

---

### Post by Brewfreak on 2009-12-03
Hello people, I have installed davmail and have been able to sync e-mails and calendar with exchange 2007 using Thunderbird but have been unable to get the LDAP functionality working.  I get the following message upon davmail startup "DavMail Gateway
Unable to bind to server socket for LDAP on port 389: port not allowed or in use by another process".
I have also tried with socket 636 with the same error message.  My IT department "insures" me that the socket is open and listening for any requests from users.
Does anyone have any ideas of what the problem might be?
Thank you for any help you can give!

Ubuntu 8.10
Kernel linux 2.6.27-15-generic
Gnome 2.24.1
CPU Mobile Intel Pentium4-M 2.00GHz

---

### Post by knight187 on 2009-12-03
> **Brewfreak said:**
> Hello people, I have installed davmail and have been able to sync e-mails and calendar with exchange 2007 using Thunderbird but have been unable to get the LDAP functionality working.  I get the following message upon davmail startup "DavMail Gateway
Unable to bind to server socket for LDAP on port 389: port not allowed or in use by another process".
I have also tried with socket 636 with the same error message.  My IT department "insures" me that the socket is open and listening for any requests from users.
Does anyone have any ideas of what the problem might be?
Thank you for any help you can give!

Ubuntu 8.10
Kernel linux 2.6.27-15-generic
Gnome 2.24.1
CPU Mobile Intel Pentium4-M 2.00GHz

Hay Mate, From within davmail use port 1389 instead of port 389 and then use port 1389 in thunderbird

---

### Post by Brewfreak on 2009-12-05
> **knight187 said:**
> Hay Mate, From within davmail use port 1389 instead of port 389 and then use port 1389 in thunderbird
Knight187, thanks for the guidance.  I will try it as soon as I get back to the office.  I'll let you know as soon as I have results.

---

### Post by subdee on 2009-12-09
I have to say a big THANK YOU for this. Now I am a happy Linux user at work (although still on a VM, since evil sysadmins like to keep a controlled Windows environment).

Thank you much! :D:D:D:cool:

---

### Post by Brewfreak on 2009-12-09
Hello Knight187:

Thank you again for the info.  I changed the port as instructed and now have DavMail reporting DavMail Gateway 3.6.0-833 listening on SMTP port 1025 CALDAV port 1080 LDAP port 1389.  So this means no more error message.  My only problem now is that Thunderbird can not find any contacts when I try to searh the addressbook.  Anything I am overlooking?

---

### Post by Brewfreak on 2009-12-09
Knight187:

Forget the last part of the previous post, LDAP is now working.  It appears that what was keeping me from the contacts data was the SSL.  As soon as I turned that off, everything began to flow.  Thank you for your help and to everyone else involved with DavMail.  Ahh... No more outlook nor windows at work.

---

### Post by phoenix49 on 2010-01-08
Thanks for solution! Works great! I set it up on one of internal servers, and its acting like proxy for us, Ubuntu users in company. :popcorn:

It works perfectly with Thunderbird, but I have problems with Evolution. Is someone succeeded to setup SMTP on Evo? Everything works besides SMTP, when I try to send message, it actually sends, but Evolution keeps it in outbox..:(

---

### Post by SmarterThanMyPhone on 2010-01-11
Does this solution support personal folders as well? Thats been my big hangup with Exchange 07 so far.

---

### Post by phoenix49 on 2010-01-11
Yes, folders are shown just as in web access view, i.e. personal folders are shown.

Regarding SMTP with evolution, i've managed to use direct exchange server for SMTP connections, and davmail for IMAP =)

---

### Post by jcampen on 2010-01-31
Seems quite a lot out there are finding it simple enough getting Thunderbird/Davmail to work, yet I've been at it for days now and still no luck. I've finally given up altogether with Evolution last week, as it seems from weeks of reading and trying, there just isn't a solution for it to work with Exchange Server mail. Yes I tried brutus and its web sites are down so to get additions such as Brutus Keyring is impossible. (its all a long story for another day)Evolution is now uninstalled and in the bin.

So now Im into the 5th day trying with Davmail and Thunderbird to get emails from my company mail exchange server.

I am sure Im going to have better luck with Thunderbird from what Ive read so far, but it still eludes me how to set it up with Devmail and the information Ive found so far is not very clear. I am sure I am just missing the most simplest step somewhere along the line.

Can someone please post a detailed instruction on how to configure both Thunderbird and Devmail to work together and also how to test if Davmails is working?

This is what I have so far. 
Thunderbird 2.0.0.23 with lightning and Devmail all installed and no issues there (Devmail working on Java 6)
Ubuntu 9.10

I can easily access my company emails via OWA with [https://*thecompanyname](https://*thecompanyname)*.com from my home internet, so no issue there. 
From the efforts of trying to get Evol to work where it came up with the error. "Evolution connector is not compatible with Exchange 5.5", I assume our company server is running an MS exchange server version 2003 or older.

_Setup of Davmail:_
OWA(Exchange)URL: [https://email](https://email).*thecompanyname*.com (is the "https://" required here or not?)
IMAP port:  1143
Local SMTP: 1025 
Caldav HTTP:1080
Loal LDAP:  1389

_Thuderbird Setup:_
Account Type: IMAP
Server Name: email.*thecompanyname*.com
User Name: email.*thecompanyname*.com\*loginname* (Have also tried using just the *loginname* on its own, but still no luck)
Use secure connection: None (I tried all of them. Assume None should work)
Port: 143

Outgoing SMTP:
Server: email.*thecompanyname*.com
User: *loginname*
Port: 25
Security: None

SMTP in Thunderbird seems to be partly working because I can sent out emails, although when it send and then tries to copy it to the sent folder it never succeeds. I have checked and the emails do go thorough and get received at the other end. I have this same result whether Davmail is running or not. So I am assuming because I cant receive emails and the sent mail doesn't copy to the sent folder, that TB isn't talking to Davmail or Davmails isn't configured correctly

_The Questions._
Is there anyway to check if Thunderbird is actually talking to Davmail? 

I ran Davmail from terminal as root, but cant see anywhere on there an indication if it is talking to ether the server or TB.

Is there anyway to check if Davmail is talking to the server?

Can anyone spot any error in my TB and DM configurations?
I have tried adding /exchange and /owa at the end of [https://email](https://email).*thecompanyname*.com but neither works so assume its not needed?

Do the port settings need to be same in DM as TH eg. TB 1143 DM 1143 or is the setting in TB at 143 correct?

When I checked on my Outlook in WindowsXP, the domain setting for Microsoft Exchange Server is different to the OWA server name. On Microsoft Exchange Server it is with the three initials of the company name eg. say our company name is "The Company Name" the server address is TCN-MAIL.*thecompanyname*.com

I assume this is for outgoing mails, but not sure really.

I appreciate any help from those who have managed to get it all working.
Thanks. jc

OS: Ubuntu 9.10 Karmic Koala
Installed on: Bootable USB Stick, 16Gb SanDisk U3 Cruzer Micro

---

### Post by Brewfreak on 2010-02-01
> **jcampen said:**
> Seems quite a lot out there are finding it simple enough getting Thunderbird/Davmail to work, yet I've been at it for days now and still no luck. I've finally given up altogether with Evolution last week, as it seems from weeks of reading and trying, there just isn't a solution for it to work with Exchange Server mail. Yes I tried brutus and its web sites are down so to get additions such as Brutus Keyring is impossible. (its all a long story for another day)Evolution is now uninstalled and in the bin.

So now Im into the 5th day trying with Davmail and Thunderbird to get emails from my company mail exchange server.

I am sure Im going to have better luck with Thunderbird from what Ive read so far, but it still eludes me how to set it up with Devmail and the information Ive found so far is not very clear. I am sure I am just missing the most simplest step somewhere along the line.

Can someone please post a detailed instruction on how to configure both Thunderbird and Devmail to work together and also how to test if Davmails is working?

This is what I have so far. 
Thunderbird 2.0.0.23 with lightning and Devmail all installed and no issues there (Devmail working on Java 6)
Ubuntu 9.10

I can easily access my company emails via OWA with [https://*thecompanyname](https://*thecompanyname)*.com from my home internet, so no issue there. 
From the efforts of trying to get Evol to work where it came up with the error. "Evolution connector is not compatible with Exchange 5.5", I assume our company server is running an MS exchange server version 2003 or older.

_Setup of Davmail:_
OWA(Exchange)URL: [https://email](https://email).*thecompanyname*.com (is the "https://" required here or not?)
IMAP port:  1143
Local SMTP: 1025 
Caldav HTTP:1080
Loal LDAP:  1389

_Thuderbird Setup:_
Account Type: IMAP
Server Name: email.*thecompanyname*.com
User Name: email.*thecompanyname*.com\*loginname* (Have also tried using just the *loginname* on its own, but still no luck)
Use secure connection: None (I tried all of them. Assume None should work)
Port: 143

Outgoing SMTP:
Server: email.*thecompanyname*.com
User: *loginname*
Port: 25
Security: None

SMTP in Thunderbird seems to be partly working because I can sent out emails, although when it send and then tries to copy it to the sent folder it never succeeds. I have checked and the emails do go thorough and get received at the other end. I have this same result whether Davmail is running or not. So I am assuming because I cant receive emails and the sent mail doesn't copy to the sent folder, that TB isn't talking to Davmail or Davmails isn't configured correctly

_The Questions._
Is there anyway to check if Thunderbird is actually talking to Davmail? 

I ran Davmail from terminal as root, but cant see anywhere on there an indication if it is talking to ether the server or TB.

Is there anyway to check if Davmail is talking to the server?

Can anyone spot any error in my TB and DM configurations?
I have tried adding /exchange and /owa at the end of [https://email](https://email).*thecompanyname*.com but neither works so assume its not needed?

Do the port settings need to be same in DM as TH eg. TB 1143 DM 1143 or is the setting in TB at 143 correct?

When I checked on my Outlook in WindowsXP, the domain setting for Microsoft Exchange Server is different to the OWA server name. On Microsoft Exchange Server it is with the three initials of the company name eg. say our company name is "The Company Name" the server address is TCN-MAIL.*thecompanyname*.com

I assume this is for outgoing mails, but not sure really.

I appreciate any help from those who have managed to get it all working.
Thanks. jc

OS: Ubuntu 9.10 Karmic Koala
Installed on: Bootable USB Stick, 16Gb SanDisk U3 Cruzer Micro

Jcampen:
On DavMail setup
"https://" is required just as you would use in your browser's address bar.
for the ports just leave the defaults.

For the TB setup
make sure the IMAP port is the same as DavMail
make sure the SMTP port is the same as DavMail

About TB talking to DavMail I supose your confirmation is when you get incoming and outgoing mail.

As for the server, you can pass your mouse over the davmail icon on the task bar after it is running to see the status of the ports.  It should say something like listening to IMAP port xxxx SMTP xxxx etc etc.

You can also right click the icon and select from the menu what you need.

"I have tried adding /exchange and /owa at the end of [https://email.thecompanyname.com](https://email.thecompanyname.com) but neither works so assume its not needed?"  You need to use the same address you use on the browser with the "/owa"
Start with these suggestions and let's see how it goes.  I am away from my office computer so this is all from memory but it should work.  Also re-check the previous posts on this subject since that's how I got mine working. Best of luck!

---

### Post by genfinch on 2010-03-10
I'm glad to find I'm not the only one who is having problems getting things to work. I recently switched back to thunderbird from evolution after my company installed new exchange2007. It was a hell of a search for appropriate software until I finally found davmail and was overjoyed to see my inbox fill up again! But unfortunately this remained all. I cannot access my calendar or contacts. The fact that I can't get at my contacts doesn't matter too much just at the moment because I also cannot send e-mails. 
I haven't found anybody in any forum who has the exact same problem, it either works all or nothing or there is one small specific problem. 
Jcampen is the closest anyone ever got to having the same issues as me, and he/she also has the exact same setup. I've tried Brewfreak's suggestion but it didn't make any difference. I've tried setting the ports with the extra 1 in DM but not TB, with the extra 1 in both, in neither, and in TB but not DM (the last out of pure desperation). I tried innumerable variations of the server name and OWA URL in all the different places it goes (http and https, entirely without either, with or without /owa, with or without mail. and even with /exchange... desperation, again).
SOMEBODY HELP ME PLEAAAAASEEEE! I'm fed up with the browser access, it keeps logging me out...
Jcampen: did you find a solution?

---

### Post by Riel on 2010-03-10
You need to set LOCALHOST:1143 etc, not email.companyname.com in your thunderbird settings!

Davmail is running on localhost. Or, like I do, I have davmail running on a server (sheevaplug) and my exchange is reachable trough that server:1143 etc.


I used to use davmail this way:

(correct settings in davmail.properties, enalbe some debugging if disabled)
$ screen
$ nohup ./davmail.sh davmail.properties &
CTRL ALT-D (close screen)

Then go to davmaildir

$tail -f nohup.out

you can se exacly what davmail is doing this way.



I will stick close to this topic, I think davmail is almost a perfect solution to a lot of exchangetroubles. And it worked for me every time. We will get you trough, IF the exchangeserver is supported.

---

### Post by jcampen on 2010-03-10
Thanks for your reply Riel. 
I have it all sorted and have Thunderbird working with Davmail and thanks also to the guy at Davmail.
Hear are the settings that have it working.

Setup of Davmail:
OWA(Exchange)URL: [https://email.thecompanyname.com/exchange/](https://email.thecompanyname.com/exchange/) (note that the URL must be appended with /exchange/ for Exchange server 2003 or older and with /owa/ for Exchange 2007)
IMAP port: 1143
Local SMTP: 1025
Caldav HTTP:1080
Loal LDAP: 1389

Thunderbird Setup:
Account Type: IMAP
Server Name: localhost ("localhost" is used if Davmail is running locally which in my case it is)
User Name: loginname (same as your mail login user name)
Use secure connection: None
Port: 1143 (note added the 1 in front to match the same in Davmail settings)

Outgoing SMTP:
Server: localhost ("localhost" is used if Davmail is running locally which in my case it is)
User: loginname (same as your mail login user name)
Port: 1025 (note added the 10 in front to match the same in Davmail settings)
Security: None

Hope this helps any others who had same trouble as me. Cheers

---

### Post by davoudi on 2010-03-10
How I could set localhost in davmail? The Thunderbird can not recognize and connect to localhost.

---

### Post by davoudi on 2010-03-10
I changed port number from 143 to 1143 and everything is fine now. Thanks.

---

### Post by pigmy31 on 2010-04-09
Hello all !

I'm trying to use DavMail (3.6.4-954) to share my calendar but it doesn't work after a lot of tries.

When I configure a new calendar, I fill the first window (calendar on network), the second (CalDAV and location [[http://localhost:1080/...]](http://localhost:1080/...])), the third (name of the calendar) and that's all. No more window where I should be prompted for a login and a password.

When I have a look to the console message, I can read : "Avertissement : Une erreur est survenue lors de la lecture de données de l'agenda : test. Cependant, l'erreur est certainement mineure ; le programme va donc essayer de poursuivre. Code d'erreur : DAV_NOT_DAV. Description : La ressource sur « [http://localhost:1080/users/firstname.name@company.com/calendar](http://localhost:1080/users/firstname.name@company.com/calendar) » n'est pas une collection DAV ou n'est pas disponible".

I'm using a dual-boot desktop (Windows XP/Ubuntu 9.10) and all thunderbird (3.0.4) directories are on the windows partition.

Anyone can help me ?

Thanks,
Michel

---

### Post by pigmy31 on 2010-04-17
Hi,

Somebody knows where I can find explanations for DavMail error message ?

Thks,
Michel

---

### Post by koushik.ms on 2010-06-02
Dear knight187,
Thanks a million for this wonderful post - this made my day and saved me lots of frustration. I was almost about to ditch my attempt with Thunderbird because my calendar wouldn't sync. Only thing suspicious was that the davmail logs indicating repeated redirects to owa and auth.dll pages (which kept happenning anyway all the time even when I didn't have a caldav calendar). You made it a point to mention the case-sensitivity of caldav url and that nailed it ! A quick test-msg to my gmail revealed the capital letters. There are not enough special characters on my keyboard to "encode" the rich expletives my mind can readily conjure for the IT "professional" of my company that chose to capitalize letters in my email address. I _knew_ since my childhood that email addresses were all lowercase!

Anyway, Thanks and may God bless you! :-).
Koushik

---

### Post by knight187 on 2010-06-02
> **koushik.ms said:**
> 
There are not enough special characters on my keyboard to "encode" the rich expletives my mind can readily conjure for the IT "professional" of my company that chose to capitalize letters in my email address.

Hahaha, This really made my day. Thanks Koushik

Cheers, Bruce

---

### Post by Ronlaen on 2010-11-05
Currently running a virtual machine for Windows XP to access my mail but would love to get it running locally in Thunderbird. Tried setting up with davmail and it seems to get to the point where it connects but it can't login and authenticate. Here is my setup:

DavMail - 3.8.5-1480-1
OWA Exchange URL: "https://companyname.com/Remote/"
Defaults

Thunderbird - 3.1.7
Server: localhost Port 1143
User: domain\username
Security: None
Authentication: None

When I try to connect I get an error "Login to the server localhost failed." and if I click on Enter New Password one thing does look odd is that the username is shown as "domain\username@localhost". Somehow localhost is added and I can't authenticate. Anyone have any ideas, any help would be appreciated.

---

### Post by wheelerj on 2011-03-24
> **knight187 said:**
> Hahaha, This really made my day. Thanks Koushik

Cheers, Bruce
That's always bugged the hell outta me... everyone knows that URL's and Emails addys are always lowercase...sheesh.

---

### Post by wheelerj on 2011-03-24
This worked perfectly using the client side installation. Configuration using Thunderbird 3.x, Lightening, Davmail - Got access to all exchange contacts (Including LDAP), email (I used IMAP anyway so this works) and Calendar. Over 2100 msgs in my inbox and IMAP zipped along (Disabled Davmail IMAP/POP) without a problem. I have an MSX 2007 server with WebDAV so I didn't test with the EWS Enabled. I also downloaded a copy of directory in addressbook and I see what you mean about contacts not showing up in the contacts list unless you search. I think this may be an issue with the Tbird 3.x config. I will check the config editor in the next couple of days and see if there is something masking that view... Other than that, this works perfect. Thanks.

---

### Post by gaston48 on 2011-07-28
Hello, 

first - thanks for the great work. I got it working for me. 

In case other have the same problem:

Under ubuntu 11.04 / unity: 

davMail didn't work, when I just started it with gnome-do or "davmail" in terminal. It said: ports are not allowed or in use. 
Everything works great starting it in terminal with "davmail -v" or "davmail -h"

---

### Post by mawe3661 on 2011-10-15
I am having trouble getting GAL to work. I did work earlier this year, but now I can only retrieve my private contacts which I have added manually at work. The directory search does not work. Still works on my android phone though, so I believe nothin has changed at the server side. 

Any ideas?

---

### Post by tonytodd on 2012-10-24
This worked for me... Only thing to remember is to make sure you add Davmail to startup applications, otherwise Thunderbird won't be able to access OWA mails when you start a new session. It took me ages to figure this out, but is simple as pie.

---

