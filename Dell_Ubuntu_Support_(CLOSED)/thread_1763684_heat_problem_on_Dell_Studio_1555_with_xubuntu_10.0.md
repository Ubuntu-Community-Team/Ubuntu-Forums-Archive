---
title: "heat problem on Dell Studio 1555 with xubuntu 10.04"
date: 2011-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by campino on 2011-05-20
hello, 

I have a Dell Studio 1555 with xubuntu 10.04 on it. Unfortunately, it becomes very hot when it is full loaded. 

Maybe 10 minutes ago, lm-sensors says, the cpu temperature was 80°C (176°F, for those who are used to that unit). I had a look at acpi -V and it says, that all the TZ were 0°C (which is impossible unless I were somewhere in the perpetual ice). I didn't say anything about fan speed, but I hear that fans are at the lowest level. 

So I restarted my computer and when the Bootloader appeared, I heard the fans rising. When xubuntu was started, cpu temp was about 70°C, it was 40°C ten minutes later, when the fans go back to normal speed. 
That didn't happen for the first time. In fact, I am dealing with heat problems for two weeks. The laptop went off because it was to hot at this point in time. 

acpi -V now tells me about temperatures, which are believable and as fas  as I know, normal. It still didn't talk about any fans. Even lm-sensors  and sensors-detect couldn't find out about fan speed. /proc/acpi/fan is  empty. It is, as if there were no fan speed sensors (but BIOS shows  that information, so I guess, there is one). 

Is there any configuration which could be wrong or any tool, which could be missing (or solve the problem, if I install it?) At least something to read cpu fan speed? 

There is a hardware diagnostics tool at Dell homepage. I've downloaded and run it, it says, my fans are okay. I've even installed the newest BIOS Update. And I found, there were problems with the radeon- driver causing heat problems. That's not the problem here, because I am using fglrx. 

Thanks in advance, 
campino

---

### Post by mörgæs on 2011-05-21
Hi, welcome to the fora.

Does it also run hot in a live boot of Xubuntu 10.10 or 11.04?

---

### Post by campino on 2011-05-22
mhh...any idea how to get it to full load on the live system? All I managed was 27% by watching a video. There seems to be almost nothing on that system. Maybe I should write a python script to calculate pi (or something like that).

---

