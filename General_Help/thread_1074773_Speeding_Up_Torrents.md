---
title: "Speeding Up Torrents"
date: 2009-02-19
forum: General Help
---

### Post by u'b'u'n't'u on 2009-02-19
Hi, 

I am only getting around 25 kbps with 20 connected peers:( in transmission bittorrent client. How might I increase this?







-u'b'u'n't'u

---

### Post by Aenima99x on 2009-02-19
I used to see really slow times with Transmission, try out the Deluge torrent client. It sped up my times quite a bit.

---

### Post by anlag on 2009-02-19
Three ideas:

-if you don't have a lot of UPSTREAM bandwidth, your downloads will usually be pretty slow too, since the system generally gives the most download to the ones that upload the most too
-router/NAT/ISP/etc problems? 
-the other peers might have slow connections, or be far away, or just not have very much of the torrent to share with you

---

### Post by Mercury_Alpha on 2009-02-19
Also, if the torrent was published recently, or you're not connected to any seeders, then things may take a while.

---

### Post by cb951303 on 2009-02-19
if your router has upnp support make sure it's enabled. if not you have to do port forwarding to your local ip. also note that transmission doesn't support DHT which, in most cases, speed up downloads a lot

---

### Post by MedianMajik on 2009-02-19
> **anlag said:**
> Three ideas:

-if you don't have a lot of UPSTREAM bandwidth, your downloads will usually be pretty slow too, since the system generally gives the most download to the ones that upload the most too
-router/NAT/ISP/etc problems? 
-the other peers might have slow connections, or be far away, or just not have very much of the torrent to share with you

I would ignore the Deluge comment (no offense to it as I use it), but it sounds like your settings are the problem.  Check out your preferences and see if they're setup correctly.  Is the port you're torrenting from [open]("http://portforward.com/"), because if it isn't that is likely the problem.  What are your settings for upload speed per torrent, bandwidth max, number of seeders, etc.  As stated above what is your ratio of download to upload?  Depending on the tracker you're downloading from you might be getting throttled for not uploading enough.  You could also be throttled by your ISP; Have you forced encryption and denied legacy connections (this is a fairly recent addition to Transmission).  Do you have a firewall that might be limiting torrents?

Edit: Settings like DHT, etc depends on your tracker.  Responses seem to assume you're on a public tracker, but if you're not consult the official rules, faq.

---

### Post by mb_webguy on 2009-02-19
Also, you mention the number of peers, but torrent speeds are really more about the seed/leech ratio.  The higher this ratio, the faster the download will tend to be, since the leeches are competing for the seeders' bandwidth.  It's generally better to select a torrent with fewer seeds but a higher seed/leech ratio than one with a larger number of seeds.

---

### Post by cb951303 on 2009-02-20
> **mb_webguy said:**
> It's generally better to select a torrent with fewer seeds but a higher seed/leech ratio than one with a larger number of seeds.

+1. Torrent client connects to a limited number of users anyway. Lots-of-seeds doesn't mean much compared to high ratio:popcorn:

---

### Post by helai on 2009-02-20
> **cb951303 said:**
> if your router has upnp support make sure it's enabled. if not you have to do port forwarding to your local ip. also note that transmission doesn't support DHT which, in most cases, speed up downloads a lot

Yes,I agree with three points

1.upnp enabled
2.port forwarding if router used
3.DHT supported by torrent client,just like vuze ,it should install the MainDHT plug.

---

### Post by joey-elijah on 2009-02-20
> **Aenima99x said:**
> I used to see really slow times with Transmission, try out the Deluge torrent client. It sped up my times quite a bit.

  agree

---

### Post by u'b'u'n't'u on 2009-02-20
im a noob and i dont understand the port thing how do i find on thats open theyre all closed!

---

### Post by Arup on 2009-02-20
Make sure your incoming ports are open in our firewall or router. Also check how many seeds are there. Transmission is a very good lightweight client, I use it on daily basis and depending on the seeds, I get full speed if there are multiple seeds, absolutely no issues.

---

