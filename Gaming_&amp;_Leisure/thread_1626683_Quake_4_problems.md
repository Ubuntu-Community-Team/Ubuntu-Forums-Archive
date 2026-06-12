---
title: "Quake 4 problems"
date: 2010-11-20
forum: Gaming &amp; Leisure
---

### Post by confessionsofapwner on 2010-11-20
Hey all.

I tried to install an old quake game on my computer, quake4 to be exact, and I'm getting the following error; 
```
 idRenderSystem::Shutdown()
Sys_Error: Texture compression unavailable

```
My box is running ubuntu 10.10, with all updates and everything. If anyone could help to show me how to fix this, I would greatly appreciate it.

---

### Post by Soulcage on 2010-11-21
Did you install using the installer from [http://zerowing.idsoftware.com/linux/quake4/]("http://zerowing.idsoftware.com/linux/quake4/")?
Did you remember to copy all the .pk4 files from the cds/dvd and set the permissions on the ones you copied?

---

### Post by confessionsofapwner on 2010-11-22
> **Soulcage said:**
> Did you install using the installer from [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)?
Did you remember to copy all the .pk4 files from the cds/dvd and set the permissions on the ones you copied?
Yes, I've done all of that.  Except the installer was from here:
[ftp://ftp.idsoftware.com/idstuff/quake4/linux/](ftp://ftp.idsoftware.com/idstuff/quake4/linux/)

---

### Post by Soulcage on 2010-11-23
Make sure you have read permission set for your user on all the files inside /quake4/q4base it was the problem I had.
The error message might of been different though.

---

### Post by rajeev1204 on 2010-11-23
> **confessionsofapwner said:**
> Hey all.

I tried to install an old quake game on my computer, quake4 to be exact, and I'm getting the following error; 
```
 idRenderSystem::Shutdown()
Sys_Error: Texture compression unavailable

```My box is running ubuntu 10.10, with all updates and everything. If anyone could help to show me how to fix this, I would greatly appreciate it.

This is a problem of incompatible hardware or software drivers.


Do you have an ATI card ? Which one.

---

### Post by confessionsofapwner on 2010-11-26
ATI radeon 3100 HD

---

### Post by rajeev1204 on 2010-11-27
> **confessionsofapwner said:**
> ATI radeon 3100 HD


Please install the drivers for this card from system > administration > hardware drivers .Right now you are using the open source drivers which will not run quake 4 due to a key component missing in the driver.

---

### Post by confessionsofapwner on 2010-12-04
Sorry for loooong reply. 
Thank you so much! It worked

---

### Post by rajeev1204 on 2010-12-04
> **confessionsofapwner said:**
> Sorry for loooong reply. 
Thank you so much! It worked

Good to know.
Try multiplayer , there are some servers active ,i have my own server too:

178.63.185.171:28006 . Its called 'home of the pronoobs'. I also have a demo server running since someone told me there are people who play demo too .

Then there is one in uk called muliplay.co.uk. I play there a lot .

My nick is InDuS.

---

### Post by kaldor on 2010-12-05
> **rajeev1204 said:**
> Good to know.
Try multiplayer , there are some servers active ,i have my own server too:

178.63.185.171:28006 . Its called 'home of the pronoobs'. I also have a demo server running since someone told me there are people who play demo too .

Then there is one in uk called muliplay.co.uk. I play there a lot .

My nick is InDuS.

Reinstalling this right now. Last time I played this summer, nobody (only 1 server without bots) was on. Seems everyone moved on to Quake Live :(

---

### Post by rajeev1204 on 2010-12-05
> **kaldor said:**
> Reinstalling this right now. Last time I played this summer, nobody (only 1 server without bots) was on. Seems everyone moved on to Quake Live :(


Well, many have moved to quake live, but many have stuck to quake 4.I have always loved the style of this better .But there are like 500 active q3/ qlive players compared to 50 in q4 . Basically around 3 or 4 active servers only .But we have been playing there for many years now.Its great fun.

Quake live is frankly a 10 year old game reworked with a bit more eye candy and plays a bit like quake 3. And i prefer q4 gameplay more.And q4 has much better sounds than q3.

I also love the graphics on quake 4,its still good after so many years.


P.S. My server is down right now . :P Have to restart but forgot my password .

---

### Post by kaldor on 2010-12-05
> **rajeev1204 said:**
> Quake live is frankly a 10 year old game reworked with a bit more eye candy and plays a bit like quake 3. And i prefer q4 gameplay more.And q4 has much better sounds than q3.

I also love the graphics on quake 4,its still good after so many years.

Couldn't agree more... I'll hop on your server sometime if there are people :)

I've barely played at all, but when I do play I love it.

---

