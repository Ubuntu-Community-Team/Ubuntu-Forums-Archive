---
title: "System Shutdown issues - Latitude D630"
date: 2012-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BlackJack on 2012-07-14
I am having an unusual problem with my laptop.

Dell Latitude D630
4GB RAM
80 GB Hard Drive
Quadro NVS 135M
Ubuntu 12.04 LTS
GNOME Classic
mmmmmm... I think that's about it.

Anyway, when shutting down I seems to get “hung up on a blank screen and never finishes the shutdown procedure. Normally I see the Ubuntu screen and then a screen with several lines of text as the processes shut down (maybe the Ubuntu screen is after eh text screen?) an then eh laptop powers down. Well when this happens, it never shows the text screen and the power never shuts down, I have to manually power I down by holding the power button, or be disconnecting the AC Adapter and removing the battery.

Unfortunately, his is not always consistent as to when it happens. It only seems to be happening after I make changes to the system (it could be installing software, installing updates or just adding something to the panel), but does not ALWAYS happen every time I make changes.

Unfortunately I am not a stellar System Admin (give me a router or switch and I can make the network do whatever I want, give me a system and I am nothing more that an average end user) and I do not know where to find the log files to look at, or what to look for (I did a search for “log files” and got so may hits the reference the log files, but don't say where they are that I am still in the dark on this.

Can anybody point me in the right direction? 
Where are the log files? 
Which ones will tell me what is happening during the shutdown process?
Does this issue sound familiar to anybody?

Thanks.

---

### Post by BlackJack on 2012-07-16
I think I might have resolved his issue.

I had disabled Bluetooth in the system BIOS, but there was still a Bluetooth Manager loading when GNOME started. I removed the Bluetooth Manager from the Startup Applications and have not experienced this issue since. Of course, this is just since yesterday so I will need to watch it to make sure that this was the problem,  but so far it is looking good.

I am guessing that the Bluetooth Manager might have been hanging up while waiting for Bluetooth to shutdown. Of course, this would never happen since Bluetooth was disabled at the BIOS level. The one thing that has me still wondering is that the issue was intermittent and didn't happen every time. As I said though, it is looking good so far.

---

