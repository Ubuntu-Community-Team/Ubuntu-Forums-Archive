---
title: "Broke my login while playing with brightness values"
date: 2016-08-18
forum: Desktop Environments
---

### Post by harshatts on 2016-08-18
I have an Asus K53SM laptop and it is running 16.04.1

The brightness would reset to maximum value on restart. So i messed up while was playing around with 
sys/intel_brightness files  acpi_video0 
the etc/grub/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
and rc.login entry acpi_video0 intel_brightness

The brightness issue after "suspend and re awake" did not get solved.

I have a black login now, I am not sure if it is low brightness or a broken login screen.

I have access to grub and ubuntu recovery mode.

I tried altering back the values using an Ubuntu CD but cannot change acpi_video0 value which is 10, my highest brightness value is 4882.

Please help me restore the settings and guide me through this.

Thanks

---

### Post by harshatts on 2016-08-18
It is ok I reinstalled it! too much of a pain troubleshooting!

---

