---
title: "DELL studio CPU FAN problem"
date: 2010-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stavroscph on 2010-11-26
Hello,

Please I would really appreciate any help or suggestion.

I have a Dell studio 1535 with 4GB of RAM and 320GB hard drive.I am using UBUNTU 10.10 for one month ago and everything works perfect so far.The main problem that I am currently facing is the annoying sound from the fan but this is not the pragmatic issue as it is getting hot for some specific reason. Also I have to mention that Windows 7 are still running on the same machine.Under Win 7 the fan runs very quiet and increases and decreases in speed according to the CPU load as it would be expected. My BIOS update is A05.In UBUNTU when the CPU fan starts on,it stays active/warm for long periods of time until I reboot the system, regardless of the CPU temperature(currently is CPU 1:10 and CPU 2 :11.8 degrees Celsius) 

  I don't run anything really "heavy" when it gets hot. Just using some effects from the compiz utilities but this problem preexisted.

I also have GKrellm System monitor to check what is going on but nothing makes sense to me.

Thanks in advance for any help.:D
 

__________________

---

### Post by Mark76 on 2010-12-18
There was a GKrellM plugin to control the fan on Dell laptops. But like the majority of GKrellM plugins that haven't been ported to an official repository it's disappeared.

---

### Post by matt.cohenprice on 2011-01-12
I'm having the same problem. Dell Studio 1458 running Ubuntu Studio 10.10 and my motherboard fan is on high all the time. [PWMconfig]("http://manpages.ubuntu.com/manpages/karmic/man8/fancontrol.8.html") isn't working for me. I get the error:

"There are no pwm-capable sensor modules installed"

I know that the CPU isn't hot: conky puts my CPU temp (confirmed with 'sensors' command) between 27 and 30 degrees Celsius. Although when I run 'sensors-detect' it finds no sensors, so I'm a bit confused.

I'd love to not be running my fan all the time. Kills my battery and, I assume, the fan. And it's loud.

Any advice?

---

