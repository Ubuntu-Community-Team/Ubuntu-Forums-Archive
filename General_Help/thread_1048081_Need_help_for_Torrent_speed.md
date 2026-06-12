---
title: "Need help for Torrent speed"
date: 2009-01-23
forum: General Help
---

### Post by halovivek on 2009-01-23
Hi all,
I do have internet connection speed of 59 M bps. i will get 10MB per second speed if i use torrent or ordinary download in windows. But i could not get the same speed at least 1MB in Ubuntu. Could you give us the detail or solution how to do that one. But one thing i noticed. if i connect to server for ubuntu updates. It will download at 8MB per second. But torrent does is very bad.
any idea to solve this issue?

---

### Post by halovivek on 2009-01-23
Sorry i forget to tell.
I tried Transmission bit and bit torrent. Both gives same result.

---

### Post by jerome1232 on 2009-01-23
If you have a 59 mbps internet connection the maximum speed you could ever download at would be about 7.375 MB/sec, in reality less than that.

Are you sure your not connected wirelessly to your router at 59 mbps and that your internet connection speed is something else? (like 12 mbps?)

At any rate the main cause of slowness in torrents is simply the torrent doesn't have many seeders compared to leechers and/or many seeders with a fast upload speed. Just try to find a torrent with a better seeder to leecher ratio.

Another reason is maybe you have a host based firewall setup that blocks incoming connections, in that case you need to unblock whatever ports your specific torrent client needs open.

Yet another reason would be your router isn't uPnP enabled or has uPnP turned off and isn't automatically forwarding the ports your torrent client needs, you would need to browse to the web gui of your router and either turn on uPnP or forward the necessary ports to your computer.

---

### Post by bgerlich on 2009-01-23
increase the number of connections (peers) per torrent and global number of peers.

Remember that Transmission saves torrent settings per torrent, so remove and add againn torrents you were already downloading

---

### Post by halovivek on 2009-01-23
1. I do have internet connection speed of 59Mbps and i can get max at 10Mbps. 
2. I have tested the torrent in both windows and Ubuntu with the latest uploaded torrent which is having more seeds.
3. I could find the difference very well.
4. I use utorrent in windows and it will keeps adding the seeds and more requests but in ubuntu. nothing more. Just even it cant touch 1Mbps speed. and connecting to seed is also limited where as windows i could connect to 10 max full seeds. here not more than 1 0r 2.

---

### Post by neur0 on 2009-01-23
I never had problems with Deluge torrent client. Have you tried it?

---

### Post by halovivek on 2009-01-23
> **neur0 said:**
> I never had problems with Deluge torrent client. Have you tried it?

Ok i will try this one also.

---

### Post by hyper_ch on 2009-01-23
if you have 10m bits per second then max speed is 1.125m Bytes per second... so your previous torrent client might have measured in bits and the new one in bytes.

---

### Post by scouser73 on 2009-01-23
I'd also recommend Deluge as a Bittorrent client.

---

### Post by hyper_ch on 2009-01-23
rtorrent, everything else is just too much bloated :)

---

### Post by marcgh on 2009-01-23
I am using Vuze ( azureus ) and I cant't find much speed difference between th XP and Ubuntu version.
You can install it easily with ADD/REMOVE PROGRAMS.

---

### Post by halovivek on 2009-01-30
> **hyper_ch said:**
> if you have 10m bits per second then max speed is 1.125m Bytes per second... so your previous torrent client might have measured in bits and the new one in bytes.

my internet connection is 59MBS but i get the download speed is 10 MB/s in windows OS.

---

### Post by jerome1232 on 2009-01-30
What you are saying is impossible.

Network speeds are measured in bits. Generally when you download a file the speed shown is measured in bytes.

There are 8 bits in one byte, so to convert bits to bytes you simple divide by 8.

59 megabits per second divided by 8 equals 7.375 megabytes per second. This is well below 10 megabytes per second. 

So you are saying that you download files at a speed faster than what your connection is capable of.

If you are saying you have a 59 megabyte per second connection than that is about a 472 megabits per second connection. This tops out standard lan equipment. I don't think even fiber goes that high for internet connections.

At any rate, are you connecting through a router? Does it have UPnP enabled? If not do you have the appropriate ports forwarded to your computer?

---

### Post by HammerOfDoubt on 2009-01-30
Hello all.
I'm having this problem too.
Or I was having it, and now have a modifed version of the same problem.
Regular downloads were good, but once I loaded a torrent, it was barely above 12kbps.
Then in a different thread (I can;t remember which one) I saw this recommendation to someone with a slow connection issue:

> try setting the speed manualy: sudo iwconfig wlan0 rate 54M or sudo iwconfig wlan0 rate 24M

I ran the first code, and my downloads are much much faster now.

But my upload speeds are still miserably low, often just sticking at 0, sometimes hovering above 8kbps.

As a result, I've become a horrible seeder.

---

### Post by bgerlich on 2009-01-31
> **HammerOfDoubt said:**
> But my upload speeds are still miserably low, often just sticking at 0, sometimes hovering above 8kbps.

As a result, I've become a horrible seeder.

Now all you need to do is turn on Upnp support in your torrent program. This will forward appropriate ports to your computer increasing upload speeds significantly.

---

### Post by HammerOfDoubt on 2009-01-31
Did that, and also using Deluge instead of the default torrent program. Works fine now.

---

