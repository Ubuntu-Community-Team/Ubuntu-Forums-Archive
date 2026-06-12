---
title: "Ubuntu 8.04 Can't connect to internet"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wh00mp on 2008-04-25
I have a Dell Inspiron 1501 and Ubuntu 8.04 can see my network card, so it seas but it does not want to connect to my router and i have no internec connection. I can't do nothing without internet on it. Help please.

---

### Post by wh00mp on 2008-04-25
Forget about it. After I put in Software Source de CD of Ubuntu it took the drivers for the network card and now internet works.

---

### Post by skipx on 2008-05-02
Ok, downloading now with my other machine. But it might be VERY handy if there is a notice about this, to download the Ubuntu CD BEFORE you decide to upgrade (via update programm) and after restart loose your internet connection.
In my case both wireless and ethernetcard are not recognized, and i guess will be after inserting that disc.

EDIT:
WHAT A MESS, burned ubuntu dvd, downloaded with other machine, is not recognized by system. Also my optical drive drivers are trashed? What's happening???

---

### Post by Nico0020 on 2008-05-02
I had some major problems with Hardy on my E1505.  I can not connect to the internet via wired or wireless.  I finally gave up and put Gutsy back on my main partition and have made an extra partition to work on Hardy with.  It is really strange though.  I can connect while on campus, or at a friends house.  But when I try to connect at home, it never can.  I have a 2wire DSL modem/router, and it goes nuts when Hardy trys to connect to it.  It continues to shut down and reboot for as long as hardy is trying to connect.  

So for now I am staying away from hardy.

---

### Post by alejobar on 2008-05-02
> **Nico0020 said:**
> I had some major problems with Hardy on my E1505.  I can not connect to the internet via wired or wireless.  I finally gave up and put Gutsy back on my main partition and have made an extra partition to work on Hardy with.  It is really strange though.  I can connect while on campus, or at a friends house.  But when I try to connect at home, it never can.  I have a 2wire DSL modem/router, and it goes nuts when Hardy trys to connect to it.  It continues to shut down and reboot for as long as hardy is trying to connect.  

So for now I am staying away from hardy.

I have the same notebook, E1505 Inspiron 6400, I had no problems with Hardy, everything works better than Gutsy, even Compiz worked after installing the restricted ATI driver. Did you installed Hardy with a working internet connection? and also be suer you enable the wireless driver in the restricted drivers area. 

The only problem that I have now is with Sauerbraten, when I launch the game the screen start flickering :confused: I'm still working on that.

---

### Post by wh00mp on 2008-05-02
I managed to make the ethernet and wireless conections work. The wireless is not so good, sometimes it connects sometimes not bot at lest for now it works most of the time. I hope they fix the bugs as soon as possible. Every thing els seams to work for now.

---

### Post by lauriejb on 2008-05-03
I'd put serious money on these being router problems.  Apparently quite a lot of routers, particularly the cheaper ones, don't implement the protocols as they should.  A friend was told this by a BT engineer, and although he was using WinXP the problem was the same - and was resolved with a new router.  If you can connect somewhere then it isn't your PC/Laptop.

---

### Post by jaime256 on 2008-05-08
I think everyone has had this problem, meaning connecting to a wireless network in general under Ubuntu 8.04. I basically have to manually connect every time I turn on my computer now which is a pain because the system won't do it automatically any more like 7.10 used to. Try this after you have set your network to manually force it to connect:

sudo iwconfig wlan0 essid "your essid without the quotes"

This should find your network, just make sure you match your settings correctly or you will never find it though. Hope this helps. One more thing, this has to be done in a terminal window for the newbies.

---

### Post by Nico0020 on 2008-05-11
> **lauriejb said:**
> I'd put serious money on these being router problems.  Apparently quite a lot of routers, particularly the cheaper ones, don't implement the protocols as they should.  A friend was told this by a BT engineer, and although he was using WinXP the problem was the same - and was resolved with a new router.  If you can connect somewhere then it isn't your PC/Laptop.

Yes, that is what I believe to be the problem on my end.  I can connect everywhere except my own home to my 2wire modem.  Sucks too, as I wanted to use Hardy.  And another router is not really my option as my modem works as a router also.  I tried putting it in bridge mode before and using a router with it, but that just caused other problems.

---

### Post by atulkakrana on 2008-05-15
In my case..ubuntu recognigew both wireless ( Broadcom ) and wired ( realtek)...and it connects with cyberoam client also through browser...i enter user and pass....and login...but even after sucessfull login....fails to connect to internet...

Help is required....any suggestions

---

### Post by cartisdm on 2008-06-08
> **atulkakrana said:**
> In my case..ubuntu recognigew both wireless ( Broadcom ) and wired ( realtek)...and it connects with cyberoam client also through browser...i enter user and pass....and login...but even after sucessfull login....fails to connect to internet...

Help is required....any suggestions

I'm in your same boat.  I can see all available networks, I can enter my ESSID, I can even connect to the network (according to network-manager).  Then I try to open a webpage.....nothing:confused::confused:

---

### Post by heiko_s on 2008-07-26
Just wiped off my Windows XP from a Dell Latitude D600 to instal Ubuntu 8.04 Hardy (downloaded as ISO just 2 days ago) - no Internet !!!!!
Not via wireless, nor via regular wired connection to my router.

I tried everything, including the following:
* Static IP configuration on both router and laptop
* After some tweaking I could get a ping to my desktop PC, but still no Internet (at least no name resolution). I checked the DNS entries in the Ubuntu network configuration and they are OK - same as on my desktop PC.
* I also tried to get the wireless working, since during install and later the laptop complained about some missing or incorrect driver. I downloaded and transferred it to the laptop - still not working.
* Today I just reinstalled the same 8.04 Ubuntu, hoping that I screwed up the previous install and maybe now I would be able to get things working - no go.

I do not understand how come that there are so many complaints about this Internet and/or wireless issue (Broadcom chipset & driver) on various fora going back to April and May, but I haven't yet found an adequate solution (actually, any solution that works).

This is a serious issue with Ubuntu 8.04. I know that everything was fine when I tested 7.x and other Linuxes in the past using the life CDs, at least with the wired connection!

I'm going to install another Ubuntu/deb based distribution just to see if that is working.

---

