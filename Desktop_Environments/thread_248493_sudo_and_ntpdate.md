---
title: "sudo and ntpdate"
date: 2006-09-01
forum: Desktop Environments
---

### Post by holyhalo on 2006-09-01
I will describe my situation.

At August 30 clocks on my computer was set to August 31.
I dicided to repare this situation and use ntpdate to adjust the clocks.
I do 
$sudo ntpdate pool.ntp.org
My clocks was set to current time at August 30.
Thats ok.
Then I want to do some administrative task on my computer and do
$sudo <some_command>
sudo will write to me that timestamp is far away in future and do not execute <some_command>
Till August 31 I can't do administration tasks with sudo.
What to do?

---

### Post by alecjw on 2006-09-01
You did ntpdate wrong. Don't ntpdate with pool.ntp.org. It should be:
mirrornumber.countrycode.pool.ntp.org
Eg in the uk, it should be something like 0.uk.pool.ntp.org or 1.uk.pool.ntp.org

Goto [http://ntp.isc.org/bin/view/Servers/NTPPoolServers](http://ntp.isc.org/bin/view/Servers/NTPPoolServers) and select your comtinent, then it will give you a list of servers.

---

### Post by holyhalo on 2006-09-01
Thank You! Very interesting information abount ntpdate.
And what to to with sudo?

---

### Post by alecjw on 2006-09-01
I'm not quite sure what to do about that, but let's try the windoze way! Reboot!

---

### Post by holyhalo on 2006-09-01
:))))))

---

