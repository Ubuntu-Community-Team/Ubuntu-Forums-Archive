---
title: "Weather Report - units problem"
date: 2012-12-09
forum: Desktop Environments
---

### Post by lprofil on 2012-12-09
Hello,

there is a problem on my Ubuntu 12.10 system on which the gnome-fallback-session is installed as windowmanager. I put the "Wether Report" into the topbar. There i can not change the units for Fahrenheit to Celsius even though i can choose them. I already deleted it at put it back there but nothing changes.

Does anybody has an idea where i can find a config file to do the change by hand?

Thanks in advance!

/lprofil

---

### Post by ohnonot on 2012-12-10
gnome-fallback-session is not a window manager.
i guess it's what your display manager chooses at login.
(yes, the terms are confusing. however they are doing very different things. the display manager starts a session, which usually includes a window manager)

however, gnome-fallback-session sounds wrong.
try to get it to start default session, then see if you can change the values.

if you can't solve it, please post more detail.

if you can solve it, please mark it so.

---

### Post by lprofil on 2013-04-13
Dear ohnonot,

thanks for your reply. My problem still exists in 12.10 and 13.04.

To be a bit more verbose i will post the weather report of my current 12.04 system 
and of a fresh installed 13.04 system in a virtualbox enviroment.



# 12.04 current system with working weather report units
[IMG]http://helios.wh2.tu-dresden.de/~gulliver/12.04_weather_report_working_units.png[/IMG]


# 13.04 system, broken weather report units, visible but will disappear after closing the menue and not switch to desired units
[IMG]http://helios.wh2.tu-dresden.de/~gulliver/13.04_weather_report_broken_units.png[/IMG]


Believe it or not: it is the only thing keeping me from upgrading to a newer version ;)

I really appreciate any kind of help. Thanks in advance!

/lprofil

---

