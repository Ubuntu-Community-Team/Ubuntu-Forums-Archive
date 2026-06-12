---
title: "Local time settting problem?"
date: 2005-11-11
forum: Desktop Environments
---

### Post by fei on 2005-11-11
After I installed Hoary on my laptop, there is one hour difference between the Ubuntu system and my windows. I have to use time synchronizing program to keep ugdate my local time setting every time I switch from Ubuntu to windows. 

Is there a way to fix the problem??

Thanks!

---

### Post by MichaelM on 2005-11-12
Try this:[QUOTE=ubuntuguide.com]**Q: How to disable system time/date from being reset to UTC (GMT)?**

   **1**. Read General Notes
   **2**.
sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS

   **3**. Find this line
...
UTC=yes
...

   **4**. Replace with the following line
UTC=no

   **5**. Save the edited file (sample)
   **6**. System -> Administration -> Time and Date
Set the correct time/date

   **7**.  sudo /etc/init.d/hwclock.sh restart[/QUOTE]

---

