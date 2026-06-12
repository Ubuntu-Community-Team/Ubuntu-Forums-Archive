---
title: "vnstat shows that Ubuntu is constantly downloading something?"
date: 2009-04-19
forum: General Help
---

### Post by cinematography on 2009-04-19
I installed vnstat to keep track of my Internet usage. In live mode, vnstat shows that I'm downloading something between 3kb/s - 6kb/s even when I'm not downloading anything; the only programs that I have open right now are Pidgin and Firefox.

Is Ubuntu always downloading something? If so, is there a way to stop this?

Your help would be appreciated.

---

### Post by thewolfman on 2009-04-19
> **cinematography said:**
> I installed vnstat to keep track of my Internet usage. In live mode, vnstat shows that I'm downloading something between 3kb/s - 6kb/s even when I'm not downloading anything; the only programs that I have open right now are Pidgin and Firefox.

Is Ubuntu always downloading something? If so, is there a way to stop this?

Your help would be appreciated.

Hi, I would think that having 2 Internet related programs running would be enough to keep your new prog active as both rely on a constant connection to the Internet it would be fair to assume that they are constantly in need of feeding!!!!????.

---

### Post by Yashiro on 2009-04-19
Try
*lsof -i -P -n*
or
*sudo netstat -tuaevpn*
from a terminal.

It might show what's going on.

---

### Post by tommynz1975 on 2009-04-19
I have often wondered this also...  i will download say a linux iso 600 mb
And upload to who knows where 32mb of data to some such place... I would never know what was sent.

I think what cinematography may like is a program that details where everythng is downloaded from / uploaded to and where it got downloaded to...

obviously some of the traffic is from the ISP confirming the connection.

as said before pointing one in the right direction is appreciated.

---

### Post by Jimmynemo2 on 2009-04-19
Just did sudo netstat -tuaevpn on my machine- neat to see- thanks for the great CLI info there, great to know about.

---

### Post by cinematography on 2009-04-19
Thank you for the replies.

> **thewolfman said:**
> Hi, I would think that having 2 Internet related programs running would be enough to keep your new prog active as both rely on a constant connection to the Internet it would be fair to assume that they are constantly in need of feeding!!!!????.
lol. But even when I close them vnstat still shows downloading.

> **Yashiro said:**
> Try
*lsof -i -P -n*
Typing this showed 2 pidgin results.

> *sudo netstat -tuaevpn*
Typing this showed "named", cupsd, pidgin, avahi-daemon, and dhclient.

> **tommynz1975 said:**
> I think what cinematography may like is a program that details where everythng is downloaded from / uploaded to and where it got downloaded to...
Exactly. I don't like mysterious file transfers. I want to know exactly what I'm sending, and what is being sent to me. 

And I know 4kb/s doesn't seem like a lot, but it does add up quickly. It's about 336megs per day. :o

---

### Post by Jimmynemo2 on 2009-04-19
a fast google search of each of these show them as programs that _use the internet/network_ constantly, and that if running, you would expect to see them transferring data. 

Not to downplay your worries, as its good to keep control of your system, but now that you know whats sending data, and knowing it comes from programs you choose to run/need, being worried still is akin to being afraid your car is using gas when idling (as well as having the same solution- turn if off for 100% no data transfer over the network.)

FYI, my system gets constant little net activity as the router pings it and I ping back every so often- guess it just wants to make sure I'm there, but that doesnt really worry me, it's just part of having a computer on a network. Pidgin likewise on my system periodically pings out and in to make sure Im there and what my status might be. It's just how the program works.

---

### Post by Brucevdk on 2009-04-19
> **cinematography said:**
> Exactly. I don't like mysterious file transfers. I want to know exactly what I'm sending, and what is being sent to me. 

If you want to see what kind of traffic is going over the wire you could install Wireshark.

---

### Post by Yashiro on 2009-04-19
If you close everything down and those two commands show nothing out of the ordinary then vnstat is possibly monitoring your loopback device. Although this is doubtful.

Just close apps and daemons that show up in the list from before one by one.
You'll find which app it is.

If you've installed any browser plugins that prefetch data to 'speed up browsing' this can also be a source of data leakage.

---

### Post by cinematography on 2009-04-19
I guess vnstat was just monitoring my network pinking. :)

Thank you very much for the help, folks.

---

### Post by lavinog on 2009-04-19
iftop is also a good program to see what kind of network activity is going on.

---

