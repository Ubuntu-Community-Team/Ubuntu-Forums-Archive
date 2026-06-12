---
title: "I like KDE! But.. Konqueror web page loading speed is poor, help?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by wabble on 2005-10-15
Hey!

I installed the kubuntu desktop package here the other day to try out kde vs gnome.

I like Kde. I like it so much i am stopping the use of gnome on my laptop i think.

BUT!

There is one question i have regarding to the speed Konqueror loads web pages. Is it supposed to go insanely slow? Some pages i am sure would load at over 1/4'th of the time in Firefox. So is this a known issue or do i have a bad configuration maybe? I Like konqueror also so i don't want to use firefox if i can avoid it ;)

I Think kde rocks on visual layout and system layout. It also seems snappyer and faster than gnome on my laptop. A Thinkpad X31 with a gig of ram.

Are there any recomended packages i should use that is not in the base?

---

### Post by Lord Illidan on 2005-10-15
Not sure, some people say that Konqueror is faster...

---

### Post by SGC on 2005-10-15
I read some where that adding this line to /etc/environment then restarting you computer, makes konqueror faster:
```
KDE_NO_IPV6=true
```

But even without that line konqueror is as fast as any other browser for me.

---

### Post by wabble on 2005-10-15
Well since i am going to stop using gnome i am doing a clean install after this weekend so maybe it all works out then.. i think it could have something to do with flash, but not sure.

---

### Post by Freddy on 2005-10-15
Is Konqueror slow on all the sites you visit ot just some? Firefox use a diffrent engine then Konqueror and maybe the pages you visit are slow against khtml.   /// Freddan

---

### Post by mstlyevil on 2005-10-15
Have you considerd installing Firefox? I installed it and it is working great with KDE.

---

### Post by Jengu on 2005-10-15
Maybe show some example pages? Konqueror is almost always just as fast for me or faster than firefox (I still use firefox because I'm tied to the extensions though). You can also still use firefox in KDE.

---

### Post by t2kburl on 2005-10-15
I agree. Firefox was the first package I added to my Kubuntu Breezy

---

### Post by Freddy on 2005-10-15
Firefox is a great browser but not that well intergrated into your KDE desktop under Kubuntu. Okey I know that you atleast can get the look of things right but you could make a cup of coffe and even drink it up before it boots :).   /// Freddan

---

### Post by mojorising on 2005-10-16
I also reccomend installing firefox. 

I run it on my kubuntu systems and everything runs great (plenty fast, even though my PCs are not new).

Additionally, I have experienced a fair amount of problems rendering pages in konqueror and very few, if any in firefox. Its rendering engine seems much more mature to me. Some   people surely have different experiences and opinions on that, however. 

Mike

---

### Post by wabble on 2005-10-17
Well, Konqueror was faster after a fresh install. Verry nice.

But, there was some issues with installing flash (sudo did not seem to work when i ran the script, not kdesu either). That is kind of a red light to me.

So next release i will try kde again, but i need a stable working system so going to install ubuntu with gnome again for now.

Hope the irritating bugs are out by next release. I like the KDE desktop alot better than Gnome. But i am sticking by ubuntu/kubuntu. So the choice is Ubuntu for now..

Thanks for the input guys :)

---

### Post by zenlunatic on 2005-12-22
I'm also having major speed problems with konqueror where konq is loading pages 3-7 times slower than firefox.

---

### Post by Luke on 2005-12-22
[QUOTE=zenlunatic]I'm also having major speed problems with konqueror where konq is loading pages 3-7 times slower than firefox.[/QUOTE]

me too. could it be related to the fact that this is not a "fresh install" of kubuntu? i was running gnome and then installed kde via 
$ apt-get install kubuntu-desktop

i'd like to give konqueror a shot but it's slow to the point of being completely unusable. i tried disabling ipv6 but it didn't help. firefox 1.5 runs fine (even faster after disabling ipv6 there).

---

### Post by schms on 2005-12-23
I am facing exactly the same (extremly slow) problem with Konqueror.
As it is a new, fresh installation (my first one), I can not compare the speed
with firefox or any other browser.

kind regards,

stefan

---

### Post by Rackerz on 2005-12-23
I seem to get this problem only on my laptop, no problems in Gnome but on my laptop with Konqueror it's really slow. Are you uding wireless by anychance?

---

### Post by Denta on 2006-02-05
Hmm, my fresh install of 5.10 has this problem. Sites loads fine in Konqueror besides it usually takes about 10 times longer than in Firefox. Tried disabling ipv6 with no luck.

---

### Post by elocal on 2006-02-25
I am also expericing this, but under Gentoo ~x86-64, fresh install also, kde 3.5.1.

Very weird, i am coming to think it is a kde bug.

---

### Post by elocal on 2006-02-25
Problem fixed by putting the DNS IPs that my modem was reporting directly into /etc/resolv.conf.  

Konqueror doesn't seem to like the IP of the router as a nameserver, so I just put the DNS IPs from my ISP, as reported by my modem, and it is all set.

Keep in mind that /etc/resolv.conf gets overwritten every time you run a dhcp client, so either use static IP, or prevent your dhcp client from overwriting /etc/resolv.conf (check its respective manpage).

Cheers.

---

### Post by tadashi on 2006-02-26
I also installed Firefox using the package manager and it works great.  I now only use Konqueror as a file manager now. :D

---

### Post by shaolinux on 2006-04-16
*Thanks to elocal for figuring this out. *

I had this same behavior, and it sucked. In Akgegator (rss feed viewer) the default behavior was to open links in a new tab rendered by konqueror, and it was like incredibly slow. Links opened in mozilla 5-7 times faster. The fix is to make your resolv.conf have a name server other than your router.

So if you use static ip, just add proper nameservers to your resolv.conf. If you use dhcp, edit your /etc/dhcp3/dhclient.conf. Find the line like:
# prepend domain-name-servers 127.0.0.1

and edit it to have real dns server ip.

The way I got my dns servers was to do a whois on my ip address. This gave me hostnames for the dns servers handling my netblock, then pinging those hostnames to get the ips:
whois 71.105.xxx.xxx

[...snip...]
NameServer: NS1.BELLATLANTIC.NET
NameServer: NS2.BELLATLANTIC.NET
NameServer: NS2.VERIZON.NET
NameServer: NS4.VERIZON.NET
[snip]

ping NS2.BELLATLANTIC.NET
64 bytes from ns2.bellatlantic.net (199.45.32.41): icmp_seq=1 ttl=248 time=99.2 ms

Then armed with this information, I added:
```
prepend domain-name-servers 199.45.32.41
```

to my dhcpclient.conf and now its all speedy and yummy.

---

