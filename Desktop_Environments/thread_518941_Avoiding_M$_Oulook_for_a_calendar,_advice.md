---
title: "Avoiding M$ Oulook for a calendar, advice??"
date: 2007-08-06
forum: Desktop Environments
---

### Post by tegwilym on 2007-08-06
I'm a sys admin for an office in Seattle that is about 56% Mac, and the rest of the employees are using Windows XP Pro, with a few scattered victims of Vista (we try to avoid this when possible, but you know how new computers are!).  
Our marketing people are screaming for some kind of shared calendars (like the thing that is included in Outlook/Exchange).  The lead marketing person hates Macs and is a total Microsoft groupie.
So, I'm looking for either an Open source calendar with iCal suport, or some way to easily share calendars between employees.  I've been playing with Egroupware version 4 and really like it myself, but convince them to use a web based thing?  Ha!
So, I'd like a web based application with automatic calendar syncing with our server that is running Egroupware (or something very similar). Then they could access the calendar from any web browser, but still update their calendars when offline - like during the commute home and back on the bus/boat that people ride to get here.  (I just read a book during my commute!)

Anyway, any suggestions ideas or advice on something?  I refuse to go back to Exchange/Oulook that isn't an option. Even some shareware thing that works that would cost something would be fine, but we aren't going the Microsoft way.

Help!

Tom
Somewhat frustrated Sys Admin
(I'm sold on Ubuntu and personally run it 99% of the time at work and home!)

---

### Post by nichipet on 2007-08-06
When I first starting read your post I was thinking of Sunbird, from the Mozilla Foundation. But you are looking for a web-based calendar. I wonder if Sunbird has Google Calendar integration. That may work (I really don't know, considering your other requirements, but maybe). I'm curious of a solution to this.

---

### Post by BoneKracker on 2007-08-06
There are many options.  Here is a good place to look:

[http://en.wikipedia.org/wiki/Category:Free_groupware](http://en.wikipedia.org/wiki/Category:Free_groupware)

---

### Post by tegwilym on 2007-08-06
> **nichipet said:**
> When I first starting read your post I was thinking of Sunbird, from the Mozilla Foundation. But you are looking for a web-based calendar. I wonder if Sunbird has Google Calendar integration. That may work (I really don't know, considering your other requirements, but maybe). I'm curious of a solution to this.

Oh I forgot to mention that I have tried Sunbird/Lightning from Mozilla.  The syncing is pretty awkward even if I did set up a Davweb server.  Everything I've read isn't very clear no how this should work.  I just get errors when it tries to sync.  I like the web method, then everyone can reach it no matter what OS platform they run, and with VPN they can reach it from outside too.

Tom

---

### Post by col.panic on 2007-08-09
I use Sunbird on windows and linux and as long as you download the provider extension for google calendar(its on the mozilla addons website).  I found it works flawlessly with google calendar and google calendar suports ical as well.  Has anyone gotten evolution to 2 way sync with google calendar because that is my app of choice on linux

---

### Post by tegwilym on 2007-08-10
> **col.panic said:**
> I use Sunbird on windows and linux and as long as you download the provider extension for google calendar(its on the mozilla addons website).  I found it works flawlessly with google calendar and google calendar suports ical as well.  Has anyone gotten evolution to 2 way sync with google calendar because that is my app of choice on linux

I'll take a look at that.  But since this would be for business use to sync between employee calendars, I'd prefer to set up an internal web server.  The if needed, they could reach it through VPN from outside.  I've been trying to get the Egroupware iCal server working, but no luck yet.  The HowTo pages seem kind of experimental since the mozilla stuff is still very new.

---

### Post by Wharf Rat on 2007-08-11
> **tegwilym said:**
> I'll take a look at that.  But since this would be for business use to sync between employee calendars, I'd prefer to set up an internal web server.  The if needed, they could reach it through VPN from outside.  I've been trying to get the Egroupware iCal server working, but no luck yet.  The HowTo pages seem kind of experimental since the mozilla stuff is still very new.

You might look at a Nitix server. They run Exchange it - their answer to Exchange Servers.  It has a web interface that supports shared calendars.  The Windows/Outlook users can access the system using Outlook as a frontend.

[www.nitix.com](www.nitix.com)

---

### Post by HermanAB on 2007-08-11
Webcal by Maurong Zou from U Texas is pretty good and I've been using it for years:
[http://www.math.utexas.edu/users/mzou/webCal/index.html](http://www.math.utexas.edu/users/mzou/webCal/index.html)

Otherwise, you can get a full fledged email, calendar, chat, whatever server from Citadel:
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

Citadel is extremely easy to install - takes about 15 minutes.  Or you can use a pre-installed VMware image, which takes about 5 minutes.

Cheers,

Herman

---

### Post by spacegypsy on 2007-08-12
I don't know about how to stay in sync with evolution but if you're using thunderbird and want to sync it with google cal you can use this link;

[http://bfish.xaedalus.net/?p=239](http://bfish.xaedalus.net/?p=239)

it works perfect for me.

---

