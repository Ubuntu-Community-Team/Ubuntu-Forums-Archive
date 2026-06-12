---
title: "Lightning 0.9 (wcap) does not work in Thunderbird 2.0.0.23 (20090817)"
date: 2009-09-15
forum: Desktop Environments
---

### Post by kweepeer on 2009-09-15
Hi,

I use ubuntu 904 server (32 bit) (as a sunray server) and tried to install the lightning wcap ([https://addons.mozilla.org/en-US/thunderbird/addon/2313](https://addons.mozilla.org/en-US/thunderbird/addon/2313)) add-on in thunderbird 2.0.0.23. After installation and restart of thunderbird, you cannot add a calendar and most of the Preferences do not work, lighning with wcap is unusable.

Is there something that I miss? Should this work or is it known not to work at all?

Thnx

---

### Post by celebroom on 2009-09-23
Exactly the same problem here.  Experienced with Lightning 0.8 and 0.9. :(

---

### Post by mtn on 2009-10-30
Yup, same here. Says on the [project page that Lightening 0.9]("https://addons.mozilla.org/en-US/thunderbird/addon/2313") (the version I have tried) only works with Thunderbird: 2.0 – 2.0.0.*, and it goes on... 

* Lightning 0.9 is intended to be the last release for the Thunderbird 2 series. For the future we are planning to integrate Lightning fully into the upcoming Thunderbird 3 release.

Damh! I was so close to getting all my [calenders synced up]("http://thebankshow.com/2008/04/30/integration-of-online-calendars/")

I'm running Karmic Ubuntu 9.10 so not sure how to get round this. Any suggestions?

---

### Post by noob555 on 2009-10-30
Same problem here, although it happened to me as soon as I upgraded to Karmic Beta over a week ago.  I've been trying to figure out what's wrong, but nobody seems to have an answer on the forum.  Unfortunately, I'm just not saavy enough to figure this stuff out on my own.

Does anyone have any ideas?

---

### Post by mtn on 2009-10-30
After messing about I got the calender working. 

I uninstalled the Lightning 0.9 add-on I had tried and. 

Installing libstdc++5 was mentioned as a fix in a number of forums/bug reports, so i installed libstdc++5 and libstdc++6! I then used Synaptic to install Lightning from the repos - that seemed to work for me. 

I got Lightning working with Facebook "birthday events", however, it wouldn't work with just "events" - which would be very sweet.

---

### Post by noob555 on 2009-10-30
OK, cool.

I uninstalled Lightning, but I can't figure out how to install libstdc++5 or libstdc ++6.  It doesn't seem to come up in synaptic and I can't figure out how to do it from the terminal.

---

### Post by mtn on 2009-10-30
> **noob555 said:**
> OK, cool.

I uninstalled Lightning, but I can't figure out how to install libstdc++5 or libstdc ++6.  It doesn't seem to come up in synaptic and I can't figure out how to do it from the terminal.

Opening up a terminal session Applications>Accessories>Terminal and then pasting ```
sudo aptitude install libstdc++5

```worked for me. I have all the repos checked in System>Administration>Software Sources. I also have the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos added - these are the only extra repos I have!

---

### Post by noob555 on 2009-10-30
I looked around and libstdc++5 is just not in the Karmic repositories.  I get a weird error from the terminal before it asks if I want to continue. So I'm not even going to try.

HOWEVER, I was able to find "lightning-extension" in the repositories.  Just installed and it works like a charm.  It's a bit hard to find in Synaptic so I recommend just opening Applications --> Ubuntu Software Center --> Search: "Lightning".  It should come straight up.

It and works *perfectly*.  Gmail calendars through Provider and everything are working just as before.  :D

---

### Post by lipkap80 on 2009-11-09
sudo apt-get install lightning-extensions works fine as well.

---

