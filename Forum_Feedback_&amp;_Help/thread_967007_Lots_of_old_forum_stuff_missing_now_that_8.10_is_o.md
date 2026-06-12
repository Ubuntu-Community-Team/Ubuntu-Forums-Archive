---
title: "Lots of old forum stuff missing now that 8.10 is out?"
date: 2008-11-01
forum: Forum Feedback &amp; Help
---

### Post by Jim Lewis on 2008-11-01
It has been a few days since I logged in here, but since I'm STILL having NVIDA resolution problems I logged in today to get a "sticky" that _was_ in the Video section only to find that it was gone.  I searched for and did not find it in the Archives (there are several NVIDA articles there, but not this one).

I can't recall the title, but it was something to the effect that it was a compilation of "solutions" to the problems with these drivers.  _Does this still exist here, somewhere_, or is there some other way I could get it?

I'm still using Feisty (but have ordered an 8.10 disk), but would like to see if I can get more than 800x600 res between now and then.  (Though it seems there _still_ are NVIDA problems with 8.10.)

This seemed the most logical place to put this query.  Appologies if it isn't.

jim

---

### Post by schauerlich on 2008-11-01
We've had way too many stickies, there has been a lot of condensing lately. Also, a lot has changed between 7.04 and 8.10. Your video problem may well have been fixed. Is there a reason you're not able to download your own .iso and have to order a CD?

---

### Post by kevdog on 2008-11-01
Seems like to me alot of the old stickies were relevant no matter what the version number.  Seems very presumptuous of the forum staff the day Ibex was released to automatically declare all the old stickies "invalid" and remove them.  A great dis-service to many, particularly those not choosing to upgrade.

---

### Post by Jim Lewis on 2008-11-01
> **EDavidBurg said:**
> We've had way too many stickies, there has been a lot of condensing lately. Also, a lot has changed between 7.04 and 8.10. Your video problem may well have been fixed. Is there a reason you're not able to download your own .iso and have to order a CD?

Alas, yes.  A very unreliable ISP (the only DSL provider in the area (I'm WAY out in the country)).

I saw the thread about too many stickies.  That may be true -- except when you need one, like I do.  :)  Are they all gone, then?

---

### Post by schauerlich on 2008-11-01
Threads are very rarely deleted, so I'm sure they still exist. They just aren't stickied anymore. Try using google and putting site:ubuntuforums.org before your query. That way it only searches the forums, and it gives much more reliable results than the forum's built in search function.

---

### Post by cyberdork33 on 2008-11-01
> **Jim Lewis said:**
> I saw the thread about too many stickies.  That may be true -- except when you need one, like I do.  :)  Are they all gone, then?
They are not deleted, just unstickied.

---

### Post by Jim Lewis on 2008-11-02
> They are not deleted, just unstickied.

Ahhh.  And, like,  where would they have gone?  5,300 pages  (+-) back somewhere according to the date they were originally posted?]

Hard to find those when you don't remember the topic line "quite right."    OR the date?

---

### Post by ugm6hr on 2008-11-02
> **kevdog said:**
> Seems very presumptuous of the forum staff the day Ibex was released to automatically declare all the old stickies "invalid" and remove them.  A great dis-service to many, particularly those not choosing to upgrade.

The stickies were not felt to be invalid at all.

Stickies have to be reserved for threads that are felt most relevant to the most users.  The most benefit for the most users.  

Unfortunately, that means that most apply to the latest release.

Having more than about 3 stickies in each sub-forum makes them annoying when browsing multiple sub-forum pages.  And despite this, it is apparent lots of people disregard information within stickies.  We do try and index any unstickied relevant posts in a "Contents" type post somewhere.

As mentioned - threads are almost never deleted just unstickied.

Unfortunately, your thread is probably in the Archive, since Feisty is not supported on the desktop (so video card advice is probably genuinely irrelevant), and it would truly be irrelevant to the vast majority of users.

My advice for all: subscribe to any threads that are relevant to you, and arrange your subscriptions appropriately (you can create folders).

---

### Post by cyberdork33 on 2008-11-02
> **Jim Lewis said:**
> Ahhh.  And, like,  where would they have gone?  5,300 pages  (+-) back somewhere according to the date they were originally posted?]

Hard to find those when you don't remember the topic line "quite right."    OR the date?
That's why I bookmark things I want to find again.

---

### Post by Jim Lewis on 2008-11-03
Well, I knew where it _was_ . . . but it isn't there any more.  Anyway, I think I've found it.  Now I just have to figure out what it means; At 71, I'm not as geekish as I used to be.

---

### Post by chengzi86 on 2008-11-03
PFA (Perfluoroalkoxy) which for **[chemical valve](http://www.corrosion-resistant-valves.com)** was developed in order to achieve a true melt-processable fluoropolymer.FEP (Fluorinated Ethylene Propylene) is another melt-processable Fluoropolymer. It does not have the almost universal **[chemical valve](http://www.corrosion-resistant-valves.com)** resistance of PTFE and PFA and its maximum operating temperature in service is 150oC.chemical valve [www.corrosion-resistant-valves.com](www.corrosion-resistant-valves.com)

---

### Post by ua6icab7 on 2008-11-06
[WOW Gold](http://www.gold4power.com/) was released in 2000 and is part of the WOW Hits series.It was a single 2-CD/2-cassette collection of contemporary Christian music from the 1960s to the time it was released. Marketing & distribution responsibilities for this title in the WOW Hits series was relegated to Brentwood Records (now Provident Music Group). The album reached #111 on the Billboard 200 chart.

---

### Post by alwayshere on 2008-11-06
You could try this 

sudo apt-get install 915resolution
--------------------------------------

sudo apt-get update 
--------------------------------------

sudo 915resolution 3c 1024 768
--------------------------------------

sudo gedit
--------------------------------------

Insert the two below lines

    #!/bin/bash 915resolution
    3c 1400 1050

Save it as /etc/init.d/resolutionfix.sh
---------------------------------------

sudo chmod +rx /etc/init.d/resolutionfix.sh
--------------------------------------------

sudo update-rc.d resolutionfix.sh defaults
--------------------------------------------

now restart

---

