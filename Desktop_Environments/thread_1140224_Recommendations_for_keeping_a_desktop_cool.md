---
title: "Recommendations for keeping a desktop cool?"
date: 2009-04-27
forum: Desktop Environments
---

### Post by stair314 on 2009-04-27
I built my own desktop and it's always had some issues with heat. This is largely because I don't know much about what I'm doing.
I first built it about a year ago. The case is an Antec Sonata III. It only has one fan that blows out. The CPU is a Core 2 quad core. I'm just using the default fan/heatsink that came with it.
When I built it, I installed Gutsy, and was using lm-sensors to try to monitor the temperature level. This required setting up files to convert voltages to temperatures and I was never very confident that I'd gotten them right.
When I upgraded to Hardy, my sensors applet could suddenly see something called "libsensors" which had fairly plausible temperatures-- like 30-40 C at rest. I found that if I ran all 4 cores at max speed, the temp would go up to about 85 or so though.
Since the GPU doesn't get very hot even running CUDA stuff on it, I think the problem is with the CPU heatsink/fan rather than the case as a whole. I really don't know though. But acting on that suspicion I redid the thermal grease on the CPU and it helped for a little.
It's always stayed high though, and it seems like the CPU fan fills up with dust pretty fast. Over time it's gotten worse and I've seen temperatures in the 90s.
So do I need to get a custom CPU cooler? Do you think I need more than one fan on the case, or that the case has bad ventilation for other reasons? Do I just need to clean my CPU fan really often (which seems kind of weird since laptops can live forever without being opened up)? Are there other factors besides the thermal grease, quantity of fans, etc. that I need to be considering? Do you think libsensors/the sensors applet is accurate if I haven't taken any steps to configure it explicitly?

---

### Post by TitanusEramius on 2009-12-07
Hey stair

Try to take a look at this:
[http://www.theschierers.net/blog/wp-content/uploads/2009/07/case_airflow.jpg](http://www.theschierers.net/blog/wp-content/uploads/2009/07/case_airflow.jpg)

Generally i would say the temperature in the tower is no problem as long as it stays below 40-45 celcius, but this also depends on the number of harddisk drives and so on.

In the case of your cpu i would recommend using some sort of custom cooler, i use one that blows the air out back and my cpu has never been over 50 celcius. Maybee something like this:
[http://www.hometheatrepc.com.au/images/cnps7000cu-b1.gif](http://www.hometheatrepc.com.au/images/cnps7000cu-b1.gif)
But the size and model depends on you needs, and offcourse, how much money you will use for cooling. I used around 50$ in Denmark and that gave me plenty of cooling.

You also have to remember that your desktop pc stands on the floor while you have the laptop on the table, i normally clean my tower out once a year, just before the summer starts, but this depends on how "dusty" it gets.

Good luck
Titanus

---

