---
title: "GNOME: Change cpufreq govenor on all processors"
date: 2007-12-01
forum: Desktop Environments
---

### Post by charles_elwood on 2007-12-01
Using the appropriate KDE applet (whose name I have forgotten) I can easliy convince all processors on my system to use whichever cpufreq governor I wish. Using gnome the only way I can do it is to have multiple instances of *CPU Frequency Scaling Monitor, *one for each cpu, or make appropriate use of cpufreq-selector -c.

What I want to be able to do is easily set all cpus to use the performance govenor (ondemand and jack don't get on), and have some kind of visual reminder that i've done this, so I caqn change back when I'm done.

Any ideas?

---

### Post by didier on 2007-12-01
for instant results do the following
sudo cpufreq-selector -g performance

to keep changes after a reboot for a laptop 
vi ~/.gconf/apps/gnome-power-manager/cpufreq/%gconf.xml
change the stringvalue from ondemand to performance

<?xml version="1.0"?>
<gconf>
        <entry name="policy_battery" mtime="1196433352" type="string">
                <stringvalue>performance</stringvalue>
        </entry>
        <entry name="policy_ac" mtime="1196433352" type="string">
                <stringvalue>performance</stringvalue>
        </entry>
</gconf>

and for a desktop its the same procedure but the location has changed
 ~/.gconf/apps/gnome-power-manager/%gconf.xml

---

### Post by charles_elwood on 2007-12-03
Thanks for the speedy response, but you've missed the sticking point.

On bootup, CPU0 and CPU1 are both using ondemand. (For the most part this is the desired behaviour)

$ sudo cpufreq-selector -g performance
Only sets the governor for CPU0 so I need to
$ sudo cpufreq-slector -c 1 -g performance

and when I'm done using whichever apps don't play well with the ondemand govenor, I have to either prod 2 instances of CPU Frequency Scaling Monitor or prod the command line twice. This is ugly behaviour and I'd like to find a workaround.

---

### Post by Linteg on 2007-12-03
It is a bit annoying, yes, and there's already a bug opened about it.  See [http://bugzilla.gnome.org/show_bug.cgi?id=399461](http://bugzilla.gnome.org/show_bug.cgi?id=399461)

---

