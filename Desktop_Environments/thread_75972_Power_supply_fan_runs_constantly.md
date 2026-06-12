---
title: "Power supply fan runs constantly"
date: 2005-10-14
forum: Desktop Environments
---

### Post by JMW on 2005-10-14
New, clean install and everything works beautifully, except the power supply fan runs continuously -- making quite a lot of noise. It's a Vaio desktop PCV-RX560. Any suggestions?

---

### Post by Freddy on 2005-10-14
> New, clean install and everything works beautifully, except the power supply fan runs continuously -- making quite a lot of noise. It's a Vaio desktop PCV-RX560. Any suggestions?
It haven't before ?

---

### Post by JMW on 2005-10-14
First time I've installed Linux on this box... (Trying to move completely away from Windows)

---

### Post by Freddy on 2005-10-14
and in your former OS your psu fan didn't run all the time? How did you cool down your system?, the psu fan is essential for keeping the temp down.

If I understood you correctly it probaly was software enabled and maybe hard to get in Kubuntu, perhaps someone else will know more about this.   /// Freddan

---

### Post by JMW on 2005-10-14
The PS fan ran under the former OS, but must have worked at variable rates. It now runs in a very noticable (loud) fashion... You're right, it must be software controlled. Anyone know if this is enabled in Unbutu?

---

### Post by virtualXTC on 2006-06-05
I have a Sony PCV-RX651 on my hands with the same problem.   The fan runs continously though boot up until loged into Windows.  It then slows down or stops and only can be heard during very heavy installs.  With vairous debian based distos the fan never shuts off (she's currently running ubuntu).

I've messed around with powersaved and powernowd - neither seem to do anything.

when I try to run acpi from a shell I get:
```
# acpi
No ACPI support in kernel, or incorrect acpi_path ("/proc/acpi").

```

Checking the path:
```
# ls /proc/acpi
ls: /proc/acpi: No such file or directory

```

This is my girlfrineds computer, and latley the noise is her #1 deterent from allowing me to leave her computer linux.  She claims she hates it!

---

### Post by jrobbins on 2006-09-22
I am having the same problem on a Sony desktop VAIO RX650.  The fan runs at full speed when the BIOS starts up.  Under MS Windows the fan speed decreases, but under Ubuntu Dapper it continues to run at full speed.  I have a /proc/acpi/fan directory but there is nothing in it.   Typing the 'acpi -v' command says that there is no thermal support.

Can anyone point me in the right direction to quiet the fan?

Thanks,
jason!

---

### Post by ymeng on 2006-09-28
I have a RX 651. After being frustrated by the problem for nearly 2 years. I recently found out that Windows OS cannot control CPU fan either! Sony conjured up this utility to control the fan after OS starts up! [http://esupport.sony.com/US/perl/swu-download.pl?mdl=PCVRX651&upd_id=1530&os_id=7](http://esupport.sony.com/US/perl/swu-download.pl?mdl=PCVRX651&upd_id=1530&os_id=7)

My understanding is that the freaking Sony motherboard and/or fan are not ACPI or APM compliant!

Either Sony provides a Linux utility or they can publish their dirty fan secret, so someone can write a linux util.

So I'm still searching ...

---

### Post by zipper123 on 2006-10-18
Give this a try, it worked for me.  Thanks to post which I can't find any more. :confused: 

install package: lm-sensors

run: sensors-detect 
I answered "yes" to all of their questions

run: pwmconfig 
to set the preferences
you can try to run fancontrol at this point as root to see if it is working.

Finally add 
/usr/sbin/fancontrol &
to rc.local

---

### Post by virtualXTC on 2006-12-30
SUCESS!!!


Thank you so much!!!   Before this, my girlfriend kept rebooting to windows because of the fan noise.

---

