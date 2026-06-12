---
title: "BitTorrent is gona' kill me one of thes days"
date: 2009-01-04
forum: General Help
---

### Post by flOOi!ghenTM on 2009-01-04
Hy as you already might have guessed my main issue  is with BitTorrent download speed. Every time i reinstall my system it works fine, this meaning that the speed is above 2.0 Mbps, but after a while the speed starts fluctuating from max 900 kbps to nothing or insignificant and this is extremely annoying  since the average speed is like 30-50 kbps (and yes it usually stays at very low speeds).
 Currently I am using deluge 1.0.6. I tried every combination of settings I could come across and none work. I tried deleting and purging all the files and even that didn't work. This happens regardless of the version and after deluge starts behaving like this pretty much all clients do the same.
 I can't understand what is happening, Please help

---

### Post by adult swim on 2009-01-04
what port are you using?  does your isp throttle bit torrent traffic?  have you opened the port in your firewall?  have you opened the port in your router?  are there many seeders for the torrent you are downloading?

---

### Post by flOOi!ghenTM on 2009-01-04
Well i don't know if my ISP is throttling traffic, but i would like to know a way to find out and no i am not using a firewall and a router, and the port i am using is 50911 (yes it is open)

---

### Post by adult swim on 2009-01-04
by default ubuntu is  running a firewall.  try opening that port
```
sudo ufw enable

sudo ufw allow 50911
```

---

### Post by flOOi!ghenTM on 2009-01-04
Ok done but it seemes nothing has changed

---

### Post by pyromanic123boom on 2009-01-04
It sounds like your ISP is choking your bittorrent traffic, but the reinstalling thing doesn't make sense.

I would recommend either:  1) installing some sort of proxy for torrenting, 2) a torrent client using wine, (and if that doesn't work), 3) using a virtualbox?

I know torrents can be very frustrating on linux...I had some problems a while back. Now I use Deluge 0.5.9.3 (don't know if that's an older version or not) with successful results.

---

### Post by semi_fiction on 2009-01-04
Most BitTorrent Trackers regulate your client's bandwidth based on your download/seed ratio, meaning if you download a file then delete it right away without seeding for a while, they reduce the amount of incoming connections you can receive.
This used to happen to me, then I seeded the Fedora install DVD .iso file overnight at around 200 kb/s to put my ratio at around 3 to 1 and after that, i got full bandwidth as long as I seeded whatever I downloaded to a 1 to 1 ratio.

---

### Post by pyromanic123boom on 2009-01-04
I don't see how that would apply to mostly public trackers. 
My typical ratio for, say, a movie, is probably 0.3 or so. Now, I have an account on sportbit.org, which I am going to be banned for soon for not maintaining a solid 0.7 ratio.

---

### Post by semi_fiction on 2009-01-04
It's always happened to me and the only tracker I use is The Pirate Bay and i don't have an account there.

---

### Post by flOOi!ghenTM on 2009-01-04
> It sounds like your ISP is choking your bittorrent traffic, but the reinstalling thing doesn't make sense.

I would recommend either: 1) installing some sort of proxy for torrenting, 2) a torrent client using wine, (and if that doesn't work), 3) using a virtualbox?

I know torrents can be very frustrating on linux...I had some problems a while back. Now I use Deluge 0.5.9.3 (don't know if that's an older version or not) with successful results.

I tried using utorrent under wine but it pretty much has the same problem not as slow as deluge but still not as fast as it should go. I never thought of using a proxy for bit torrent actually i never heard that was possible.

> Most BitTorrent Trackers regulate your client's bandwidth based on your download/seed ratio, meaning if you download a file then delete it right away without seeding for a while, they reduce the amount of incoming connections you can receive.
This used to happen to me, then I seeded the Fedora install DVD .iso file overnight at around 200 kb/s to put my ratio at around 3 to 1 and after that, i got full bandwidth as long as I seeded whatever I downloaded to a 1 to 1 ratio. 

I's not a tracker issue i have pretty high share ratios on all of them meaning over 2.0 exept one wich i don't really use.

---

### Post by pyromanic123boom on 2009-01-04
That's weird

---

### Post by deltaromeo on 2009-01-04
One important thing to try is to cap your upload bandwidth in your torrent client.  Keep it at about 85% of your real upload bandwidth.

---

### Post by flOOi!ghenTM on 2009-01-04
I tried limiting the upload download speed as much as possible and it still made no difference I even changed the network settings until i got sick of it an still no joy.

---

### Post by semi_fiction on 2009-01-04
That must be frustrating. What ISP do you have? The ISPs that throttle bittorrent bandwidth that I know of are Comcast, Clearwire, SusCom, Atlantic Broadband, iProvo, Qwest, and Resnet.

Also, have you tried using uTorrent in Wine?

---

### Post by flOOi!ghenTM on 2009-01-05
Well i live in Romania and i don't think you have heard of my ISP since it's a local one and yes i tried running utorrent in wine but it's pretty much the same as any other client, meaning slow. I have heard though that tor+privoxy may be a good solution if i could just configure them right

---

### Post by mwillams73 on 2009-01-09
this is simple guys, your overexplaining something that easy to explain. Torrent downloaders use a fluctuating system, like the ebb and flow of the sea, so with this logic in mind it is normal for the bitrate to go up and down, this also means that you will get extreme highs and also extreme lows, for the most part it will even itself out over a period of time but will always fluctuate. You download rate first is determined by seeder, then leechers, finally it is determined by your upload rates, Logically speaking, its never going to stay at one bit rate for any length of time ,ever.

---

### Post by hyper_ch on 2009-01-09
> **semi_fiction said:**
> Most BitTorrent Trackers regulate your client's bandwidth based on your download/seed ratio, 
You mean to say private trackers do that ;)

However, test whether your ISP is throttling you:

[http://www.eff.org/testyourisp/switzerland](http://www.eff.org/testyourisp/switzerland)

---

### Post by adamlau on 2009-01-09
Sounds like upstream ISP throttling. Give aria2 a shot. It is the fastest BT client I have tried and I use it exclusively. You can set various options, review output logs and determine your best bet options to deal with throttling from there.

---

