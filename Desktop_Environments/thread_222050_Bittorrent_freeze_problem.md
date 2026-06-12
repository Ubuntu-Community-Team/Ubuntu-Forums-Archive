---
title: "Bittorrent freeze problem"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Metacarpal on 2006-07-24
Hi everybody.  I've been trying to sort out a problem on my system where running any bittorrent client (regular, BitTornado, Azureus, etc) causes the system to freeze.  I can still move the mouse, but nothing is responding.  If I restart my X session with Ctrl-Alt-Bkspce, I can log back in and manually kill bittorrent through System Monitor, which restores functionality.

I've noticed that this only happens when downloading torrents on a wireless connection while also using other internet apps (Firefox, Synaptic, anything that accesses the connection).  If I just run the torrent client and nothing else, it works like a dream.  So the issue appears tied to having a torrent client accessing the wireless network at the same time as another app.

I've searched this issue on the forums and haven't found a solution.  Most of the posts on this are older and end with the issue up in the air, or else there's a lot of talk of ATI video drivers, which I don't have.

Has a solution to this problem been found, to anyone's knowledge?

---

### Post by xinhoj on 2006-07-30
I have had a similar problem with BitTorrent, but with some even crazier side effects...

I use BitTornado, which has never caused me any trouble until recently. I'll be running a download and doing other things (or go to bed) and suddenly my computer randomly shuts off (no shutdown sequence, just *boom* off. Have woken up to see a dead screen almost every day now for the past couple weeks). I have to turn off the switch on my power supply and leave it for a couple minutes, then turn it back on so it'll start up again. HOWEVER, when it boots back up again, my screen resolution is locked at 640x480, and I have to /etc/init.d/gdm stop/start about 4 or 5 times before it'll go back to normal.

A friend of mine advised that, because the house is so dusty, the innards of my computer were probably covered in it, so I went to the store and got some canned air. When I sprayed into my power supply, a virtual Dust Bowl came billowing out. Everything worked fine for a while, but now it's been shutting down with increasing frequency. Yesterday was the first time it restarted my computer instead of a cold shutdown. It only seems to perform these shenanigans when I'm running BitTornado.

Please help, if you can!

---

### Post by infogorf on 2006-12-04
Having the exact same problem. Any news on how to solve it?

---

### Post by Tectuktitlay on 2006-12-16
Same here,
with 6.06 LTS and wireless lan RTL8180.
I noticed that this problem is all over the forum, with no conclusive solution.

Greetz,

Maarten

---

### Post by Winzeep on 2007-02-04
I had exactly the same problem with a wireless PCMCIA card with the RTL8180 chipset. I had everything working but the bittorrent clients which made my ubuntu freeze.

After days and nights looking for a solution, I discovered that my card was not handled well by the rt818x driver, so I installed the official REALTEK windows XP drivers from the realtek website : 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3)

I used ndiswrapper with the INF file  instead of the autoloaded drivers and it works fine now !

I hope it will help you...


- Winzeep -

---

### Post by closetpirate on 2007-02-05
I once had the same problem and began using Ktorrent instead. It not only fixed the problem but appears to be better software for faster downloads

Hope that helps

---

### Post by 21jeremy21 on 2008-02-28
I have you all beat! When i' running a torrent program, ANY torrent program (even my beloved ktorrent) my computer freezes in a matter of minutes, giving me a blank screen with just my Num Lock and Caps Lock lights flashing. What in sam hell is the meaning of this malarky? It gets me all fired up, I tell you what. My computer doesn't shut down either when this happens so I wake up in the morning to my laptops fan just givin'er full bore.

:confused:

any ideas?

---

### Post by Hr7376 on 2008-03-08
well you mentioned you have a laptop and so do i , i also have the same problem.  My laptop is a acer aspire 3050.

---

