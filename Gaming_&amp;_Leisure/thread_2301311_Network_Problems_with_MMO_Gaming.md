---
title: "Network Problems with MMO Gaming"
date: 2015-11-01
forum: Gaming &amp; Leisure
---

### Post by darrellakitchen on 2015-11-01
Before we switched over to a newer ISP, I was able to play my favorite MMO in Ubuntu. But now all I get is the game loader logging me in to the MMO's login server and not going any further from there.

I play Final Fantasy XI ... a lot. Before I switched from Windows 7 to Ubuntu. After installing Ubuntu, the only reason I would ever load Windows 7 was to play this FFXI. So about four months after this I was able to get FFXI running using WinE. It played just as good on my Ubuntu OS as well as (or even better) on the Windows OS. And across Satellite Internet, and at 2.xMbps throughput.

However, just about two weeks ago we switched over to a ground-based radio ISP which provides us now with 25~35Mbps throughout. But for some reason now I can't get the actual game to load on Ubuntu, but I can from Windows 7. 

On Ubuntu the PlayOnline Viewer loads as far as asking me to log into the viewer, and log into the game. But after it loads all the player information from the login server it just stops, hangs, and after about a minute sends back a POL-1463 error which indicates it can't connect to the game server. Yet, when I switch over to Windows 7, I can login, load, and play the game.

Both OS's have my NIC set with a static IP, and the same IP address. The `ifconfig` information from Ubuntu, and `ipconfig` from Windows are practically the same except that ifconfig displays a bit more detail than W7. The Network information from the POL Viewer in both Ubuntu and Windows are exactly the same.

The only thing I can even fathom is there is some network information I am overlooking on the Ubuntu side that Windows seems to have covered. Something about using the new ISP has confused my Ubuntu networking that doesn't confuse Windows.

I'm not opposed to reinstalling FFXI, but I'm not totally convinced this will correct the problem as it has to be network-related in Ubuntu. Does anyone have any experience with this type of problem? Any advice or suggestions on how to correct this?

---

