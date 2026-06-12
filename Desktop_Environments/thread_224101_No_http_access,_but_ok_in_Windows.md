---
title: "No http access, but ok in Windows"
date: 2006-07-27
forum: Desktop Environments
---

### Post by code-breaker on 2006-07-27
I am a new ubuntu/linux user. I have a dual-boot setup, and I have been using dapper almost exclusively for about a month. I've had a tough time getting my wife on the bandwagon, however, and every little ubuntu glitch is taken by her as one more huge reason *not* to use it. 

Yesterday, we lost the ability to browse the web. Firefox just times out on any page we enter. At first I thought it was the dsl connection, but I can check and receive imap mail (and send smtp), I can ftp & fileshare, and most painful of all, I can browse the web just fine in windows. I tried both ie and firefox in windows, both work fine.  

Any suggestions?

---

### Post by x64Jimbo on 2006-07-27
What about another browser in Linux? Try that first - it will tell us whether you're experiencing problems on the browser or OS level.

---

### Post by Ares Drake on 2006-07-27
Sounds to me as either your Firefox is malconfigured or as if your DNS was broken. DNS resolves the IP addresses to the url ([http://www.something.com](http://www.something.com)) so having it broken could explain your problems.
You can either configure it by editing the file /etc/resolv.conf - or, easier for new users, with the graphic configuration tool: System -> Administration -> Network -> DNS
If you need DNS addresses, just google for one near you. Hope this helps!

---

### Post by x64Jimbo on 2006-07-27
> **Ares Drake said:**
> Sounds to me as either your Firefox is malconfigured or as if your DNS was broken. DNS resolves the IP addresses to the url ([http://www.something.com](http://www.something.com)) so having it broken could explain your problems.
You can either configure it by editing the file /etc/resolv.conf - or, easier for new users, with the graphic configuration tool: System -> Administration -> Network -> DNS
If you need DNS addresses, just google for one near you. Hope this helps!
If DNS was broken, wouldn't IMAP/SMTP be broken as well? I really think this probably has something to do with that firefox update that just happened.

---

### Post by code-breaker on 2006-07-27
I just remembered something: I use a bash script that accesses freedb.org using wget, and that wasn't working either. But I will try another browser tonight, and take a stab at the dns suggestion if needed, and report back. 

Thanks for the quick replies.

---

### Post by code-breaker on 2006-07-27
OK. So, I installed konqueror, and I can browse the web with that. I thought maybe Synaptic might have trouble downloading, but no. So maybe it is Firefox. I uninstalled/reinstalled, still no-go. 

Any ideas?

---

### Post by x64Jimbo on 2006-07-28
Try deleting your firefox profile and restarting firefox to have it create a new one for you?

---

### Post by Hikaru79 on 2006-07-28
Just to make sure it's not the DNS, try connecting to, for example, [http://64.233.187.99](http://64.233.187.99) . If that lands you at Google, then you definitely have a DNS problem.

EDIT: Oh, never mind. Just read about Konqueror.

---

### Post by x64Jimbo on 2006-07-28
The first post made it pretty clear that it wasn't a DNS issue. IMAP and SMTP wouldn't work without DNS.

---

### Post by code-breaker on 2006-07-28
This is a very curious problem. When I open firefox (after a reboot), it can't find any websites. But, if I close firefox, open konqueror, and open a webpage (like google), I can then re-open firefox, and it can then find that page! It cannot find other pages until they are first opened in konqueror. 

Any ideas?

---

### Post by x64Jimbo on 2006-07-28
Did you try deleting your firefox profile like I said?

---

### Post by code-breaker on 2006-07-29
I deleted the profile, no-go. Then the whole firefox folder, nope. Then uninstalled, deleted all traces, and reinstalled, nothing. Then out of desparation, did a full reformat, ubuntu reinstall, STILL the same problem. Interestingly, synaptic could not connect to the internet to get updates. Eventually I was able to get some stuff installed (it does seem to work intermittently, sometimes), so I installed konqueror, lynx, and epiphany. Epiphany and lynx have the same problem as firefox. I tried to install some other programs that happen to be from archive.ubuntu.com (I could tell by clicking "show progress of single files" while downloading), synaptic wouldn't download them, so I pasted that domain into konqueror, and sure enough, when I tried again in synaptic it started downloading. 

I have tried the usb connection on my dsl modem, which has both ethernet and usb. No difference.

---

### Post by x64Jimbo on 2006-07-30
Woah. This is way out of my league, unfortunately. Can someone else please step in and help out? I am completely out of ideas.
P.S. It sounds like your box is possessed. :P

---

### Post by msandersen on 2006-07-30
Maybe your wife is right :)
So, is it only Gnome apps that are affected? IE, can other KDE apps other than Konqueror connect to the web? wget isn't either, so if it has trouble, I don't know. Can you ping Google or your ISP? Maybe it's a proxy or gateway issue or something. Maybe your ISP changed its setup in a way that affects default Linux but not Windows. You could try contacting them and ask.
Failing, that, there's always Windows... :o

---

### Post by x64Jimbo on 2006-07-30
[quote=msandersen] Failing, that, there's always Windows... :eek:[/quote]
Blasphemy! Heretic! Burn! ;)

---

### Post by decryptoknight on 2006-07-30
Did you set firefox to direct connect to the internet?
Do you have a firewall that sets port 80 only open bij use of the other browser?

try ftp. Look how that goes?

---

### Post by msandersen on 2006-07-30
> **x64Jimbo said:**
> Blasphemy! Heretic! Burn! ;)
I'll be sure to use K3B or GnomeBaker for that then... :cool:

---

### Post by x64Jimbo on 2006-07-30
> **msandersen said:**
> I'll be sure to use K3B or GnomeBaker for that then... :cool:
LMAO [IMG]http://www.online-thecatsmeow.com/images/Emoticons3/lmao.gif[/IMG]

---

### Post by code-breaker on 2006-07-31
Thanks for all the replies. Here is all the info I can think of:

-I can ftp just fine. I use the command line 'ftp' function now, and used gftp before the full ubuntu reinstall

-I could file share fine, before I did a full ubuntu reinstall (I lost amule)

-synaptic does not connect to anything, unless I first type in the domain in konqueror. same with automatix, wget, firefox, lynx, or seemingly any other app that uses http access. I tried to install swiftfox, but I have an amd64, and I think automatix only has a 32 bit version. Anyway, it won't run. 

-I am new to linux and ubuntu, so I don't really know about whether a firewall is installed. If it gets installed with the default installation, then I guess I have it. I did not install one myself.

-In firefox the status bar says 'connecting to www.google.com...' and never changes, until the request times out. As I have mentioned, once an address is entered into konqueror, I can access that domain. It is difficult to know exactly for how long I have access, but I would estimate about 15 minutes. After that, the domain is not accessible anymore (so I go back to konqueror, and enter the domain, and so on...)

-I can ping google.com, and ubuntu.com

-I can tracerout nytimes.com

-Some settings that might be of interest:
Under System/Network settings,
DNS Tab:
  DNS Servers
    192.168.0.1
    205.171.3.65
  Search Domains
    domain.actdsltmp
Hosts Tab:
  IP               Aliases
  ff00::0          ip6-mcastprefix
  127.0.0.1        localhost UbuntuDesktop
  fe00::0          ip6-localnet
  ff02::2          ip6-allrouters
  ff02::1          ip6-allnodes
  ::1              ip6-localhost ip6-loopback
  127.0.1.1        UbuntuDesktop
  ff02::3          ip6-allhosts

Under System/Network Tools,
Devices Tab:
Protocol       IP            Netmask/Prefix
IPv4           127.0.0.1     255.0.0.0
IPv6           ::1           128

Interface Information
  Hardware address: Loopback
  Multicast:  Disabled
  MTU:  16436
  Link speed: 
  State:  Active

Does anything look funny to anyone?

---

### Post by coffeecat on 2006-07-31
> **code-breaker said:**
> This is a very curious problem. When I open firefox (after a reboot), it can't find any websites. But, if I close firefox, open konqueror, and open a webpage (like google), I can then re-open firefox, and it can then find that page! It cannot find other pages until they are first opened in konqueror. 

Any ideas?

Sorry I've only just found this thread, but what you've described is an absolute classic. It's almost certainly diagnostic of the IPv6 issue. But what I don't understand is why you were able to use Linux for browsing the internet for a month, and then suddenly you couldn't. Did you change your router?

Anyway, try this in Firefox. Type 'about:config' (without the quotes) in the address bar. Now type 'ipv6' in the filter (again no quotes). You'll see a line starting 'network.dns.disableIPv6...' Double (or right) click on false to change it to true. Close firefox and reopen. If firefox now resolves addresses OK, it proves your problem is IPv6 related.

But this only fixes firefox. There will still be problems elsewhere in the system. By the way, IPv6 is not enabled in Konqueror or Windows. You can disable IPv6 system-wide - see [this thread](http://www.ubuntuforums.org/showthread.php?t=87798). (But read it all, especially the posts from Yagisan). Or you can try to find out why this problem suddenly emerged after a month. If you did change your router, look to see if there is updated firmware available. (Router firmware can be confused by IPv6 addressing.) Or ask your ISP if they've done something recently.

---

### Post by x64Jimbo on 2006-07-31
I too thought it odd that you had entries under both IPv4 and IPv6, but I didn't know if it was supposed to be that way, so I kept my mouth shut. Sounds like my instincts were right on this one.

---

### Post by bigken on 2006-07-31
You could try this ;)

[http://www.ubuntuforums.org/showthread.php?t=222047](http://www.ubuntuforums.org/showthread.php?t=222047)

oops sorry didnt see it in above post

---

### Post by msandersen on 2006-07-31
> **x64Jimbo said:**
> Blasphemy! Heretic! Burn! ;)Actually this could be a cool Linux slogan campaign like Apple's "Rip, Mix, Burn!" campaign, except targeting Windows users. A picture of Bill Gates with glowing red eyes and the slogan below, with Tux in the corner and a webaddress to some Linux campaign site, like [www.linux.org](www.linux.org) :D
Actually it should be Ballmer, but he isn't as well known, though he looks more evil! Maybe a picture of him doing his sweaty Developers! Developers! Developers! dance. 
:mrgreen:

---

### Post by code-breaker on 2006-07-31
> Anyway, try this in Firefox. Type 'about:config' (without the quotes) in the address bar. Now type 'ipv6' in the filter (again no quotes). You'll see a line starting 'network.dns.disableIPv6...' Double (or right) click on false to change it to true. Close firefox and reopen. If firefox now resolves addresses OK, it proves your problem is IPv6 related.

This worked. I'll write more tonight when I have some time to work on this. At least I have firefox working (and I can tell my wife it's 'fixed')!

