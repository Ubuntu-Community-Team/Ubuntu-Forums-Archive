---
title: "Weird power problem - spontaneous reboot"
date: 2009-03-31
forum: General Help
---

### Post by dhughes on 2009-03-31
This is an odd problem, I'm using a fresh install of 8.10 2.6.27-11-generic that I installed a few days ago (~March 27/'09) after wiping my drive of an 8.10 install updated via Update Manager to 9.04 Beta (not sure which build it was) the 8.10 version was on since October 2008 and worked fine.

 Before any of this my system was fine with uptimes of months until I had to reboot for various reasons none of which were due to system errors.

 I wiped it due to a mouse problem, it became unbearably laggy, I had a look but couldn't get it to work but most of all the worst thing was a weird power failure/reboot which occurred out of the blue. Now it just happened again, twice within two hours, this time it's on the new 8.10 install from a recently downloaded 8.10 installed on a my formatted my drive a few days ago.

 I don't think it's a hardware problem, power supply, because my system has been fine since July (new build) although it could be swelled capacitors and I've only recently begun to power off my system at night when I'm not downloading or seeding torrents.

 I looked in the log files, nothing stands out, I'm about to go look at launchpad for reboot or power off bugs.

 Posting this before it's too late...!

(April 3/09) edit: It seems when using a browser and Flash is used on the webpage or a PDF opened my mouse lags big time but not my entire system, just the mouse.
(April 4/09) edit#2: It does it even without the browser being open and it did it from a cold boot. Something is running lagging my system, System Monitor isn't showing anything unusual - but even it lags while updating.

---

### Post by dhughes on 2009-04-06
I switched to Kubuntu (8.10), it was getting impossible to try to troubleshoot with a mouse and system lagging so bad you couldn't do anything in X, so I'm trying KDE 4.2 which is interesting and very different than Gnome! 

 I thought it was using Flash in Firefox, PDF in Firefox, Nvidia restricted drivers, then trackerd but there wasn't any common thing.

 Whatever happened to Ubuntu or Gnome after October 2008 just killed my system performance, it was fine in Oct. 08 but after that it's horrible. An Ubuntu 8.10 download, burned, installed in October 2008 works great but but an Ubuntu 8.10 download, burned, installed in April 2009 has very bad lag (mouse and system), so did the Ubuntu 9.04 Beta I tried about a week ago.

 Everything is great with KDE, no lag, everything is snappy! Even Openoffice opens in the blink of an eye compared to what seemed like ages in Gnome.


...moving on

---

### Post by dhughes on 2009-04-13
It did it again, I don't understand what it could be other that the power supply but it's so random I can't tell. 

 Just a few moments ago my system powered off, no shutdown just off, rebooted, then powered off again just before the POST (No OS involved just BIOS, that's why I'm thinking Power Supply).

 It must be hardware :(

---

### Post by defaultusername on 2009-04-13
dhughes,

Unfortunately, the only thing you can do is test components one-by-one to identify the culprit. Once you've resolved that issue, it wouldn't be a bad idea to run torture tests overnight to ensure stability. If you feel that the PSU might be fubar, then consider investing in a quality multimeter to test PSUs for proper functionality before using them before/after a build. Check your motherboard for leaking (bursted) capacitors; it's entirely possible to replace them with some soldering. I've done similar things with high $ MB's.

Good luck!

---

### Post by dhughes on 2009-04-18
Thanks, for the suggestions.

 I have a new Power Supply sitting next to me but I want to be sure more for curiosity's sake that it is the PSU. Wouldn't you know it my multimeter isn't working either, I'm going out in a few minutes to buy a new meter, which ironically will probably cost more than the PSU I just bought. 

 What gets me is I built this system in July 2008 and it worked fine with Ubuntu 8.04 and Ubuntu 8.10 but as soon as I tried the Beta of Ubuntu 9.04 this is when the trouble started, even Kubuntu 8.10 doesn't work if that is the problem - there's nothing worse than convincing yourself of a non-existent problem and chasing it.

 CPU temps are fine at 31C, any fan failure in BIOS is set disabled to prevent and power off.

 It funny though because right now at work I have a couple pieces of equipment down because of failed power supplies, swollen caps. Someone needs to invent a better capacitor.

---

### Post by dhughes on 2009-04-18
I've replaced the power supply, I didn't bother getting a new meter, and so far so good, at one point before I swapped the PSU I thought it may be my seven year-old UPS but it wasn't, same result when not using the UPS, anyway my uptime is great now no reboots or power fails since the install or so says **last -20 reboot**.

 Now I've discovered **dmidecode** I'm experimenting with it to see if I can track the voltage of my motherboard using the BIOS utilities, it would have been nice to know about it sooner!

---

### Post by rmadla on 2009-05-09
The power supply seems to have solved the problem for you, but I fear that it may not for others: in case this information is useful, I offer the following information (sadly, without solution).

I used 8.04 for two months without problem, and last week, decided to upgrade to 9.04. Since then, I have experienced four apparently random spontaneous reboots. In each case, it has been after the system has been running for many hours, and after several resource-intensive programs have been used (Pandora within Firefox, Virtualbox, OpenOffice). I haven't detected any other patterns that would allow me to predict impending doom. :(  One minute I am working happily, the next microsecond all joy is gone and my system is starting up.

Since my problem coincided with the upgrade, I suspect that in my case the problem is ***not*** due to hardware failure. I'm afraid I'm a noob (8.04 marked my switch to Linux from Windows), so am not sure how to proceed from here, where to post bug reports, etc., although learning more about such things may have to be this morning's project.

---

### Post by SLEEPER_V on 2009-05-10
> **rmadla said:**
> The power supply seems to have solved the problem for you, but I fear that it may not for others: in case this information is useful, I offer the following information (sadly, without solution).

I used 8.04 for two months without problem, and last week, decided to upgrade to 9.04. Since then, I have experienced four apparently random spontaneous reboots. In each case, it has been after the system has been running for many hours, and after several resource-intensive programs have been used (Pandora within Firefox, Virtualbox, OpenOffice). I haven't detected any other patterns that would allow me to predict impending doom. :(  One minute I am working happily, the next microsecond all joy is gone and my system is starting up.

Since my problem coincided with the upgrade, I suspect that in my case the problem is ***not*** due to hardware failure. I'm afraid I'm a noob (8.04 marked my switch to Linux from Windows), so am not sure how to proceed from here, where to post bug reports, etc., although learning more about such things may have to be this morning's project.

I'm having the same problem, oddly enough

---

### Post by dhughes on 2009-06-05
> **rmadla said:**
> ... I'm afraid I'm a noob (8.04 marked my switch to Linux from Windows), so am not sure how to proceed from here, where to post bug reports, etc., although learning more about such things may have to be this morning's project.

 Go to launchpad.net, make an account and snoop around.

 Pretty much any problem has already been reported and you can read the comment under the report, it give you a good idea where to look or at least what is not part of the problem, so you don't waste your time only to find out 1,000 other people already know about it.

---

### Post by zenarcher on 2009-06-05
I was having the same problem with one of my systems here.  It had a fairly new and adequate power supply, but thinking of nothing else I could determine to be the problem, I replaced the power supply.  Same result...once I had replaced the power supply, the random rebooting disappeared.

Cheers,
zenarcher

---

