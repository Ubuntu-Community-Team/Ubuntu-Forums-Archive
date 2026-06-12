---
title: "Ubuntu 8.1 and 9.04 crippled on two laptops - please help!"
date: 2009-05-10
forum: General Help
---

### Post by DJB1609 on 2009-05-10
Hi,

Please, please help as I really want to use Linux/Ubuntu and have been close to wiping XP on my netbook. It is my wife's preferred OS on her Toshiba laptop. I can't because of a showstopper that I am sure is fixeable.)

First - hardware and relevant background.

I am in China. (The problem is not the great firewall.)
I had been happily surfing/posting/chatting without problems for months.

Laptop 1- Toshiba dual-boot with vista and Ubuntu 8.1 (Just upgraded to 9.04)

Laptop 2 - Asus eee1000H dual boot with XP and Jaunty 9.04 clean.

Since my D-Link routers failed twice, I replaced with an Asus WL530G V2. 

I know you hate to hear this, and I truly hate to say it because I so want to use Linux and was happily for over nine months (Previously PCLinuxOS), but I simply cannot use Ubuntu. 

Everything works, but I have to switch to windows on both machines to:

1) Send Yahoo webmail. (XML error on send, and preview pane refusing to load.)
2) Post messages to this and other groups. (I get the "Connection Interrupted The connection to the server was reset while the page was loading." whenever I try to post - or a timeout.)

In Firefox: a request to open "posting.php" and asks me which program to open it with, or where I want to save the php page for another group. The same page in Konqueror 4.2.2 (KDE 4.2.2) gives the timeout exactly as before.

I use Firefox and Thunderbird, all latest updates, on both machines and operating systems. (The posting problem occurs in Konqueror as well, which rules just Firefox out.)

Now, when I search the web I see other posts with xml errors on yahoo, on Ubuntu asking to "open" a xxx.php file, and similar problems to mine, but no solutions.

What's up? It has to be simple. If Windows can work, it can't be hardware or the firewall in China. If it doesn't work on Ubuntu 8.1 and 9.04 as a clean install - same errors - then it has to be an Ubuntu issue.

What can I do to see what's wrong. Millions of users are using Ubuntu, as I was, so i know it has to be a setting somewhere - but whatever it is, it's affecting two different Ubuntu revisions on the same wireless point, but not windows.

Sorry for my long post, but there has to be an answer or a "Process of elimination tree" I can follow. One Linux website even tried to tell a user that nobody else, anywhere, has this problem. My searches show otherwise.

DavidJ.

Edit.
FF was the main problem.
Opera solved most, but still need to come to XP to "Advanced Edit" such as this OP.

Am downloading a new distro to see if i have better luck there.
DavidJ.

---

### Post by danwood76 on 2009-05-10
Did you install the eepc and upgrade the toshiba from the same install CD?
there could be an error on the install media and you might need to redownload/reburn and try again.

---

### Post by DJB1609 on 2009-05-11
> **danwood76 said:**
> Did you install the eepc and upgrade the toshiba from the same install CD?
there could be an error on the install media and you might need to redownload/reburn and try again.

Thanks. Different media, and I validated the Md5Sum. 

Absolutely *everything* else works, which is why I'm stumped.

When searching the web, there seems to be a spurious selection of posts, with no concrete answers. Many original posters don't follow up with a *solved* and at least one said it just started working.

It really pains me, as I do my presentation in Linux, most of my photo (hobby) work, and used to do all the surfing. As I saif, XP almost came off my netbook!

I'm again replying to this from XP after Jaunty timed out again.

I just "Upgraded" 8.1 on the Toshiba to Jaunty, (Via Upgrade) and still have the same problems.

Thanks for the interest in helping. I may try one more d/l and burn - but if that doesn't work then I can't use Ubuntu.

DavidJ.

---

### Post by danwood76 on 2009-05-11
It might be an issue with the router.
It would be good if you could try using another one.

At home my router messed up because my brother connected his mobile phone to it and it screwed the DNS servers, the odd thing was only the XP machines were affected and my two linux boxes still worked fine.