---

### Post by code-breaker on 2006-08-01
I read the [thread]("http://www.ubuntuforums.org/showthread.php?t=87798") you posted, and disabled ipv6 using the example by the thread's original poster. This worked. I tried the 'bad_list' method, but this didn't work. 

I don't have time to trouble shoot why things suddenly stopped working, but I'm back up and running and that's the important thing. I'm thinking about switching isp's anyway, so it may be a mute point (since you implied that it may have been an isp issue). 

Thanks to everyone who posted with suggestions and help.

---

### Post by x64Jimbo on 2006-08-04
You're absolutely welcome! Thanks for using the forums as a resource. We're always happy to help. :)

---

### Post by code-breaker on 2006-08-11
Just a quick follow up, for completeness. 

I started having some trouble again, even with ipv6 disabled (I wasn't able to fully disable it I think). So I called my ISP, Qwest. The tech knew of an issue with the Actiontec GT701-WG dsl modem I had and linux. A friend of his uses linux, and experienced the same problem. There is a bug in the firmware that causes problems for some sites, apparently. There is a firmware upgrade that may solve the problem, but they have had problems with THAT, so they recommend against the upgrade. He said that if a modem ships with the new firmware it works fine, but trying to upgrade it yourself will cause trouble. So we agreed on a deal where they would send me a new modem (2wire), and they gave me a $50 credit to cover the price difference (monthly rental for the next year). Sweet deal, and the 2wire modem is really nice (and noticeably faster). I got the modem in today, and everything works great. 

Best of all, I can tell my wife that the whole problem was the modem's fault.

I'm back in business!

---

