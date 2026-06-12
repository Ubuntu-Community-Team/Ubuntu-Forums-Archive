---
title: "how to get back my resolution?"
date: 2011-02-27
forum: Desktop Environments
---

### Post by donpeter06 on 2011-02-27
Hi
I am using a 1400x900 resolution LCD monitor with nvidia chipset.
When i first install ubuntu 9.10 i had the correct resolution. then i installed KDE in ubuntu 10.10 after upgrading.
Then its all messed up. i cant get back my resolution no matter what all i try.
now i did a fresh istall of ubuntu 9.10 , But the resolution is stuck at 1024x768.
I tried "xrandr" but its showed this,


Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  


please do help.
My maximum resolution is 1440x900, and not what is shown in here.

---

### Post by realzippy on 2011-02-27
Do you use the nvidia driver?
If so,which one?

---

### Post by sites on 2011-02-27
System - Administration - NVIDIA X Server Settings

After you make a change to your resolution, be sure to click "Save to X Configuration File".

---

### Post by donpeter06 on 2011-02-27
I have nvidia geforce 6150 and nforce 430. 
In xsever settings there the top resolution i can choose is 1024x768.
So there is no way to do that.,
But luckily i got my resolution back. 
Now that i have restarted my sytem.
Dont know how it came back.
I have been typing commands into terminal.
Let me work out which command really did the job!!
Anyway thank you Guys!!

---

### Post by donpeter06 on 2011-04-04
All that you hav eto do is to boot from your live cd.
and restart the system after accessing the desktop.
And you are done.

---

