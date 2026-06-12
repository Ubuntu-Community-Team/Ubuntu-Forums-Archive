---
title: "Hardware Stats for DE"
date: 2016-11-06
forum: Desktop Environments
---

### Post by Blackbug on 2016-11-06
Is there any application which can log the hardware stats for the DE. I want to compare the stats esp. cpu, battery drain, fan usage, ram for a session and then can generate some kind of graphs and compare with other DE's.

I know psensor but it doesn't record battery drain. I am not sure if any such app though.

---

### Post by mastablasta on 2016-11-07
why would fans speed be depndent on DE?


htop for CPU, RAM

powerstat, powertop for battery
[http://askubuntu.com/questions/73904/how-do-i-monitor-power-consumption](http://askubuntu.com/questions/73904/how-do-i-monitor-power-consumption)


note that the problem with so many apps is that they each measure in a different way. IMO if you take a terminal app (that doesn't actually depend on gtk, qt etc.) and use it in all DE you should get comparable results.

there are also services for server that can run and logs status. so you can see changes over time. for example like collectd

have a look at this comprehensive list if you can find something good. most will not do the battery usage. :
[URL="https://blog.serverdensity.com/80-linux-monitoring-tools-know/"]https://blog.serverdensity.com/80-linux-monitoring-tools-know/
[/URL]

---

