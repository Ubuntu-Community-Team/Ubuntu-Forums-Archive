---
title: "Turning off hard drive spindown?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by vtrac on 2005-04-20
When on battery power, my laptop's hard drive spins down only after a few seconds of idling time.  It's annoying to hear it spin up, and spinning up/down is the most stressful time for a harddrive.  It's not good for a drive life to constantly spin up and down.  Is there a way to turn this off?

I've edited /etc/laptop-mode/laptop-mode.conf and made the following changes:
> 
AC_HD_WITH_LM=244
AC_HD_WITHOUT_LM=244
BATT_HD=244

# Shall we adjust the power management values on the hard drives?
DO_HD_POWERMGMT=1

# Power management for HD (hdparm -B values)
AC_HDPARM_POWERMGMT_WITH_LM=255
AC_HDPARM_POWERMGMT_WITHOUT_LM=255
BATT_HDPARM_POWERMGMT=255


To try to make the spin-down time to something reasonable.  I've restarted laptop-mode, but this does not appear to do anything.

---

### Post by heimo on 2005-04-20
I'm not familiar with laptop-mode config, but hdparm will give you a hint how to do it. 'hdparm -h' to get parameters, and you'll find this interesting one:
 ```

-S   set standby (spindown) timeout

``` 
[i]
hdparm -S600 /dev/hda [/i]would change hda drives spindown time to 10 minutes. 

You could put something like this in /etc/hdparm.conf:
 ```

/dev/hda {
		mult_sect_io = 16
		write_cache = off
		dma = on
		spindown_time = 600
}

```


EDIT: I realised I didn't answer to your exact question. You can try manually changing those B values with hdparm, or you can just change the spindown time to reasonable value.

---

### Post by vtrac on 2005-04-28
I don't think changing it in hdparm's settings does much, since it only kicks in while in laptop-mode.  I have managed to turn it off manually by stopping laptop mode while on battery.

---

### Post by heimo on 2005-04-28
[QUOTE=vtrac]I don't think changing it in hdparm's settings does much, since it only kicks in while in laptop-mode. I have managed to turn it off manually by stopping laptop mode while on battery.[/QUOTE]
 
Ok. Just to clarify, did you try it and it didn't work? I'm quite sure I have used it with desktop computers without laptop-mode, but maybe laptop-mode does something to override these settings. It would be useful information for others who want to do the same thing.
 
Maybe it's about ACPI settings? I don't know.
 
Good thing though that you found a solution.

---

