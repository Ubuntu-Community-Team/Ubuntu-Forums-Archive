---
title: "Ubuntu v8.10 doesn't keep time"
date: 2009-01-12
forum: Desktop Environments
---

### Post by corsairgt on 2009-01-12
I installed v8.10 on a USB flash drive. The Time and Date Settings were configured as follows:

Time zone: Asia/Hong_Kong
Configuration: Keep synchronized with Internet servers
Time servers: stdtime.gov.hk

However, after each reboot,the time zone is default back to Africa/Accra. Does anyone have a clue?

---

### Post by npatel31 on 2009-01-12
use ntp service to synchronize your time to one of the time servers in your country.

I suspect, battery on your system board is out.

---

### Post by mgol on 2009-01-12
npatel31, he already posted that he has ntp enabled - this option:
"Configuration: Keep synchronized with Internet servers"
states it clearly.

I don't know if it must be connected to a battery state. My Intrepid also had time problems. I mean, it didn't change my time zone (I live in Poland), but Intrepid after a few hours of being not used was loosing a couple of hours... I even made a script which I invoked each time I was going back to my computer after a long time of not using it (this script turned off ntp service, then synchronized time using a command 'ntpdate ntp.certum.pl' and then turned it on again).

I switched back to Hardy and I no longer have these problems. Maybe I should fill a bug but I use Intrepid no more so it could be hard for me to keep track on it; besides that, I don't have too much free time right now.

I've posted a thread some time ago about this issue, but nobody responded. It's located here:
[http://ubuntuforums.org/showthread.php?t=983958](http://ubuntuforums.org/showthread.php?t=983958)

---

### Post by corsairgt on 2009-01-13
It has nothing to do with the battery state of my notebook PC. The same problem shows up on my old(XP)and new(Vista)laptop PC. Both laptops are keeping time accurately. I think this is an Intrepid bug.

---

### Post by corsairgt on 2009-01-28
I've finally figured out how to configure v8.10 to keep time accurately. The trick is NOT to choose any time server. Don't ask me why but it works!:)

---

### Post by mgol on 2009-01-28
Maybe You should report a bug on launchpad. It should be fixed...

---

