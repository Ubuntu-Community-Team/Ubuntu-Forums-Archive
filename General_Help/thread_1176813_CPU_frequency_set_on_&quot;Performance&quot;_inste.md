---
title: "CPU frequency set on &quot;Performance&quot; instead of &quot;Ondemand&quot;"
date: 2009-06-02
forum: General Help
---

### Post by jespdj on 2009-06-02
I've noticed that on Jaunty, the frequency scaling setting on my laptop (Dell XPS M1530) about 4 out of 5 times after booting is set to "Performance" instead of "Ondemand" - I can see this with the GNOME frequency scaling applet. I have to click the applet, select "Ondemand" and enter my password to change it.

Did anybody else notice this?

Where is the default frequency scaling setting stored?

---

### Post by blueridgedog on 2009-06-02
The performance setting appears to be a common complaint:

[http://ubuntuforums.org/showthread.php?t=1129135](http://ubuntuforums.org/showthread.php?t=1129135)

---

### Post by dcstar on 2009-06-03
> **jespdj said:**
> I've noticed that on Jaunty, the frequency scaling setting on my laptop (Dell XPS M1530) about 4 out of 5 times after booting is set to "Performance" instead of "Ondemand" - I can see this with the GNOME frequency scaling applet. I have to click the applet, select "Ondemand" and enter my password to change it.

Did anybody else notice this?

Where is the default frequency scaling setting stored?

You could probably put a command in the /etc/rc.local file:

```
man cpufreq-selector
```

---

### Post by AlexanderDGreat on 2009-08-01
@[jespdj]("http://ubuntuforums.org/member.php?u=130139") - Hi, I'm using a laptop HP Pavilion dv2000 Series. I read a little bit about Ubuntu's CPU Frequency Settings.

1. Did you configure it already? Say Yes when asked to use ROOT when making changes to your Cpu Scaling Applet.
[INDENT]sudo dpkg-reconfigure gnome-applets
[/INDENT]2. My settings are stored here, change cpu0 to cpu1 - If you have 2 Cores because they have different settings.
[INDENT]/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
[/INDENT]3. To set it automatically to preferred setting on startup, these lines should be added in /etc/rc.local
[INDENT] echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
[/INDENT][INDENT] echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
[/INDENT]4. To stop it from changing to other modes after 1 minute has passed. Backup then delete afterwards, then reboot:
[INDENT]/etc/init.d/ondemand
[/INDENT]I gathered these info from these:
[http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)
[http://ubuntuforums.org/showthread.php?t=1143506](http://ubuntuforums.org/showthread.php?t=1143506)
Hope to help. :D

---

### Post by dcstar on 2009-08-01
> **AlexanderDGreat said:**
> 
......
2. My settings are stored here, change cpu0 to cpu1 - If you have 2 Cores because they have different settings.
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governors
3. To set it automatically to preferred setting on startup, these lines should be added in /etc/rc.local
 echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governors
 echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governors
.....

You **cannot** set different CPU clocking for single CPU's with multiple cores, you can only set different CPU clocking for each individual CPU.

---

### Post by AlexanderDGreat on 2009-08-02
@[dcstar]("http://ubuntuforums.org/member.php?u=7532") - Hi, thanks for that info, I'm sorry because I'm still new to Ubuntu.

What should I do? Thanks.

Oh I got it, in AMD, you don't need to add these 2 lines:

echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

Only:

echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Since "cpu0" - will change both processors...

---

