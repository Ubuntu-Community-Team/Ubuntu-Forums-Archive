---
title: "Has the load cycle problem for laptops been fixed?"
date: 2009-03-07
forum: General Help
---

### Post by ispyamoose on 2009-03-07
I gave Ubuntu a whirl on my Dell laptop a few months ago, but I was concerned with the load cycle bug. Does anyone know if this issue has been fixed? If so, I may be coming back to Ubuntu.

Thanks.

---

### Post by ispyamoose on 2009-03-07
My laptop model is a Dell Vostro 1500, if that helps anything.

---

### Post by davetv on 2009-03-07
I believe that this issue is fixed in the next release (Jaunty) in April. I fixed the problem on my own laptop (Acer 3623) by creating a shell script called 99-hdd-fix.sh and putting it in /etc/acpi/start.d , /etc/acpi/resume.d and /etc/acpi/suspend.d

Make sure that you make the shell script executable before copying it to the directories above using "sudo chmod a+x 99-hdd-fix.sh"

#!/bin/sh
hdparm -B 255 /dev/sda

I'm not sure exactly what this does (googled it 18 months ago) but it works.

---

### Post by ispyamoose on 2009-03-08
> **davetv said:**
> I believe that this issue is fixed in the next release (Jaunty) in April. I fixed the problem on my own laptop (Acer 3623) by creating a shell script called 99-hdd-fix.sh and putting it in /etc/acpi/start.d , /etc/acpi/resume.d and /etc/acpi/suspend.d

Make sure that you make the shell script executable before copying it to the directories above using "sudo chmod a+x 99-hdd-fix.sh"

#!/bin/sh
hdparm -B 255 /dev/sda

I'm not sure exactly what this does (googled it 18 months ago) but it works.

I really hope that the issue is resolved, like you say that it might.

---

