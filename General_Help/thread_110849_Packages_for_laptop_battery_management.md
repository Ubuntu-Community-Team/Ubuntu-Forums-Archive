---
title: "Packages for laptop battery management"
date: 2005-12-31
forum: General Help
---

### Post by healychan on 2005-12-31
Hi all,

Happy new year:KS :p :D 

I am using a samsung laptop with Ubuntu 5.10.
When I point to the battery icon on the panel, it says that "No battery present".
I guess it was because I haven't install a package to manage battery. Am I right??
Since I can't see the battery state, I don't know if it is charging or not, power left etc...

please give me some advice;)

---

### Post by jdong on 2005-12-31
Is your laptop relatively recent (ACPI-compliant)?

Issue the following commands at a command line, and post the output:

```

acpi -V

```
```

find /proc/acpi

```
```

apm

```


It seems like your laptop BIOS isn't talking to Linux properly... Some manufacturers have really weird, non-standard BIOSes that Linux can't understand, and this unfortunately looks like your system. If the manufacturer has any BIOS updates, those may help -- try applying them.

---

### Post by healychan on 2006-01-01
result of "acpi -V"
```
No ACPI support in kernel, or incorrect acpi_path ("/proc/acpi").

```


result of "find /proc/acpi"
```
find: /proc/acpi: No such file or directory

```


result of "apm"
```
On-line, battery charging: 3%

```


I modified my BIOS setting last night. There is a field call "installed OS" with 3 options "other", "WIN 95/98" and "WIN 2000/ME".
It was "WIN 2000/ME" and I changed it to "other".

After I made the change, when I point to the icon again. Things had changed.
It was 
System is running on AC power
No battery present

but now is
System is running on AC power
Unknown time (3%) until charged

However, no matter how long I charge, it is still 3%.....

---

### Post by healychan on 2006-01-03
What is the main different of acpi and apm??
How can I know which one should I use??

I took away the battery now because I am afraid of over charging it.

PLEASE give me some help!!!

---

### Post by kingsidy on 2006-01-03
i dont think it is necessary to take away the battery because when the battery is full it ll stop drawing current automatically. that is implemeted in hardware. the software just let's you know how much u have left. For example the battery meter in my laptop does not work. (acer). but even when i used the computer on battery, it still recharges until it is full and stops. the only thing is that i cannot tell how much battery life i got left when running on battery.

---

### Post by jdong on 2006-01-03
You will not overcharge your battery -- thank goodness that's controlled by the BIOS.

---

### Post by healychan on 2006-01-03
Thanks for your advice!!

Perhaps I should explain my situation a bit more.

I am not sure I am using acpi or apm, but an icon on the top right corner shows this information.
System is running on AC power
Unknown time (3%) until charged

while charging, the charging level is always 3%, but all in sudden it jump to 100% (it takes about 2 hours)

However, when I tried to run the laptop with battery, the indicator shows that only 3% left. No matter how long I charge, the battery last for about 10 minutes only.
The system will shutdown because of the low power level.

I need to get the indicator working properly before I can run with battery power.
This is very frustrated since I can not use my laptop without a power cable.

Thanks for any help!!:razz:

---

### Post by jdong on 2006-01-03
[QUOTE=healychan] No matter how long I charge, the battery last for about 10 minutes only.
The system will shutdown because of the low power level.
[/QUOTE]


(1) Did power management work correctly with another OS? This specific quote leads me to suspect more of a hardware problem than anything else. How about charging with the laptop OFF? How long does the battery last then?

You are not using ACPI (your BIOS doesn't support it), so almost all the power management is being handled by APM, which is virtually pure BIOS controlled.


Also, please post more hardware specs on the laptop.

---

### Post by healychan on 2006-01-03
[QUOTE=jdong](1) Did power management work correctly with another OS? This specific quote leads me to suspect more of a hardware problem than anything else. How about charging with the laptop OFF? How long does the battery last then?[/QUOTE]
The power management work fine with winME. I tried to charge it with laptop off, but still the same.

[QUOTE=jdong]You are not using ACPI (your BIOS doesn't support it), so almost all the power management is being handled by APM, which is virtually pure BIOS controlled.[/QUOTE]
Actully, my BIOS does support ACPI. As I said before, I modified the BIOS setting. This is what I said before.
> I modified my BIOS setting last night. There is a field call "installed OS" with 3 options "other", "WIN 95/98 ACPI" and "WIN 2000/ME ACPI".
It was "WIN 2000/ME" and I changed it to "other".

After I made the change, when I point to the icon again. Things had changed.
It was
System is running on AC power
No battery present

but now is
System is running on AC power
Unknown time (3%) until charged


[QUOTE=jdong]Also, please post more hardware specs on the laptop.[/QUOTE]
My laptop is Samsung which is quite old (about 5 years)
P3 500 MHz, 128MB RAM, 10GB harddisk.
What other information do you need???

---

### Post by jdong on 2006-01-03
Try the acpi -V command with each of the settings.

---

### Post by healychan on 2006-01-04
I changed the BIOS setting back to acpi again. I swtich on my box with ac power and battery together.

I tried this
```
acpi -s
```
and it said "Battery 1: slot empty". But the battery was there!!!!

I tried
```
acpi -a
```
and it said "AC Adapter 1: on-line". It is working fine

So the problem is the acpi working fine with ac power but it seem that could't detect my battery. Any Ideas??

---

### Post by healychan on 2006-01-04
And this is the output of acpi -V

```
No support for device type: thermal
  AC Adapter 1: on-line

```

---

