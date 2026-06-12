---
title: "System monitor network history is not smooth"
date: 2008-11-13
forum: Desktop Environments
---

### Post by tweakt on 2008-11-13
The network graph displayed in the System Monitor resources tab displays the network history is showing signs of merging samples. Instead of a nice smooth graph showing the bandwidth, I get a spike every other second or so showing 2x the traffic. The numeric display below also flips between 2x and 0. 

I suspect this may be system related (possibly even kernel?) as System Monitor is only reporting the data as it sees it. I have not yet tried Ibex.

---

### Post by ohzopants on 2008-11-14
Man if I had speeds like that I wouldn't dare complain about ANYTHING (even taking into account the 2x factor, that's bitching fast)!  Is that internal LAN transfer rates?

I'm also running Hardy with the latest updates and my monitor doesn't show this behaviour.

Is it wired or wireless?  If it's wireless what's the make/model of the card and what driver are you using?

---

### Post by ohzopants on 2008-11-14
I checked the graph again and there is one "bump" that is wider than the others.  This may be related to the type of transfer occuring.  Does this behaviour occur for all types of network traffic (e.g. http, ftp, bittorrent, etc.)?

---

### Post by tweakt on 2008-11-14
> **ohzopants said:**
> Man if I had speeds like that I wouldn't dare complain about ANYTHING (even taking into account the 2x factor, that's bitching fast)!  Is that internal LAN transfer rates?

I'm also running Hardy with the latest updates and my monitor doesn't show this behaviour.

Is it wired or wireless?  If it's wireless what's the make/model of the card and what driver are you using?

This is using wireless... an Atheros AR5212
(Lenovo Thinkpad T61)

PS: Internet speeds... FiOS @ 20Mbit ;-)

---

### Post by tweakt on 2008-11-14
> **ohzopants said:**
> I checked the graph again and there is one "bump" that is wider than the others.  This may be related to the type of transfer occuring.  Does this behaviour occur for all types of network traffic (e.g. http, ftp, bittorrent, etc.)?

The graph is definately not representative of the traffic. It should be one continuous smooth transfer. It looks the same if I download a large file over HTTP. I get alternating spikes and gaps just like that, a tcpdump trace shows a continuous stream of traffic.

---

### Post by ohzopants on 2008-11-18
That's pretty weird and I'm all out of ideas, sorry.

The only other thing I can think of (and, yes, I'm grasping at straws here) is that the driver you are using might be reporting weird data to whatever utility is used to fetch the data for sysmon.

ndiswrapper, madwifi, other?

---

