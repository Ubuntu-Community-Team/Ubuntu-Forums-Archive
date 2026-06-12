---
title: "DVD backup in Breezy"
date: 2005-10-30
forum: Desktop Environments
---

### Post by dickmorrell on 2005-10-30
Having followed the howto's with wine and other methods discussed here I saw most of them as a waste of time and daft ways to skin a cat. Adding CPU overhead to an already CPU hungry activity makes no sense really so I needed to find a totally generic Linux way of backing up AND burning to same or second drive.

Enter a tool developed by a Mandrake Cooker developer called XDVDShrink. RPM's are available or feel free to grab a deb I've just made available on one of my US mirror servers at [http://www.force-majeure.info/breezy/dvdshrink_2.6.1-4_ubuntu_unofficial.deb](http://www.force-majeure.info/breezy/dvdshrink_2.6.1-4_ubuntu_unofficial.deb)

With libdvdcss and all the usual codecs on Breezy it's actually backing up better than CloneDVD or DVDShrink would under XP with faster read and rip times. Oh and no Wine.

Either use the latest RPM file from Sourceforge or the .deb I made above.

Read more at the Sourceforge website as it is either shell or GUI (perl-gtk2) based depending on the script or the perl command you use. Either way I've backed up 2 DVDs in the last two hours effortlessly.

Info online at [http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/) from the maintainer himself.

Enjoy - for many this was the last dependancy on dualboot or keeping a Windows box free. Not any more personally.

Richard

---

### Post by vassie on 2005-10-30
Thanks, seems to working fine so far

Just one question, how do I get the GUI working?

Ben

---

### Post by vassie on 2005-10-30
Don't worry, found it

xdvdshrink.pl

Ben

(PS This is fantastic, another peice in the "Remove Windows" jigsaw, thank you)

---

### Post by manicka on 2005-10-30
xdvdshrink is a nice program but I still prefer DVDshrink under wine, which now works perfectly with latest 0.9 beta release of wine.

A little CPU intensive as you say, but worth it for the results and features provided.

---

### Post by dickmorrell on 2005-10-30
Excellent Wine rocks, but my initiative as it has been for the last ten years wherever people listen to me when I talk about Linux is to move people entirely. Hence when Sane first appeared I was like a pig in the proverbial, same with Hylafax, same when HP released their first GPL'd Officejet project work. So where possible if I can find an alternative without having to use Wine it makes more sense to use it. It also makes for a better experience and better performance too.

Richard

---

### Post by NewbieNik on 2005-10-30
[QUOTE=dickmorrell]Excellent Wine rocks, but my initiative as it has been for the last ten years wherever people listen to me when I talk about Linux is to move people entirely..............So where possible if I can find an alternative without having to use Wine it makes more sense to use it. It also makes for a better experience and better performance too.

Richard[/QUOTE]

Its a little off the topic, but mention samba, squid and dansguardian. This provides file-sharing, web-caching and content-filtering for a network for some time and effort. Microsoft solution is W2k3 server and ISA server costing around £2,500 GBP and with less support!!!
For home-users, I have Windows apps running on wine at 20-30% faster than they do in XP SP2....Thats the tip of the iceberg!! Give the LiveCD to people an let them see what is available.....If you program it, they will come... (I'm sure I've heard that somewhere??!!)

---

### Post by stoeptegel on 2005-10-30
Looks nice. What does xdvdshrink different then k9copy?

---

### Post by matva on 2005-10-30
cool nice prog. how bout doing dvd5 isos, is that possible? I see where you can select by title, but if i want all the titles? 
how bout making a menu entry in the applications? Any icons available ?
thx

---

### Post by dickmorrell on 2005-10-30
DVD5 iso's totally doable

"Its a little off the topic, but mention samba, squid and dansguardian......" Umm I employed the Dansguardian author and gave him a salary and a full time directorship. That count ? I also worked with the Samba creators for three years fulltime at Linuxcare and VA and still do on and off. What I'd like is a proper Perl/PHP front end to Ubuntu server for ClamAV/Spamassassin with RBLs, proper vhosting and mail aliasing, domain management, awstats and some other cool toys (akin to what Contribs SME / Mitel SME server once stood for before the numpties threw the toys out their combined pram). Stability combined with updates. Thats your success story. If I had the time and wasn't flat out protecting 6m internet users I'd stick my hand up...

Don't think there are the hours in the day. I would fund it though same as the other opensource projects I provide bursaries for. Anyone want to take the mantel and come up with a plan ?

Richard

---

### Post by NewbieNik on 2005-10-30
[QUOTE=dickmorrell]DVD5 iso's totally doable

"Its a little off the topic, but mention samba, squid and dansguardian......" Umm I employed the Dansguardian author and gave him a salary and a full time directorship. That count ? I also worked with the Samba creators for three years fulltime at Linuxcare and VA and still do on and off. What I'd like is a proper Perl/PHP front end to Ubuntu server for ClamAV/Spamassassin with RBLs, proper vhosting and mail aliasing, domain management, awstats and some other cool toys (akin to what Contribs SME / Mitel SME server once stood for before the numpties threw the toys out their combined pram). Stability combined with updates. Thats your success story. If I had the time and wasn't flat out protecting 6m internet users I'd stick my hand up...

Don't think there are the hours in the day. I would fund it though same as the other opensource projects I provide bursaries for. Anyone want to take the mantel and come up with a plan ?

Richard[/QUOTE]

Ah ,but can you pat your tummy and rub your head??

I am suitably impressed and thank you and others for their dedication and hard-work and if I had an ounce of your knowledge or expertise I would gladly volunteer to help. 
Even if it was just sweeping the floors so you could remove that broom.........

---

### Post by bionnaki on 2005-10-30
thanks for the deb.
I havent installed it yet.
just curious tho
how does this compare to thoggen?
does it burn or just rip?

I am currently using dvdshrink via wine
but I do prefer to use linux apps over win32 apps.

---

### Post by dickmorrell on 2005-10-30
Glad to see that the great unwashed still live and breathe Nick

Seriously the more people who stick to Linux native apps and move away from crud like CrossOver and the need to use Wine etc then the faster we'll evolve, was saying this 5 yrs ago and still saying it now. More gtk apps give more power to the elbow.

---

