---
title: "Success: Hardy, Vostro, Wireless, Disk killer, Suspend"
date: 2008-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mdcallag on 2008-06-13
I had success after some work on a Dell Vostro 1400 with Hardy Heron. More details are [here]("http://mysqlha.blogspot.com/2008/06/ubuntu-on-dell-laptop-not-mysql.html") .

The biggest problem I (think) I was able to fix was to prevent the value of Load_Cycle_Count from growing quickly by setting ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support.

Wireless with Dell 1490 wireless works after installing b43-fwcutter.

Suspend and hibernate work after disabling screen lock.

---

### Post by Playa1313 on 2008-06-13
> **mdcallag said:**
> The biggest problem I (think) I was able to fix was to prevent the value of Load_Cycle_Count from growing quickly by setting ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support.

WOW are you serious?  I always thought it was the opposite.  Did you mess around with hdparm and the advanced power management settings at all?

---

### Post by luopio on 2008-06-15
> **Playa1313 said:**
> WOW are you serious?  I always thought it was the opposite.  Did you mess around with hdparm and the advanced power management settings at all?

That depends on your laptop-mode settings (etc/laptop-mode/laptop-mode.conf). Unfortunately the road to partial oblivion with the HDD Clicking (running m1330 on Ubuntu Studio 8.04) wasn't as easy for me.

The previously mentioned ACPI-setting didn't work. Neither did putting scripts in the ACPI-dirs (as one might expect), or using rc.local (it wouldn't help when resuming from sleep). The only working solution was putting small scripts under each *.d dir in etc/pm.

And one more tip: check that your cpu throttling is working properly (e.g. run "laptop_mode status" and see that cur frequency on both CPUs changes according to load). Laptop_mode couldn't control my other CPU and did bad job at the throttling in general. I switched to powernowd, which seems to work perfectly. It seems you'll need to restart it as well through a manual script after resuming :-P

I have to say that power management on ubuntu is a real mess :-k ...

---

