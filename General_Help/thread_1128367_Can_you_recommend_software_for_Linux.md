---
title: "Can you recommend software for Linux?"
date: 2009-04-17
forum: General Help
---

### Post by YMS_1975 on 2009-04-17
Hey folks,

I was wondering if there is any freeware software for Ubuntu, that will serve 2 purposes : 

1) Manage my contacts (phone numbers,addresses,date of births,etc.)
2) Manage appointments/important dates with the option of reminders.

I'm not sure if Ubuntu even has anything like that already built in. It's such a basic tool that I'm sure it's out there, but would appreciate somebody pointing it out.

BTW...I'm not interested in anything that I'd have to go online to access (I.E: Yahoo! Calendar). I'm just looking for software that's on the PC.

---

### Post by codeseer on 2009-04-17
You can do that in Evolution; it's the little envelope in the top left of your screen. I personally use Task Coach for my scheduling, but that's because I was familiar with it from Windows.

Edit:
I'm pretty sure that Evolution doesn't require you to be online to use those features. It also integrates into your desktop clock/calendar.

If not, perhaps this? [http://clay.ll.pl/osmo/]("http://clay.ll.pl/osmo/")

---

### Post by UbuntuNerd on 2009-04-17
you can also check this link: [http://www.xtuple.com/postbooks](http://www.xtuple.com/postbooks)

---

### Post by jrdonnaruma on 2009-04-17
I know you said nothing online, but you can use Google Calendar in offline mode. Google Calendar + Gears =  Offline :-)

---

### Post by Therion on 2009-04-17
Look into **Chandler** - the PIM (Personal Information Manager) for Linux.  

Well, actually it's cross-platform but there are .debs available on the website.  

[http://chandlerproject.org/](http://chandlerproject.org/)

---

### Post by codeseer on 2009-04-17
> **Therion said:**
> Look into **Chandler** - the PIM (Personal Information Manager) for Linux.  

Well, actually it's cross-platform but there are .debs available on the website.  

[http://chandlerproject.org/](http://chandlerproject.org/)

Excellent! I think I'll give this a try myself. :D

---

### Post by YMS_1975 on 2009-04-17
Thanks a lot for all the advice guys! I went with Evolution. Didn't even know that I had that there (do I have egg on my face or what?!) LOL.

Inputting all of my contacts/appointments has proven to be a time intensive task (but I'm glad I have it) but it does raise a question. If I upgrade my Ubuntu to the next version or if I was to manually upgrade Evolution, would my contacts/appointments be saved or would I be....ummmm.....screwed?   :)

---

### Post by mb_webguy on 2009-04-17
> **YMS_1975 said:**
> Thanks a lot for all the advice guys! I went with Evolution. Didn't even know that I had that there (do I have egg on my face or what?!) LOL.

Inputting all of my contacts/appointments has proven to be a time intensive task (but I'm glad I have it) but it does raise a question. If I upgrade my Ubuntu to the next version or if I was to manually upgrade Evolution, would my contacts/appointments be saved or would I be....ummmm.....screwed?   :)

As long as you're not talking about a clean installation of a new version of Ubuntu, none of your data will be lost.  An upgrade of Ubuntu or Evolution won't affect your data.

---

### Post by codeseer on 2009-04-17
> **YMS_1975 said:**
> Thanks a lot for all the advice guys! I went with Evolution. Didn't even know that I had that there (do I have egg on my face or what?!) LOL.

Inputting all of my contacts/appointments has proven to be a time intensive task (but I'm glad I have it) but it does raise a question. If I upgrade my Ubuntu to the next version or if I was to manually upgrade Evolution, would my contacts/appointments be saved or would I be....ummmm.....screwed?   :)

Backup the /home/username/.evolution directory, then restore it if needed. I recommend you set up a bash shell script, on a daily cron job, using rsync to back up your important data to another drive.

---

### Post by stchman on 2009-04-17
> **YMS_1975 said:**
> Hey folks,

I was wondering if there is any freeware software for Ubuntu, that will serve 2 purposes : 

1) Manage my contacts (phone numbers,addresses,date of births,etc.)
2) Manage appointments/important dates with the option of reminders.

I'm not sure if Ubuntu even has anything like that already built in. It's such a basic tool that I'm sure it's out there, but would appreciate somebody pointing it out.

BTW...I'm not interested in anything that I'd have to go online to access (I.E: Yahoo! Calendar). I'm just looking for software that's on the PC.

Evolution.  Very similar to Outlook in functionality.

---

### Post by codeseer on 2009-04-17
> **stchman said:**
> Evolution.  Very similar to Outlook in functionality.

I agree, except I'm still trying to get OWA to work for my university email.

---

### Post by stchman on 2009-04-17
> **codeseer said:**
> I agree, except I'm still trying to get OWA to work for my university email.

What is OWA?

n/m - Outlook Web Access

I don't know what that has to do with Evolution.

---

### Post by codeseer on 2009-04-17
MS Exchange.

Exchange supposed to support OWA, but I can't get it to work.

---

### Post by stchman on 2009-04-17
> **codeseer said:**
> MS Exchange.

Another evil M$ proprietary thing.

---

