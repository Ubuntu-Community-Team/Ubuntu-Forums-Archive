---
title: "Netapplet and wireless browsing"
date: 2005-10-30
forum: Desktop Environments
---

### Post by awilisch on 2005-10-30
I'm curious to know how anyone using netapplet is handling their wireless networking with encrypted networks. 

I installed netapplet today. I figured netapplet would handle keeping track of my wireless networks for me, much like Windows XP's wireless networking does. So I removed my encryption key from the networking configuration for interface ATH0. When it scanned and found my wireless network (and my neighbors unencrypted network to actually), I clicked on it..it asked me for the ssid and the encryption key which it said it saved on my keyring. Sounds good so far. I had to restart networking cause it had already connected to my neighbors open wireless network. The problem is networking browsing (web, mail, etc) is VERY slow...as in, unusablly slow. I went back into networking and put the encryption key back into interface ATH0 and things went back to normal.

Basically, I'm wondering if this is a problem with the program, or if I should always register my encrypted networks in the Networking panel, and just let netapplet automatically connect me to open wireless hotspots?

Just trying to figure out the best way of making it all happen. Any thoughts would be great.

--Aric

---

### Post by raghav_p on 2005-10-30
I found GTKWifi good for wifi-networks on Hoary; haven't upgraded to breezy yet so not sure of its functionality there.

---

### Post by awilisch on 2005-10-30
I actually went and installed that gtkwifi after you mentioned it. This looks like a pretty good applet as well. Still running into some issues with it though. I removed my encryption key from the networking panel and started the gtkwifi applet. My house has two wireless ap's that are linked to create one large network. Under the gtkwifi app though it lists them both under the ssid, but to connect you have to connect to one of the individual ap's. So it kind of neuters my wireless network. Plus I can't get it to stay connected..keeps dropping me or it just won't get an address at all.

Between these two apps I think there's definatly possibilities here if I can get this connection issue resolved.

how do you connect up? Do you just leave the wireless connection in the networking panel blank, and manage all your encryption keys through the gtkwifi applet?

---

