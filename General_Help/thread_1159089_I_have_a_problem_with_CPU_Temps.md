---
title: "I have a problem with CPU Temps"
date: 2009-05-14
forum: General Help
---

### Post by IceRayn on 2009-05-14
Whenever I attempt to read the temperature of my CPU on my 8.10 install, it always displays 40 C. I have tried reading it with cat 
/proc/acpi/thermal_zone/THRM/temperature,
SSHing in to the machine,



  My graphics card, on the other hand, which I read in nvidia-settings shows the correct temp. I'd like to know if there is a way in which I can read the temp correctly in Ubuntu. It actually works in WinBl0ws... But Windows can't change my fan speeds, so I guess it's a trade off.

On an unrelated note that might need help, my time in Ubuntu always reads a strange hour, but the correct minutes. Example: At 8:40 AM now it displays 10:40 PM. I was wondering if anyone had help with this as well.


Thank You,
IceRayn

---

### Post by Legace on 2009-05-14
Btw, you can use SpeedFan on Windows to change fan speeds..

---

### Post by BZF on 2009-05-14
[SIZE=1][COLOR=Blue]you can change the time by right clicking the time and date and choose "adjust time and date" and yes you can change the fan speeds gladly[/COLOR][/SIZE];)

---

### Post by IceRayn on 2009-05-14
I don't think you're getting what I'm saying, after I set the time and date, after a restart, it changes. And I know about SpeedFan, it doesn't work on my copy of Windows <sarcasm> Shocker! </sarcasm> The fan speeds change fine in Ubuntu, what doesn't work is reading temps. It ALWAYS shows 40 C in Ubuntu.

---

### Post by Legace on 2009-05-14
> **IceRayn said:**
> I don't think you're getting what I'm saying, after I set the time and date, after a restart, it changes. And I know about SpeedFan, it doesn't work on my copy of Windows <sarcasm> Shocker! </sarcasm> The fan speeds change fine in Ubuntu, what doesn't work is reading temps. It ALWAYS shows 40 C in Ubuntu.

Set the clock in your BIOS to the right time..

And for temp, try this: [http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)

---

### Post by IceRayn on 2009-06-04
Once I do, it always gets set to a random hour. And the temp still remains at 40 C. For example, after an SSH, I removed all the other info. 
System load:  -               Swap usage:  -     Users logged in: -
  Usage of /:   - of -   Temperature: 40 C
  Memory usage: -                Processes:   -

---

