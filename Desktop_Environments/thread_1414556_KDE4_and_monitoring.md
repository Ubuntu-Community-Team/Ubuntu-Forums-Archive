---
title: "KDE4 and monitoring"
date: 2010-02-23
forum: Desktop Environments
---

### Post by CHaoSlayeR on 2010-02-23
Hi,

I have several issues (or just don't find the right thing) regarding KDE4 and the plasma desktop.

The first thing is that I miss the ability to just give a command line that outputs some numeric value and that value is being plotted like the system monitor or complex plotter plasmoids do.

That wish just came out of the next issues:

My second issue is that the "temperature" plasmoid should give me what my system provides. As I currently use a 2.6.33-rc8 + RV740 fix kernel with the built-in k10temp module I get the temperatures on the command line straight from sensors:
```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +40.2°C  (high = +70.0°C, crit = +79.0°C)
```

But as I learned recently I am really disappointed that KDE4 seems to use some kind of own monitoring thing That contains a lot useless things but does not benefit from improved basics:

[IMG]http://img6.imageshack.us/img6/3387/snapshot4ra.png[/IMG]

...uhm... "Device" ... yepp, whatever ... "Free Blocks" ... nice, but from where??? ... "Interrupt 32618" ... OK... 

...but wait, where the hell are things like busy/bandwidth utilization percentage of the I/O subsystem? What unit is "Read data device xxx" ???


So now I have several questions:

How do I get information about this KDE4 specific things on the command line?

Can I extend something with a little scripting or configuration?


The last thing that really struggles me is that after I upgraded to KDE 4.4 on my karmic system (using the kubuntu-ppa backports repository) all plotters stopped plotting anything and no resources where available. I have verified that it isn't some type of incompatibility with my kernel as I verified on 2.6.31-20 from karmic, 2.6.32 mainline and 2.6.33-rc8 mainline, all with the same result. The graph resource selector e.g. in complex plotter configuration was always empty. So I reverted completely to KDE 4.3 which works.


Thanx for any hints or thoughts,

C]-[aoZ

---

