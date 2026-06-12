---
title: "Syncing multiple calendars in Evolution to Palm... or merging calendars in Evolution?"
date: 2007-08-22
forum: Desktop Environments
---

### Post by naked on 2007-08-22
Is there anyway to do this?  I have 3 calendars that I want to sync.  I'd also be ok with merging them into one calendar as well, but I don't know how to easily do this.

I have a Treo 680 if that makes any difference.

L

---

### Post by elektronaut on 2007-11-15
I just (hopefully) solved this problem. It involves J-Pilot as the sync partner for the Palm, because Evolution doesn't work the way you want. It's a bit tricky - it involves shoving iCalendar files between J-Pilot and Evolution. I didn't test it yet in both directions, so you have to see for yourself it it works. I had to do try it because this happened to me: 

I used to sync with J-Pilot - no trouble with duplicates like with Evolution and other advantages. Then I also synced with Evolution because I wanted to get contacts and appointments also on my mobile phone and Google Calendar (search for the scheduleworld thread). To further complicate the whole story, I had split my appointments in two calendars for Evolution / Google (one public, one personal). What happened was, that after synhing with Evolution a lot of appointments disappeared from my Palm. The whole set of my appointments was now spread between the two Evolution calendars and the Palm calendar. And J-Pilot doesn't seem to offer a *'Desktop overwrites PDA'* conduit policy, which would have replicated the appointments on my Palm. Being dumb as I am sometimes, I gave it a shot and synced with J-Pilot. As you might have guessed, the appointments disappeared there also. 

So, in the end I installed the iCalendar import support for J-Pilot, like described [**[COLOR="Red"]on this page[/COLOR]**](http://www.computechgroup.com/?p=381). I also had to install the libpisock-dev package, otherwise *./configure* wouldn't work: ```
sudo aptitude install libpisock-dev
```
In the end I exported the two calendars from Evolution, imported them in J-Pilot, and finally synced my Palm again with J-Pilot. Don't know yet how to get new appointments from J-Pilot to Evolution, but for now I have disabled the calendar sync conduit in Evolution.

---

