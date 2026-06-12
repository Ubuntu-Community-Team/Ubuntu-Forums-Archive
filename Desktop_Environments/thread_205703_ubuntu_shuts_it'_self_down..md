---
title: "ubuntu shuts it' self down."
date: 2006-06-28
forum: Desktop Environments
---

### Post by ghettohacker on 2006-06-28
ubuntu 5.10, and ubuntu6.06 both shut them self down properly when run on my emachine t2882 machine.  it meets all requirements, but does not operate properly.  after the machine has been on for a while, it will shut its self down, bringing up a black screen with the normal logout message and then the pc powers off.  i've installed the default version of ubuntu 6.06, and 5.10 as well as xubuntu 6.06, and ubuntu 6.06 server.  same error with all of them.  the ubuntu dapper LiveCD's however run fine on my pc as i tested them for about 4 hours last night.  windows xp home also runs fine with no problems.  i was told to check my bios settings for somthing that would power the pc down if it got too hot, there is no setting for this, although there is a setting to select harddrive type, "'DOS', or 'OTHER'". ive tried both settings with the same results.  i would really like to get ubuntu running on my other pc, as it is the main OS for this pc and i am extremely happy with it.

---

### Post by kzutter on 2006-06-28
Two thoughts:

1. Emachines are notorious for bad power supply fans - make sure yours is blowing.
(Although this should cause it to fail on Windows)

2. A problem with acpi - kill the acpid daemon and see if it is better
sudo /etc/init.d/acpid stop

---

### Post by ghettohacker on 2006-06-29
incredible.  i've been searching for a solution for about 3 days now.  last night after reading your post, i fired up my other pc, killed the acpi daemon, and it was still running this morning when i woke up!  i think this is a record for uptime with ubuntu on that pc :)  

anywho, can anyone tell me what acpi is and how to make it stop shutting my pc down, or is there somthing more i should do to keep it from running perminatly, or to fix it?

---

### Post by kzutter on 2006-06-29
ACPI - Advanced Configuration & Power Interface

ACPI is largely responsible for power management, esp useful for laptops.

I have never had a problem with it so I don't have any first hand knowledge about troubleshooting, but others have. IF it works fine without the daemon running, then you may think about turning it off permanently.

Anyway, now that you what is the main unit to looking at you can troubleshoot it to your heart's content!

Have Fun!
-Ken

---

### Post by ghettohacker on 2006-06-30
yeah, i appriciate your help greatly :)

---

