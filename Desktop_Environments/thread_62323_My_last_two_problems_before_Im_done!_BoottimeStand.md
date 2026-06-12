---
title: "My last two problems before Im done! Boottime/Standby"
date: 2005-09-04
forum: Desktop Environments
---

### Post by byen on 2005-09-04
Hey guys,
OK. Its been a while since ive been using Ubuntu and to be really frank with you...Im Loving it!Using Ubuntu has been nothing but pure joy!! and lemme just say thank you for helping me through the transformation phase. That done, I have two major issues that I have to fix as it has been getting me to a boiling point.

Problem1:Boot time ](*,) 
My boot time takes over 5 minutes :-( I use my laptop for school and would love to make standby/fast boot work as I have to switch the laptop off between classes and when need be have to boot up again...Being the only one in the class using Linux is cool but being 'that guy who is booting all the time'...sucks!. The problem is I have ndiswrapper configured to work with my broadcom and it starts out during boot time and gets stuck there for atleast 3 minutes (someone said it was looking for a network)(It never connects anyway..always have to de-activate wlan and reactivate it to connect  :| ). Is there anyway I can activate it after boot and not run it during boot? this would immediatly fix my boot problem if I fix this.Now the whole class knows that I am the guy with linux and the last thing i wanna do is make an impression that windows can boot faster than linux...NO WAY!

Problem 2: Standby: :-x 
Does standby even work in Ubuntu..? ive seen a ton of threads and no one seemed to get it to work....is it possible?

Please help... :roll: 
Thank you.
~byen

---

### Post by tktreload on 2005-09-04
installing initNG can take care of the boot time. I have great expiriences with initNg 0.18 but 0.19 makes trouble for my acpi on the laptop.

Otherwize you can remove the entries from init that corrospond to ndiswrapper, and start it manually.

as far as standy and hibernate i have not tried to make that work, initNG makes boots rather fast....

---

