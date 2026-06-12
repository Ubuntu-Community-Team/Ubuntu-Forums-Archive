---
title: "sync calendars, mobile, google, evolution on 2 computers"
date: 2009-03-02
forum: General Help
---

### Post by aBitLater on 2009-03-02
Hi,  
I've seen this post: [http://ubuntuforums.org/showthread.php?t=540330&highlight=sync+calendars]("http://ubuntuforums.org/showthread.php?t=540330&highlight=sync+calendars")

And I was wondering if anyone else has any input or advice on how to get all my calendars in sync, so I can use any one at any time and have the same info.

My setup:
1 Sony Ericsson w580i mobile
2 ubuntu computers - one desktop, one laptop
1 google calendar

I don't have to use the google calendar, I just mention it in case it makes synchronization easier (as a go-between).

Many thanks,
Brian

---

### Post by fragos on 2009-03-02
Evolution calendar can be configured synch with Google calendar. I don't know about your phone -- good luck there. Your phone's synch abilities will probably determine your approach. As an example this is what I do with a desktop, laptop and Nokia N810. To start the N810 runs Linux. I found a set of applications in the GPE family that's available on my N810 and on Ubuntu that I run on my other machines. This gave me a calendar and other PIM functions that are file compatible on all platforms. The N810 also has an ap to sync with Google calendar for those times that I on another machine. The N810 has a qwerty keyboard and is always with me. It is my primary PIM data entry vehicle and synching with Google makes my calendar instantly availble on my other devices. On a regular basis I file transfer all the PIM data bases to my desktop which then uses Unison to sync with my laptop. A bit of a mashup with a manual componet in the process but data is only entered once. The N810 doesn't have a cell modem as a smaertphone does but also has the benefit of not being feature crippled by a carrier to force you to buy media from them or use as much air time as they can make you.

---

### Post by MickSulley on 2009-03-05
Yes I would like to do this as well.  My primary requirement is between laptop and desktop, to sync all of Evolution not just calendars.  I know I can copy the files across but that overwrite the older one rather than sync the changes to both.  I am surprised that there does not seem to be any easy way to sync Evolution to Evolution.

Any suggestions gratefully received.

---

### Post by fragos on 2009-03-05
> **MickSulley said:**
> Yes I would like to do this as well.  My primary requirement is between laptop and desktop, to sync all of Evolution not just calendars.  I know I can copy the files across but that overwrite the older one rather than sync the changes to both.  I am surprised that there does not seem to be any easy way to sync Evolution to Evolution.

Any suggestions gratefully received.

You can sync Evolution to Evolution DB files. You can use Unison for this purpose. And Evolution Calendar can sync with Google Calendar but the config is less than obvious. My reason for using the GPE aps was compatibility between my Ubuntu desktops and my Nokia N810 Internet Tablet. The GPE aps come up faster than Evolution and go directly to the DB I need without an interim step in the Evolution wrapper that assumes email. We all have our preferences and personalities.

---

### Post by MickSulley on 2009-03-05
How can I sync Evolution DB files using unison?  As far as I am aware I can over-write the older one with the newer one, but if for example I have added or updated contacts on desktop and laptop then the later file will over-write the newer one and I have lost one set of changes.  Have I missed something here?
Cheers
Mick

---

### Post by fragos on 2009-03-05
It does sync on a file vs transaction basis. Either side can change and if both have since the last sync it asks what to do. Perhaps not perfect but workable. For my three way setup I favor my mobile for changes and sync so that all devices can retrieve. That doesn't prevent me from using any of the devices for changes -- just really limits to one change device per sync. I your ap stores as individual event files then you get sync at the transaction level but still can't change the same event in two places and expect it to sync.

---

### Post by Bunro on 2009-03-10
I am having the same challenge (desktop, laptop and mobile phone Nokia E71). I find the following link that is working for me with the Nokia E71 phone. The phone sync is working at this stage.
  [http://lumumba.uhasselt.be/frederickgaens/SyncE71Linux.html](http://lumumba.uhasselt.be/frederickgaens/SyncE71Linux.html)
 

 Unison is working only on database level and not on the individual contact and/or task level.
 

 I found the following link via Google [http://www.scheduleworld.com/sw2/index.html](http://www.scheduleworld.com/sw2/index.html)
 But I prefer to keep my data local.
 

 Regards, Robert

---

### Post by markosp on 2009-11-30
Hi! I just opened a new thread: [http://ubuntuforums.org/showthread.php?t=1341792](http://ubuntuforums.org/showthread.php?t=1341792)

Please check it out

---