Have you treid clearing your cache in firefox?
That can sometimes help a lot with sites that arent loading properly.

---

### Post by DJB1609 on 2009-05-11
> **danwood76 said:**
> It might be an issue with the router.
It would be good if you could try using another one.

At home my router messed up because my brother connected his mobile phone to it and it screwed the DNS servers, the odd thing was only the XP machines were affected and my two linux boxes still worked fine.

Have you treid clearing your cache in firefox?
That can sometimes help a lot with sites that arent loading properly.

Thanks. I've never had a problem with XP on this router, and firmware updates haven't cured it. Unless it's incompatible with Ubuntu/Linux, it shouldn't be the router. Replacing the router is not an option at the moment.

I've had fresh installs and cleared the cache. Your advice did clear this up for some, as I'd seen this on a search before.

Why would .php cause a problem? I can post to [http://e-group.uk.net/forum/](http://e-group.uk.net/forum/)

Does this use a different protocol?

Remember, I can surf 100%. It's just posting to newsgroups, and the xml error, so it must be a protocol issue.

Again, I would like to thank you and anyone for assistance.

DavidJ.
(Still posting from XP :( )

---

### Post by danwood76 on 2009-05-12
Php errors are normally server side issues as the php is processed server side before it sends the finished page on. Though as nobody else has these issues with these forums from linux it does seem odd.

Can you access these sites (post etc) through a free web proxy?
That will determine if its a host issue as the proxy will deal with all server requests.

Another thing you could try is changing your DNS servers, I'm not sure how legal/possible that is in china but the OpenDNS servers are pretty good.

---

### Post by DJB1609 on 2009-05-12
> **danwood76 said:**
> Php errors are normally server side issues as the php is processed server side before it sends the finished page on. Though as nobody else has these issues with these forums from linux it does seem odd.

Can you access these sites (post etc) through a free web proxy?
That will determine if its a host issue as the proxy will deal with all server requests.

Another thing you could try is changing your DNS servers, I'm not sure how legal/possible that is in china but the OpenDNS servers are pretty good.

I tried OpenDNS servers from this page:
[http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Yes the problem is odd, and infuriating as I am sure it's a rogue setting somewhere.

My next message, if it is posted, is from Jaunty via a proxy. If there is no message, then it failed.

---

### Post by DJB1609 on 2009-05-12
> **DJB1609 said:**
> I tried OpenDNS servers from this page:
[http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Yes the problem is odd, and infuriating as I am sure it's a rogue setting somewhere.

My next message, if it is posted, is from Jaunty via a proxy. If there is no message, then it failed.

And back to XP. :(

I got the same error "The connection to the server was reset while the page was loading". I used web4proxy.com.

I don't really want to reinstall, as It's a fresh install, but I am downloading again.

DavidJ.
ps. The OpenDNS instructions from that page referred to earlier slowed the web a bit and, ironically, wouldn't reopen the page of instructions - it timed out!

---

### Post by danwood76 on 2009-05-12
The instructions on that site are a bit old.
If you right click the network icon in the notification area and select 'edit connections' find the connection you use (either wired or wifi) and edit its settings the dns server addresses are in the IPV4 part. (You need to select DHCP address only to unlock them) then enter the two DNS servers click apply and then left click the icon and reclick the network connection to make it reconnect and use the new servers.

Its possible that the great firewall of china blocks the DNS servers.

---

### Post by ckonestroh on 2009-05-12
Question:  First off Is this a home router or a business?

Second if its a home router its best to replace one about every 2 to 3 years mine lost wifi....

If this is your home router put computers before the router do you get a clear connection to the internet if so then its the router.....
 
You need to test computer out from behind router to determine which one is causing problems

---

### Post by DJB1609 on 2009-05-13
> **danwood76 said:**
> The instructions on that site are a bit old.

Its possible that the great firewall of china blocks the DNS servers.

I could change the servers, but not solve the problem. Thanks for the new info.

> **ckonestroh said:**
> Question:  First off Is this a home router or a business?
<snip>
 
You need to test computer out from behind router to determine which one is causing problems

A home router, and it works fine in XP. 

Guys, please move the query to [http://ubuntuforums.org/showthread.php?p=7272043#post7272043](http://ubuntuforums.org/showthread.php?p=7272043#post7272043)

I am not alone, and there is more info there. 

DavidJ.

---

### Post by DJB1609 on 2009-05-14
OK,

I installed Opera on a clean Ubuntu Netbook Remix.

I can New post, edit posts, quick post but *not* advanced post.

What's with that?

It means I can edit my OP, but not the title - as that needs "Go advanced". I can open the advanced editor, but on click to save, absolutley nothing happens other than Opera connects, says it's receiving data and does nothing. 0kb transfer. Nil. Nada. 

Firefox is still bugged, which is why I tried Opera.

So. Firefox 5/10 - Opera 9/10.

Any idea why I can do all but "Advanced Edit"?

DavidJ.
(Remember I am in China.)

---

### Post by DJB1609 on 2009-05-14
It shouldn't be this hard. I've given up and am downloading another Distro now.

I've spent at least three days of my life just trying to use the bloody internet.

Life's too short.

Sorry, but I'm pissed off.

9/10 for Opera is better, but not enough.

DavidJ.

---

### Post by DJB1609 on 2009-05-20
Blocking IPv6 doesn't change things. Thank you for the suggestion.

Although it works in windows, and I can surf etc. in Ubuntu, does it matter if my wireless and ADSL modem have the same IP - 192.168.1.1?

Could that be an issue?

My Asus W530G V2 is the wireless, and I can access it at 192.168.1.1. I set it up as ppoE with the password etc. given by the ISP.

The Modem is a Chinese language ZTE XDSL 831, set up by the Chinese ISP. It has the same IP address, and I have to disconnect the Asus and go wired to access it's homepage - which is all Chinese!

If I have to change anything, it would have to be the Asus.

I know others can post from Linux in China from another forum.

Thanks, as any help is appreciated. (I don't want to give up!)

DavidJ.

---

### Post by DJB1609 on 2009-05-20
Although it works in windows, and I can surf etc. in Ubuntu, does it matter if my wireless and ADSL modem have the same IP - 192.168.1.1?

Could that be an issue?

My Asus W530G V2 is the wireless, and I can access it at 192.168.1.1. I set it up as ppoE with the password etc. given by the ISP.

The Modem is a Chinese language ZTE XDSL 831, set up by the Chinese ISP. It has the same IP address, and I have to disconnect the Asus and go wired to access it's homepage - which is all Chinese!

If I have to change anything, it would have to be the Asus.

I know others can post from Linux in China from another forum.

Thanks, as any help is appreciated. (I don't want to give up!)

DavidJ.

---

### Post by danwood76 on 2009-05-20
If the router and the modem have the same IP that _could_ be a problem.
Change the router to use a different subnet, so for example change it to 192.168.2.1
An address conflict (like this) could cause issues depending on how the router works.

---

### Post by DJB1609 on 2009-05-20
I am thinking it is a router/local network problem. I have two laptops sharing one Wireless router>Adsl modem.

When I had a D-Link wireless with an IP 192.168.0.1, I had no problem.

I first suspected it was an Ubuntu problem with changed hardware, and my thinking was vertical from there as Windows on both machines worked. I kept looking at it as a Linux problem.

Rethinking: I moved house, got a new (Chinese) modem *and* a new router because the D-Link failed to connect.

I am suspecting the Chinese modem and will try a friends D-Link ADSL+ modem later, as I know it has a different IP address.

I seem to recall Vista throwing me "IP conflict" messages on occasion, but for some reason everything still worked; and they are rare.

Again, I thank everyone for their assistance with my ignorance. One of the strengths of Linux is the community support and I am very grateful.

DavidJ.

(Sigh) New hardware, no change. Given up. Trying to get Linux to work here makes XP/Vista's pitfalls look comforting.

---

