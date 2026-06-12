---
title: "Torrent With Transmission Help (VERY SLOW)"
date: 2009-04-20
forum: General Help
---

### Post by Unix-Man on 2009-04-20
Hello, I am currently Using the Application Transmission to download a torrent (No Need To Say What Im Downloading) And NO it's not Porn. 

Anyway it is VERY Slow, Maybe this is Because i only have 1 peer.
 
I don't know very much about how torrenting works but i remember from my windows days i would get a Minimum of 60.Kbps With 1 peer Using Vuze. 

Im Getting Anywhere in the range of 1.0Kbps to 3.6Kbps. 

And im downloading a 1.6GB File, This will take FOREVER. and i don't want to wait a week. SO Any tips on how to speed it up? I Already set my Download Speed to Unlimited and Upload speed to Limit 5Kbps. And it's still only getting 1 or 2 Kb per second 

Thanks Unix-man

---

### Post by Svensk023 on 2009-04-20
I never ever got good download speeds with transmission

Try out Deluge or KTorrent.

I personally use deluge and it works well. you can get it from their website or get it from Add/Remove app's function. The website will have a much more updated version of Deluge however

Plus, a single peer will yield very poor results, but more seeders may start uploading later.

---

### Post by Unix-Man on 2009-04-20
Well Thanks for the Advice

But the problem with changing torrent clients is im already 50% done with Transmission and if i get a new client and get better speeds it will still take longer. So im just looking for a way to speed up Transmission.

Another Thing is. i LOVE how Slim Transmission is. I Used to use Vuse in my winBLOWS days and it would suck up like a gig of Virtual Memory. and it was SLOW as hell so on a long torrent i couldn't use my computer. 

are the Apps you suggested Slim like Transmission?

---

### Post by tiresia on 2009-04-20
Before trying another bittorrent-app, you may want to download another file, just to see if the slowness depends on trasmission or on the lack of seeds (be sure to find a torrent with many seeds)

---

### Post by Unix-Man on 2009-04-20
Well i have Comcast business class so i get 2 MBps (NOTE THE CAP "B" means BYTES not Bits so i get 2 megs a second on a speed test 
so im sure it's not a result of having slow internet

---

### Post by lloyd_b on 2009-04-20
> **Unix-Man said:**
> Well i have Comcast business class so i get 2 MBps (NOTE THE CAP "B" means BYTES not Bits so i get 2 megs a second on a speed test 
so im sure it's not a result of having slow internet

Are you aware that Comcast has a history of "throttling" traffic on bittorrent ports?

You can try configuring your BT client to use different ports, and see if that makes a difference.

On a torrent with only 1 connection, I'd suspect it being a slow/overloaded node that you're downloading from being the culprit.

Lloyd B.

---

### Post by mirhciulica on 2009-04-20
if you still want to give a chance to transmission try to increase the number of peers from edit -> preferences -> peers and change maximum overall peers to something like 1000 and maximum peers per torrent to a higher value like 200 and your speed will increase a lot!

---

### Post by Unix-Man on 2009-04-20
> **lloyd_b said:**
> Are you aware that Comcast has a history of "throttling" traffic on bittorrent ports?

You can try configuring your BT client to use different ports, and see if that makes a difference.

On a torrent with only 1 connection, I'd suspect it being a slow/overloaded node that you're downloading from being the culprit.

Lloyd B.

Alright sounds like a good idea but i have a question. 

I Know how to change the port inside the BT preferences BUT for example. Lets say i set it to 3232, Should i go to my router firmware and open port 3232?

---

### Post by tiresia on 2009-04-20
> **Unix-Man said:**
> I Know how to change the port inside the BT preferences BUT for example. Lets say i set it to 3232, Should i go to my router firmware and open port 3232?
Yes! But Transmission supports UPnP to open ports. If your router does support also it, and this option is active, you don't need. 
Transmission will tell you if the port you choose is open ( Preferences > Network)

---

### Post by Penguin Guy on 2009-04-26
You can easily continue downloading your existing torrent with another client. You don't loose all your data when you switch.

**How-to:**
Find the torrent file and put it on your desktop.
Find the data file and put it on your desktop.
Drag the torrent file onto your prefered application (or browse for file, depending on torrent program).
Done!

---

