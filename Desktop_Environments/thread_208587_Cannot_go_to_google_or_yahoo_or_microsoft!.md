---
title: "Cannot go to google or yahoo or microsoft!"
date: 2006-07-03
forum: Desktop Environments
---

### Post by rsriley on 2006-07-03
Hi,
I installed the Dapper Drake 6.06 today as a dual boot (with Windows XP Home as the other) today.  I had previously set up partitions for Linux and so had no real trouble marking them up for the root and swap installation.  The installation went fine, and I noticed that the installation program automatically checked for updates (which I didn't install).  However, web browsing with Firefox (which I also use with windows) is VERY erratic when I am running Ubuntu.  I CANNOT get to some sites (yahoo, google, nytimes, microsoft) at all when running Ubuntu.  I can get to others, however - ubuntu, mozilla.com, mozilla.org, canonical.com, chessbase.de, etc.  I use web-based mail, so not getting to google (gmail) or yahoo is BAD for me in ubuntu.  

I have dsl and access the internet through a dsl modem/router combination. 

As a check, I exited Ubuntu and re-booted into Windows.  I could access yahoo, google, etc., fine!

I cannot imagine why firefox (ubuntu/linux version) would NOT be able to access google or yahoo in Ubuntu but CAN in windows.

Suggestions anyone?

Other app's seem to run fine - openoffice.org 2 (which I also run in windows), for example.

Thank you for ANY help!

---

### Post by Bloch on 2006-07-03
This is certainly puzzling. There is no reason Firefox would not show google and yahoo.

On my system even when I type "google" in the location field, the browser interprets this to mean [http://www.google.com](http://www.google.com)

Really, try it again. If your browser works with some sites then it will work with all - or at least show something. There are sites which make use of F;ash that you might not have installed, but even these show something.

I can only suggest that maybe your connection broke and started again. Run gnome-monitor to see if the connection is active when you go to different sites.

---

### Post by XAsmodeanX on 2006-07-03
Go to System -> Administration -> Networking -> Ethernet Connection

Click on the DNS tab.

There should be a list.  Might have one or two entries.  If you see that one of the IP addresses is the address to your dsl modem/router, then remove that line and only that line.  Save.  Exit.  Bam, should work.

---

### Post by rsriley on 2006-07-03
[QUOTE=XAsmodeanX]Go to System -> Administration -> Networking -> Ethernet Connection

Click on the DNS tab.

There should be a list.  Might have one or two entries.  If you see that one of the IP addresses is the address to your dsl modem/router, then remove that line and only that line.  Save.  Exit.  Bam, should work.[/QUOTE]
Hmmm.  I will try it.  I'll let you know.  I don't know enough to understand why I can access some sites and not others.  For example, I can access the ubuntu support pages and the forum page, but when I try to go to the English forum ([www.ubuntuforums.org)](www.ubuntuforums.org)), it only loads 90% or so - every time - but never fully loads.  Google and yahoo destinations don't even TRY to load.  But your suggestion intrigues me and I will try it.  Thank you for your proposal.

---

### Post by rsriley on 2006-07-03
[QUOTE=Bloch]This is certainly puzzling. There is no reason Firefox would not show google and yahoo.

On my system even when I type "google" in the location field, the browser interprets this to mean [http://www.google.com](http://www.google.com)

Really, try it again. If your browser works with some sites then it will work with all - or at least show something. There are sites which make use of F;ash that you might not have installed, but even these show something.

I can only suggest that maybe your connection broke and started again. Run gnome-monitor to see if the connection is active when you go to different sites.[/QUOTE]

Hi - Thank you for the reply.  However, the reply right below yours was right on the money (see what he suggested).  I deleted the address to my dsl modem/router from the DNS list and now I can access ALL sites.  I find this simply amazing!  

Bob R.

---

### Post by Bloch on 2006-07-03
Can you explain why this works, XasModean?

And I think it is very important to write down any DNS you are about to delete.
My list had just one DNS in that list, the one to my modem. When I deleted it I had no connection at all.

---

### Post by rsriley on 2006-07-03
[QUOTE=XAsmodeanX]Go to System -> Administration -> Networking -> Ethernet Connection

Click on the DNS tab.

There should be a list.  Might have one or two entries.  If you see that one of the IP addresses is the address to your dsl modem/router, then remove that line and only that line.  Save.  Exit.  Bam, should work.[/QUOTE]

[QUOTE=Bloch]This is certainly puzzling. There is no reason Firefox would not show google and yahoo.

On my system even when I type "google" in the location field, the browser interprets this to mean [http://www.google.com](http://www.google.com)

Really, try it again. If your browser works with some sites then it will work with all - or at least show something. There are sites which make use of F;ash that you might not have installed, but even these show something.

I can only suggest that maybe your connection broke and started again. Run gnome-monitor to see if the connection is active when you go to different sites.[/QUOTE]

This to XAsmodeanX:  your suggestion above worked!  I have no idea why (deleting the address to my dsl modem/router) it did work but it did.  Simply amazing.  Thank you!

---

### Post by rsriley on 2006-07-03
Hi Bloch - I wondered about deleting the address to my dsl modem/router, also, but it worked.  I don't have to worry about forgetting it (your suggestion was an important one).  I have known that address for a couple of years and it is in documentation from qwest.com.  It is the address I need in case I have to make setting adjustments to the unit.  Thank you again for your getting involved here - but I am still mystified as to how this DNS deletion worked.

---

### Post by Bloch on 2006-07-03
Glad it worked out riley, (I'm a Reilly too, but spelled this way!)

My question was meant to be for XAsmodeanX, I've edited my mistake.
For the sake of other users a short note on why this works would close this thread.

---

### Post by rsriley on 2006-07-03
Maybe, long ago, our common ancestors were part of the prominent family in County Cavan?  It is nice to meet you!

---

### Post by XAsmodeanX on 2006-07-04
I believe the reason that it works has to do with using a 2.6 kernel and its ipv6 support.  I've had problems when I connected to my router with dhcp because it aquires an ip (which is fine) and 2 domain name servers (DNS, one of which was bogus).  It was like the ipv6 got confused by what the router was sending and threw in that "nameserver" which was actually just the ip address to the physical router and not a nameserver.  So, the reason you couldn't connect to any websites was because whenever you when to a site, it would try to look up the name on the bogus nameserver and it would fail to resolve since most routers do not double as suitable nameservers.  By deleting the ip address of the router in the DNS list, it no longer hangs when trying to resolve a domain name and thus, your internet is back.  It should be noted however that you did in fact have internet the whole time, for instance you could log into an instant messenger or type the ip address of the website directly into your browser, just couldn't type in a name and get directed to a website.

Some people have this problem, some don't, but when he described what was going wrong it definitely sounded like that was the problem.  I went through the same thing with my internet and that's how I knew to fix it.

Alternatively you could have edited the /etc/resolv.conf file and deleted the whole line that listed your router and left the rest intact.

Remember, every time your DHCP lease is renewed your DNS list should be updated.  And every time it updates, it's gonna throw in that bogus entry.  My work around is to use a static ip address so that my settings never change and therefore am never bothered with DHCP.

---

### Post by Bloch on 2006-07-04
Thanks for that comprehensive explanation XAsmodeanX.


Yep Riley, my parents are from Cavan. I now the area well. You wouldn't have to go back many generations.

---

### Post by rsriley on 2006-07-04
Hi XasmodeanX - you wrote:
"Remember, every time your DHCP lease is renewed your DNS list should be updated. And every time it updates, it's gonna throw in that bogus entry. My work around is to use a static ip address so that my settings never change and therefore am never bothered with DHCP."

I have Qwest as my ASDL line and ISP provider, and they want us to use a dynamic IP (for whatever reason - I don't know enough to dispute it).  And as you say, I often have to go to the DNS list to delete the internal address of the modem/router.  I think this is a bug with Ubuntu - am I mistaken?  I will have to see how we report a bug (I am a BRAND newbie to Ubuntu, as you can tell).

Bob R.

---

### Post by rsriley on 2006-07-04
Hi All,

XasmodeanX wrote:

"Remember, every time your DHCP lease is renewed your DNS list should be updated. And every time it updates, it's gonna throw in that bogus entry. My work around is to use a static ip address so that my settings never change and therefore am never bothered with DHCP."

I have done just what you did - and now when I log into Ubuntu, the internet connection is alwasy full on, with no hesitation.  In fact, my download speed with Linux is about 5% faster than it is with Windows XP, predictably.  Thank you again for your tips.  It looks like the DHCP in Ubuntu might need some tuning before the next release.

Bob R.

---

### Post by joshu on 2006-07-04
[QUOTE=XAsmodeanX]Go to System -> Administration -> Networking -> Ethernet Connection

Click on the DNS tab.

There should be a list.  Might have one or two entries.  If you see that one of the IP addresses is the address to your dsl modem/router, then remove that line and only that line.  Save.  Exit.  Bam, should work.[/QUOTE]

Thank you for your post! 
I ran into the same issue: I could retrieve email, browse the web with Links in text browse mode, and even with Konqueror - but Firefox, Epiphany, Mozilla etc wouldn't work, not in Ubuntu, and not in SUSE either. 
I followed your advice, looked up the DNS list, and sure enough, my Qwest router's IP address was listed. I deleted it. Now Firefox is working just fine.
Thanks again
J

---

### Post by rsriley on 2006-07-04
Hi Joshu - as long as you are using the "DHCP" in the Network Setup (ethernet), you may have to use the work-around every time you log in.  I followed what was said above by XAsmodeanX,  "My work around is to use a static ip address so that my settings never change and therefore am never bothered with DHCP."
  I may be able to help you with the settings for static IP address (your internal LAN - DSL modem/router and your PC).  At least I can tell you what data I put in each window for static IP settings.

---

### Post by joshu on 2006-07-05
[QUOTE=rsriley]Hi Joshu - as long as you are using the "DHCP" in the Network Setup (ethernet), you may have to use the work-around every time you log in.  I followed what was said above by XAsmodeanX,  "My work around is to use a static ip address so that my settings never change and therefore am never bothered with DHCP."
  I may be able to help you with the settings for static IP address (your internal LAN - DSL modem/router and your PC).  At least I can tell you what data I put in each window for static IP settings.[/QUOTE]
Yup, you're right, I've had to repeat the procedure after logging out and back in an hour later. But as far as I can remember, my ISP strongly recommended that we use DHCP.
It seems to me this is an issue between the Qwest router and Linux. I encountered the same problem in SUSE, and used the same workaround - deleting the router's IP address entry. 
What is baffling to me is that 
(1) Konqueror is able to browse the web, both in Dapper 6.06 and SUSE 10.1; 
(2) booting into Windows XP I can browse the web;  
(3) on my apple powerbook with OS X I can browse just fine.
I'll find out from my ISP if I can switch to a static IP address for the linux machine, and sure would appreciate any pointers re static IP settings.
Thanks!

---

### Post by rsriley on 2006-07-06
Hi Joshu - I doubt your ISP will care if you use the static ip address - that is only for your own LAN (pc and modem), I **think**, and wouldn't affect their network at all.

Here are my settings:

1.  Go to <system-administration-networking>
2. Select <ethernet connection> and then the <properties> button.
3. Configuration - select "Static IP address" instead of DHCP
4. IP Address (of my own PC on my LAN): 192.168.0.2
5. Subnet mask (automatically prefilled): 255.255.255.0
6. Gateway address (i.e., our adsl modem/router on our LAN): 192.168.0.1

Your numbers might or might not match the above - I use my browser to get to the modem (for settings) by typing in 192.168.0.1 in the web address bar.  Your modem would have a similar instruction, probably.  Check its manual.

If in doubt, however, ask an expert before following the above!

Bob R.

---

### Post by meho_r on 2007-11-14
To revive old post/problem. Recently I started having same problem. Seems that my ISP changed something because all worked till about 3-4 days ago. I changed IP to Static and put there my IP address (retrieved from IPchicken.com) instead of previous entry which was 192.168.1.50 (On my AP default was 192.168.1.1). But, strange, although I can open all sites now, there is delay about 3-4 sec., sometimes even more, before browser  starts opening it. It is annoying. Is there something that can be done in this regard? Thanks

---

