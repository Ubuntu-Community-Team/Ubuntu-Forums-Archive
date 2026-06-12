---
title: "CPU and HDD temperature"
date: 2009-04-13
forum: General Help
---

### Post by crazyfrog1234 on 2009-04-13
Hi ! Where I can find info about CPU and HDD temperature in Ubuntu 8.04 ?

---

### Post by Arup on 2009-04-13
sudo apt-get install lm-sensors hddtemp gkrellm

hdd temp will pop up options, check all the defaults.

sudo sensors-detect

select Yes for all the options that come and in the end you have to hit enter twice, reboot.

Fire up gkrellm in your applications>system tools and in configuration select your sensors. You will have a nice read out of your system temp, hdd temp, system load etc and more.

---

### Post by sdennie on 2009-04-13
For the CPU, you can probably find the temperature with:

```

cat /proc/acpi/thermal_zone/*/temperature 

```

For the disk, you can use smartctl:

```

sudo smartctl -a /dev/sda | grep Temp

```

If you want to constantly monitor those temperatures, along with what was posted above, I recommend using sensors-applet:

```

sudo apt-get install sensors-applet

```

Then right click on your panel and add and configure the applet.

---

### Post by karthick87 on 2010-12-02
I cant see the temperature,

```
karthick@Ubuntu-desktop:~$ cat /proc/acpi/thermal_zone/*/temperature
cat: /proc/acpi/thermal_zone/*/temperature: No such file or directory

```

---

### Post by mc4man on 2010-12-02
> I cant see the temperature,
The location can be different depending on kernel or nonexistent
try browsing there or general location and see

```
cat /proc/acpi/thermal_zone/THM/temperature
```
( no :

---

### Post by karthick87 on 2010-12-02
```
karthick@Ubuntu-desktop:~$ cat /proc/acpi/thermal_zone/THM/temperature
cat: /proc/acpi/thermal_zone/THM/temperature: No such file or directory
```

---

