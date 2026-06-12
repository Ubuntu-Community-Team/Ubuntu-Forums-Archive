---
title: "Internet surfing &amp; downloads really slow"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Linux-Freedom on 2006-06-20
Hello,  I just installed Ubuntu 6.06 Desktop yesterday.  This is my first time using any linux package.  But I have been using computers for almost 30 years. I installed Ubuntu on my Intel Pentium III machine with 256 MB of RAM and a 160GB Harddrive.  This machine had XP Professional on it and worked without any issues.

The major problem I have is surfing the internet...I basically can't.  It is too slow.  The majority of downloads from various sites time themselves out, Internet pages take between five to ten minutes to load, if they load at all.  On my other 3 machines (2 running XP Professional, 1 running XP Home), the same pages load in less than five seconds!  I have a high speed ADSL line and the computer is hooked up through a Linksys router.  The computer is assigned a static IP address.  The three other computers  are hooked up the same way the Linux box is hooked up (with different static IP addresses).  And as noted above, the three computers have no trouble accessing the internet.

I have spent all last night trying to figure this out.  I have changd the IPV6.  I can ping the router and get < 0.46 ms (so I know that the link to the box works really well).  But any ping to the internet is really slow – over 160 ms if it does not time out.

The system monitor shows that my CPU is running between 13% – 26%.  With regards to memory: I am using 134.9 of 250 MB.  I am also using 70.4MB of 5.1 GB in Used Swap. The issue appears with the Network History...for the most part, it does not receive any bytes.  Every now and then it shows a little bit of activity (anywhere from 59 bytes/s to 2.9 KB/s) of and then flat lines.

I am lost on what else to try.  All suggestions are greatly welcomed.

Thank you

Richard

---

### Post by tribaal on 2006-06-20
Maybe you already tried this out, so sorry if you did:

Open up firefox.
In the URL bar type "about:config"
in the "filter" bar that shows up, type in "ipv6".
Double click on "disable.ipv6" (so that it says "true").

This should dramatically speed up the internet, if it was the source of the problem. Firefox uses it's own set of internet preferences, not the system's (same goes for http proxies and stuff).

Otherwise, try adding your default gateway to yout /etc/hosts file. This way the gateway's name resolution should be much faster.

Theses tricks helped me have a decent internet speed. Hope it'll help you too!

- trib'

---

### Post by Kouya on 2006-06-20
yup that is an option that will prob work...another is 

terminal:
sudo gedit /etc/modprobe.d/bad_list

then type "alias net-pf-10 off" and save

---

### Post by stanz on 2006-06-20
yeah...if its all FFox, you might wanna spend some time at their site.
There's good info on their wiki, in their forum's, etc...
Ain't no thing joining the forum and getting info- like here!

---

### Post by Linux-Freedom on 2006-06-20
Thank you all.  Last night I disabled IPV6 through the about:config process and also edited the /etc/modproe/aliases file by putting a # in front of the IPV6 line.  Neither of these two worked.

Tonight I will try:
- adding my default gateway to my /etc/hosts file;
- modify bad_list; and
- check the firefox wiki.

I was so hoping last night that it was the IPV6 issue, but it appears that I have another issue.  While the surfing could be a Firefox issue, I thought that the downloads could point to another problem.  This is based on the assumption that the add/remove programs does not use Firefox to download updates?  When I was trying to add programs, the downloads would time themselves out.

Just before I left, I noticed that in the Java scripting window in Firefox it appeared to have a number of errors.  I can't remember what they were, but I was wondering if someone could look at theirs and let me know if they had any errors.  The errors were on various web pages, including the Ubuntu forum pages.

---

### Post by Linux-Freedom on 2006-06-20
I am at a loss and starting feel like... ](*,)
 
I have tried everything suggested and I my connections still times out. Both using Firefox and trying to download using the package downloader. For one page it loaded quicker than any page. But that was it...never to be repeated.
 
I am certain that it is not an IPV6 issue. I have confirmed that IPV6 is off by running "ip a | grep inet6" which returned nothing!
 
I have added 192.168.1.1 to my hosts file.
 
I have pointed by DNS to my ISPs nameservers.
 
My ping rates appear to have gotten faster.
 
I can do "hosts www.google.com" and it returns the alias name and address (although it did include a note that connection timed out, no servers could be reached). I have tried the hosts command with some other site and received no errors and timing was good.
 
Some of the javascript errors I was talking about in my earlier post includes:
 
"Unknown property 'word-wrap' Declaration dropped"
 
"Error in parsing value for property 'white-space' Declartion dropped"
 
"document.getElementByld("titlesearch") has no properties"
 
"Expected declaration but found '/'. Skipped to next declaration"
 
"S is not defined"
 
Maybe a bit more information about my setup will help?
 
- I have a home network 192.168.1.1 (which is the one the linux box is on) and an office network 192.168.2.1.
- The two networks are connected by a VPN through two Linksys BEFVP41 routers.
- Each of the routers have static IPs from the ISP.
- The office server is a Microsoft Small Business Server 2003.
- All computers on the network run Microsoft XP.
- I do not have any problems with any of the computers other than the linux box.
 
If anyone could please give me some more suggestions and ideally the solution :D.  If I cannot find a fix, I will have to reinstall XP. Which is really too bad because I had hoped to convert a number of my machines to Linux.

---

### Post by stanz on 2006-06-21
Geez L F,  I'm no pro here...~ sry can't throw a quick fix @ cha.
I'ld do a fresh re-install, - not knowing anything else. Since, I think 
firefox comes bundled with 6.06, it's not like you got a defective 
download from their site.
And your saying Synaptic Package Manager is slow too? {or whatever comes with}
=You got Firewall? On?
=Linksys isn't set DHCP? -no need for static ip,- which you say, linux box has 2?
=Have you shut everything down, & restarted, in order?
=DSL service? -provider can work with Linux?
#-o
I don't mean to waste your time...I'ld sure like to be reading, someone's fix- for ya!
Give this a few more days ~ if ya can... a professional will pass thru here! 8-)

---

### Post by Linux-Freedom on 2006-06-22
Thank you Stanz.  You are not wasting my time at all.  I really appreciate all of the suggestions.

Tonight I reinstalled Ubuntu.  It did not fix the problem.  So I installed a copy of Linspire that I had.  The internet surfing & downloads was also really slow in Linspire.  So I now knew that it was not just a Ubuntu issue.


So I decided to look at the hardware.  And wouldn't you know it, the cable between the computer and router was the problem.  As soon as I replaced the cable, I was able to surf and download very quickly in Linspire.  The cable worked just enough to fool me into thinking it was good.

So, for the 3rd time, I reinstalled Ubuntu.  (Boy I really hope that this is worth it :D) And without any changes to IPV6 etc, it ran perfectly =D>.

Couple of suggestions to the development team (if you are reading this email)

1. Have a way in Ubuntu that one can test hardware like cables and cards etc (this would have saved three days of ](*,)); and

2. Have the system advise if the IP address chosen in a static network is already taken.  During testing I had mistakenly assigned an IP address to the Ubuntu box that was assigned to a windows box.  Although Ubtuntu stopped working, it  did not complain or tell me what the problem was.  At approximately the same time, the windows machine stopped working.  When I opened up the networking in the windows machine it notified me that the IP address was also assigned to another computer.  That sure saved me a lot of time.

Thanks for everyone's help

Richard

---

### Post by Kouya on 2006-06-22
Woot!!! good for u!!

---

