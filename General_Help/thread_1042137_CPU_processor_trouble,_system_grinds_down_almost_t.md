---
title: "CPU processor trouble, system grinds down almost to a halt"
date: 2009-01-17
forum: General Help
---

### Post by cannon_dt on 2009-01-17
Hi All.
I got a problem, I am a newbie to Ubuntu which is running on my somewhat archaic laptop - a HP Pavilion with 512 MB RAM armed with a Intel Pentium M processor.
Now I am an active torrent user and I run 4-5 concurrent downloads via BitTornado (my favourite torrent client). When I do this I run into the following problems:
1. The responsiveness of the system goes down and the system seems crippled.
2. When I open VLC player to play an AVI, it stutters and stammers and goes black most of the time (when no torrents are running the same video plays swell).

So I did a TOP and I see that the torrents take around 6-7% of processor time. So that accounts for say 35%, firefox takes around 10-15%. Now the system monitor still says 90-100 % in use and I see Xorg taking almost 40%. This seems to be why my system is going so slow. Can I do anything about this? Also I see so many processes running, how do I figure out and configure the system so that the unnecessary ones do not start at all.

Please help, I am sure I dont need a RAM upgrade, somehow I think this problem can be solved by configuration or some sort o tweaking.
A call to all ye experts for help!

Cannon

---

### Post by walter_j on 2009-01-17
Firefox 3 has some issues where it almost locks up the system at times. Try another browser such as Konquerer or Opera.

---

### Post by DeMus on 2009-01-17
> **walter_j said:**
> Firefox 3 has some issues where it almost locks up the system at times. Try another browser such as Konquerer or Opera.

Or shut down Firefox and see what happens then. Just to make it is caused by Firefox, or not.
Xorg using 40% of your processor seems to me quite a lot. Here in my computer it's using 0% and just a little ram memory.
It looks to me you have to find the solution in Xorg, but I am not the one who can help you with that. Sorry

---

### Post by cannon_dt on 2009-01-18
DeMus,
Even I am convinced the problem lies with Xorg. I googled but not to much avail. Firefox is bad but it is not as bad as what Xorg is doing to my processor.
Can some experts please help?

Cannon

---

### Post by DeMus on 2009-01-18
> **cannon_dt said:**
> DeMus,
Even I am convinced the problem lies with Xorg. I googled but not to much avail. Firefox is bad but it is not as bad as what Xorg is doing to my processor.
Can some experts please help?

Cannon

One of the Synaptic packages is called EnvyNG. It's a program to install the latest nVidia and Ati drivers. If you did not yet install it, do it now:
System | Administration | Synaptic Package manager
Use search and type envyng
When found, click the button at the start of the line and choose install. Maybe it will also install some other programs it depends on, that's fine.
After installation you can find the launcher in Applications | System tools.
Start it, choose nVidia and choose to install the latest driver automatically.
After a while the driver is installed and you need to reboot so the new driver is used.
Check again to see if Xorg is still using so much of your processor.
Success.

---

### Post by cannon_dt on 2009-01-18
But I dont use nvidia graphics card, I have a intel graphics chipset. Should I still do this?

Cannon

---

### Post by cannon_dt on 2009-01-18
Also, in ubuntu forums itself I found so many posts complaining about xorg. No one seems to have found a solution yet. I though Linux is configurable and we should not be facing such problems. I am a little disappointed.
Also how do I figure out what are the necessary vs the unnecessary processes running. Sps -ef is quite confusing to a newbie like me. Any help there?

Cannon

---

