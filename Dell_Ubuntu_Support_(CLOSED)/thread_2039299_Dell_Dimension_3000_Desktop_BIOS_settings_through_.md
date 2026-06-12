---
title: "Dell Dimension 3000 Desktop BIOS settings through SSH (Automate Startup)"
date: 2012-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by salgala2000 on 2012-08-08
Hello Ubuntu forums,
I have Dell Dimension 3000 Desktop with Ubuntu on it. Right now I keep the computer on 24/7, but it do not have a monitor connected to it. I usually SSH to it from my laptop and I also run a Samba server from it. I would like to have an automated Startup and Shutdown time (for every day) to conserve energy and to avoid the noise of the fan while I'm sleeping. So here's a three part question?

1) How can I automate my computer to go to sleep or shutdown (whichever is easier) at a specified time every day?

2) How can I automate my computer to wake up or startup at a specified time every day?
3) I think #2 has to be edited in the BIOS but I'm not sure. If so, is there a way to edit the BIOS from SSH, or do I have to lug a monitor upstairs to edit it?

Thank you for any and all help

---

### Post by papibe on 2012-08-08
Hi salgala2000.

> **salgala2000 said:**
> 1) How can I automate my computer to go to sleep or shutdown (whichever is easier) at a specified time every day?
You can use crontab to shutdown your computer at a predetermined time. Here's a [guide]("https://help.ubuntu.com/community/CronHowto") to crontab, and here an shutdown [example]("http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html").


> **salgala2000 said:**
> 2) How can I automate my computer to wake up or startup at a specified time every day?
You can't do that exactly. However, if you can set up the machine to turn on using [WOL]("http://en.wikipedia.org/wiki/Wake_on_lan"), it may be possible. Check this [guide]("https://help.ubuntu.com/community/WakeOnLan") to set up WOL. Note that you would need another device to wake up your machine. A router running DD-WRT would be one of the ideal options (see [here]("http://www.howtogeek.com/70084/how-to-schedule-your-computer-to-wake-up-at-specific-times-with-dd-wrt/")).


> **salgala2000 said:**
> 3) I think #2 has to be edited in the BIOS but I'm not sure.
To enable WOL on your computer it may be necessary to go into the BIOS just **once** to enable waking up the computer over the network card.


> **salgala2000 said:**
> is there a way to edit the BIOS from SSH, or do I have to lug a monitor upstairs to edit it?
Unfortunately no, but it shouldn't be necessary.


I hope that helps. Let us know how it goes.
Regards.

---

### Post by salgala2000 on 2012-08-08
[QUOTE=papibe]Hi salgala2000.


You can use crontab to shutdown your computer at a predetermined time. Here's a [guide]("https://help.ubuntu.com/community/CronHowto") to crontab, and here an shutdown [example]("http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html").[/QUOTE]

Thank you very much, I set this up and it's working perfectly!

[QUOTE=papibe]
You can't do that exactly. However, if you can set up the machine to turn on using [WOL]("http://en.wikipedia.org/wiki/Wake_on_lan"), it may be possible. Check this [guide]("https://help.ubuntu.com/community/WakeOnLan") to set up WOL. Note that you would need another device to wake up your machine. A router running DD-WRT would be one of the ideal options (see [here]("http://www.howtogeek.com/70084/how-to-schedule-your-computer-to-wake-up-at-specific-times-with-dd-wrt/")). To enable WOL on your computer it may be necessary to go into the BIOS just **once** to enable waking up the computer over the network card.[/QUOTE]

Thank you for this advice. My router isn't running DD-WRT, but I think I have a solution that will work for me. I will try this tomorrow and post results, but my plan is to enable WOL on my desktop and then get a WOL client on my (jailbroken) iphone and set it to every morning. I keep my charging through the night, and if I'm not home I don't need my computer on anyway, so this solution would be ideal for me. I'll post results tomorrow for future reference for anyone trying to do something similar.

Thank you for the help!

---

### Post by salgala2000 on 2012-08-10
UPDATE: In my computer's BIOS settings there was an option from automated startup, so I just used this instead of WOL.

---

