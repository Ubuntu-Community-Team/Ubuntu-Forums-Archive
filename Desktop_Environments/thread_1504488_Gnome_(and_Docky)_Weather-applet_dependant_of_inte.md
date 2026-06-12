---
title: "Gnome (and Docky) Weather-applet dependant of internet connection ?"
date: 2010-06-08
forum: Desktop Environments
---

### Post by alkalyzer on 2010-06-08
Hello Ubuntu users,

I had experienced a annoying feature relative to both the Gnome Weather-applet (the one linked to the clock) and the weather-desklet from Docky :

With the same laptop (working under Lucid Lynx), they work perfectly fine when I am using them from work but never stop to update (in the case of the Docky desklet) or didn't show up (for the gnome weather-applet) when I am using them from home. In both case, I am using a WiFi connection and no proxy.

Has everyone else experimented such a problem ?
If so, which parameters should I adjust to solve this trouble?

Thanks for your answers

PS : Wherever the place I am, I can access with a web-browser to the websites providing the weather forecast (iGoogle, weather.com and weather.underground).

---

### Post by alkalyzer on 2010-06-09
I managed to solve this trouble, finally :D.

The main differences between my two internet connections were the **DNS** : in Network-Manager, I precised addresses of a DNS server for the connection which was working with the weather-applet while none for the troublesome one. In the latter case, I imagine I inherited random DNS server addresses through my ISP every time I got connected.

To solve the problem : I added in Network-Manager, under the "*IPv4 Settings*" tab, in the "*DNS servers*" field, two IP addresses which point towards the Google Public DNS (8.8.8.8,8.8.8.4).

Now, both the gnome-panel weather-applet, the applet Weather Report and the Docky weather-applet are working as they should be.

I hope this solution would be useful to someone else.

---

### Post by sterby on 2010-06-23
Tried this method for my computer, sadly my whole internet connection drops after applying the DNS addresses in the ipv4 tab. DHCP server is enabled on my router and it's a wired connection. I don't really know what could be the problem, the AWN weather docklet works flawlessly. I wanted to give docky a chance but this bug hogs up most of the system resources, it's like I'm using my old Windows install again.

---

