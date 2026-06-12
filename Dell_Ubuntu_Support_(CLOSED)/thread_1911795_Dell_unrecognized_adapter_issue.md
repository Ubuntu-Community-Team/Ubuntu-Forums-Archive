---
title: "Dell unrecognized adapter issue"
date: 2012-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lafcina on 2012-01-19
Hi,
whenever using my (third party) universal car adapter for my Dell M4300 laptop I run on Dell unrecognized adapter issue (there is exact warning during laptop startup about it), so CPUs work all the time at 800MHz, which is annoying. The reason for this is because Dell added ID chip in adapter so you have to by it from them :-[.
I try to found some software solution in order to use this adapter on full CPU speed with Lubuntu / Ubuntu 11.10, 64bit.


I tried solution with grub (as suggested [here]("http://techmonks.net/bypassing-the-dell-unrecognized-adapter-issue")), adding GRUB_CMDLINE_LINUX=”processor.ignore_ppc=1&#8243; to /etc/default/grub, then update-grub  but it didn't solve the problem.

Then I try with cpufreq-set:

[FONT="Courier New"][COLOR="Blue"]sudo apt-get install -y cpufrequtils

modprobe cpufreq_ondemand
modprobe cpufreq_userspace

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance 

cpufreq-set -c 0 -g performance
cpufreq-set -c 1 -g performance[/COLOR]
[/FONT]
and this worked, CPU'a was at 2.40GHz speed. A little issue was it was now fixed at maximum frequency all the time. 
You can monitor this by command:

[FONT="Courier New"][COLOR="Blue"]cpufreq-info[/COLOR][/FONT]

or in the loop:

[FONT="Courier New"][COLOR="Blue"]while :; do cat /proc/cpuinfo | egrep 'GHz|MHz'; sleep 1; done[/COLOR][/FONT]

This is my result of [COLOR="Blue"][FONT="Courier New"]cpufreq-info[/FONT][/COLOR] (for one CPU only):


[FONT="Courier New"][COLOR="Blue"]cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 2.40 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.20 GHz and 2.40 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz (asserted by call to hardware).
  cpufreq stats: 2.40 GHz:4.02%, 2.40 GHz:0.30%, 2.00 GHz:0.23%, 1.60 GHz:0.12%, 1.20 GHz:20.06%, 800 MHz:75.27%  ( 2228 )
analyzing CPU 1:
...[/COLOR][/FONT]



If I set it to ondemand governor:

[FONT="Courier New"][COLOR="Blue"]cpufreq-set -c 0 -g ondemand
cpufreq-set -c 1 -g ondemand[/COLOR][/FONT]

it sticks to 800MNz no matter CPU load !

So I try different governors with or without CPU frequency limits, hoping it will not stick to minimum again, and only working solution for me was this:

[FONT="Courier New"][COLOR="Blue"]cpufreq-set -c 0 -g conservative 
cpufreq-set -c 1 -g conservative 
[/COLOR][/FONT]

Unfortunately, this workaround will not solve other problem: [COLOR="Red"]**dell notebook will refuse to charge the battery when using non-dell adapter :(, if someone have workaround for this, please share  it **[/COLOR]! 


I hope this will help you to resolve your issue ;-)

Good lack !

---

### Post by lafcina on 2012-01-19
... and there is hardware soldering solution described [here]("http://www.laptop-junction.com/toast/content/inside-dell-ac-power-adapter-mystery-revealed"), during which you extract ID chip from original Dell adapter and built it directly in laptop so it cheats BIOS to work whit any third-party adapter. I like more software solutions :)

---

