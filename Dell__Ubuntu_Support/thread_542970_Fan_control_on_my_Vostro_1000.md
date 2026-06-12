---
title: "Fan control on my Vostro 1000"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by Solarius on 2007-09-04
I just bought a Dell Vostro 1000 laptop, and things have been going really well.

I've noticed, however, that none of the fans are running!  I checked the temperature with

erik@erik-laptop:~$ cat /proc/acpi/thermal_zone/THRM/temperature 
temperature:             40 C

but everything is scarily quiet, and there's nothing in the folder /proc/acpi/fan, which makes me wonder if Ubuntu is even seeing my cooling setup.  I want to make sure that my laptop doesn't die =(.  How can I set up fan control on this machine?

I tried to read as much as possible first, but for the record I see:

erik@erik-laptop:~$ i8kfan
-1 -1

erik@erik-laptop:~/media/music$ i8kfan 1 1
-1 -1

Thanks!

---

### Post by ubuntu.daemon on 2007-09-04
lol scary! i had that happen with mine, heres a page for u!
[http://ubuntuforums.org/showthread.php?t=338757]("http://ubuntuforums.org/showthread.php?t=338757")
follow my advice on the thread, but for info again:
main page with script
[http://www.thinkwiki.org/wiki/ACPI_f...ontrol_scripts]("http://www.thinkwiki.org/wiki/ACPI_f...ontrol_scripts")
you are going to need to chmod 750 the script when you put it in there, and you will want the debian init script.  chmod 750 that too! then get the config file, just make sure to put it all where it says and it 
shouldn't be a problem.  there are 3 altogether btw

---

### Post by Solarius on 2007-09-04
erik@erik-laptop:~/Desktop$ sudo modprobe ibm_acpi experimental=1
FATAL: Error inserting ibm_acpi (/lib/modules/2.6.20-16-generic/kernel/drivers/acpi/ibm_acpi.ko): No such device

---

### Post by ubuntu.daemon on 2007-09-04
why did you modprobe?  for startes just download the basic script, save it as tp-fancontrol then go in to that directory and
```
user@home: sudo ./tp-fancontrol
```

you should hear it start then

so JUST try the one script, no need to modprobe

---

### Post by Solarius on 2007-09-04
erik@erik-laptop:~/Desktop$ sudo ./tp-fancontrol 
grep: /proc/acpi/ibm/fan: No such file or directory
grep: /proc/acpi/ibm/fan: No such file or directory
12466: old priority 0, new priority -10
> Starting dynamic fan control
cat: /sys/block/hda/device/model: No such file or directory
> Shutting down, switching to automatic fan control
./tp-fancontrol: line 254: /proc/acpi/ibm/fan: No such file or directory


The modprobe was to show that I don't have ibm_acpi installed... or at least I didn't think that I did.

---

### Post by ubuntu.daemon on 2007-09-04
what version of ubuntu are you using? or kde for that matter?

---

### Post by Solarius on 2007-09-04
I'm using Gnome 2.18.1 and Feisty Fawn.

---

### Post by zakainsworth on 2007-09-17
@Solarius

Did you ever find a fix for this?

I am having the same problem on my new Vostro 1000 running Feisty Fawn.

---

### Post by himynameiskevin on 2007-09-28
wow, i'm not sure how long it would have taken me to notice this. looking through the vent on the left of the keyboard i can see a fan sitting there, definitely not moving. i checked earlier and it was at 55C, now it's at 45C.

tried to run that ibm script... but couldn't get it to work. anyone have any luck with this?

---

### Post by himynameiskevin on 2007-09-28
also i guess i should mention that i'm running 64-bit feisty fawn on a vostro 1000.

---

### Post by dyssident on 2008-01-04
I got the fan on my Vostro 1500 working perfectly using dellfand. See [this thread]("http://ubuntuforums.org/showthread.php?p=4069092").

---

### Post by himynameiskevin on 2008-02-12
has anybody gotten fan control working on a vostro 1000...? i've tried i8k and dellfand and neither of them are able to control the fans.. i've been limited the CPU to 800mhz to curb the temperatures for now, but it's really frustrating..

---

### Post by nugget659 on 2008-03-04
Any leads on a vostro 1000 fan fix? I am desperate to run some ubuntu on my laptop. Dellfand doesn't work for me.

---

