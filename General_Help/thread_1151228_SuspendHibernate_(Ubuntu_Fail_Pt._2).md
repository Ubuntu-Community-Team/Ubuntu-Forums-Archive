---
title: "Suspend/Hibernate (Ubuntu Fail Pt. 2)"
date: 2009-05-06
forum: General Help
---

### Post by yaiyuy8W on 2009-05-06
I use the term Windoze because as you use the OS it slowly gets slower and slower... No matter how optimized you think it is (registry cleaner, top of the line defragger, minimal start-up, etc.)

I did not lose work with the suspend/hib problem but I could have.

Anyways onto what this thread is about. I tried to follow the ways to send in a proper Ubuntu suspend bug however the ways provided did not work. I added the no_console_[something or another] option to the end of the used kernel line and I turned fsck off and replicated the error, it said then within 3 minutes to do a dmesg > dmesg.txt I did that and the errors were not the same. I took pictures with my digital camera however the pictures were only half (readability).

So I don't know what to say, if someone lives in Sterling Heights, MI you're welcome to stop by and replicate this error for the people at Canonical.

If it helps:

Presario CQ60-210US Laptop
4GB RAM
8200M G GPU
Atheros WiFi NIC
AMD Athlon Dual-Core QL-62

Ubuntu 9.04

---

### Post by BslBryan on 2009-05-06
Hello, trizicus.  :-)

May I ask firstly for you to move this to the "general help" section?  I think overall more people will be more helpful in that area.

Anyway, what version of Ubuntu are you using?

---

### Post by Polygon on 2009-05-06
suspend and hibeernate dont work for a crazy number of reasons, a lot of them deal with the fact that the ACPI table included in your motheboard  is basically 'broken', and not written to the ACPI spec, but rather to microsoft's specification instead.

You can try looking up guides on how to decompile your DSDT table and fix the errors, and then have linux use that one instead of the built in one, but its kinda complicated....

---

### Post by yaiyuy8W on 2009-05-06
Using 9.04

---

### Post by Zer0Nin3r on 2009-05-07
> **Polygon said:**
> suspend and hibeernate dont work for a crazy number of reasons, a lot of them deal with the fact that the ACPI table included in your motheboard  is basically 'broken', and not written to the ACPI spec, but rather to microsoft's specification instead.

You can try looking up guides on how to decompile your DSDT table and fix the errors, and then have linux use that one instead of the built in one, but its kinda complicated....


Suspend used to work for me way in the 7.x versions.  Since then, it has not worked ever since.  Even with the upgrade to 9.04.  Was thinking of performing a fresh install though as I want to move onto 64bit.


**Update**

I finally managed to fix my suspend/hibernate problem.  It had to do with my WiFi driver.  My system uses the RTL8187 driver.  Came across this link: [http://ubuntuforums.org/showthread.php?t=1131084](http://ubuntuforums.org/showthread.php?t=1131084)
And from there I was able to fix the problem.

---

