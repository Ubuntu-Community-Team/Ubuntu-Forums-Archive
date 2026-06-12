---
title: "What is Stacheldracht?"
date: 2006-02-03
forum: Desktop Environments
---

### Post by Luke771 on 2006-02-03
...And what does it do?
I saw an entry in Firestarter's active connections list showing an outbound connection on port 65000 reading "Stacheldracht" in the "Service" column.
I blocked port 65000 and found that this  "stacheldracht" thing keeps on trying to connect all the time.
The internet applications that I run most oftes, besides web browsers, are Tor, i2p and Azureus which is connected to the tracker throuch a Tor hidden service (no proxying on peers communication).
For that little I understand, it looks like Firestarter tries to guess service names comparing port numbers to a list, and that's why I suspect that it may be something other than Stacheldracht trying to reach the internet through port 65000, probably Azureus because it tries quite often to connect ho a site hosted in Sweden, and one my favorite .torrent sites is also in Sweden (but the pages are available in a number of languages) but I'm not sure, it could be something else after all.
So what do you guys think?
Is it Azureus or something else?
If it is, why on port 65000? I haven't configured anything like that
And if is not Azureus, then what is it?
Should I allow outbound connections on port 65000
And what is Stacheldracht anyway?

---

### Post by Joeb on 2006-02-03
If I'm not mistaken, Stacheldracht (German for barbed-wire) is used to launch a  DDos attack, at least according to [http://www.securitydocs.com/library/2553](http://www.securitydocs.com/library/2553) (half way down the page).  If that is correct, and you aren't using your Ubuntu box as a gateway for some windows computers, then it sounds like you have a worm on your box (if you are using it as a gateway, then the windows computers probably do).

If you search on Stacheldracht in google, you'll get more info.  Or better yet, search on Stacheldracht + Linux.

---

### Post by heldal on 2006-02-03
[QUOTE=Luke771]...And what does it do?

Stacheldracht (german for barbed-wire) is a DDoS-tool first spotted in '99. Haven't heard much about it in recent years. Maybe this is something new, or that what you see is something else, just that your firewall happens to associate port 65000 with stacheldracht.

First find out which process the traffic comes from. If it's using 65000/tcp, try "lsof -i tcp:65000" (or "udp"). Then "lsof -p <suspect-pid>" may give more clues as to what that process is up to.

//per

---

### Post by Luke771 on 2006-02-03
Thanks for the answers,
No, I dont use my box as a gateway, I *do* run Windows sometimes, most for playing games, but on the same box using dual boot. guess I have to scan my drives with some kind of antivirus/antiworms/antiwhatever (I haven't installed anything like that so far. If nothing is found after the scan I guess I can assume that it's something else (and then I have to find out what).
Can someone name a good program to run this kind of scans, that is fairly easy to install and update?

---

### Post by Luke771 on 2006-02-03
hm... I logged out and in again and I'm running all the possible internet connecting programs except Azureus and no stachedraht so far... I guess it must be azureus then

---

### Post by jamespi on 2006-03-07
i did that command posted above becuase i thought i had stacheldraht too, but it turns out it was bitornado.

so port 65000 must be to do with the bittorrent protocol

my faith in ubuntu security was quite shaken for a minute there, too!

---

