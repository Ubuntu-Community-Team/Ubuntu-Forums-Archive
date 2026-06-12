---
title: "uswsusp + kubuntu"
date: 2007-09-11
forum: Desktop Environments
---

### Post by cwj88 on 2007-09-11
I installed uswsusp on my kubuntu laptop in order to fix suspend/hibernate

I use the command 's2disk' in order to hibernate
In order to integrate this with kde power management I modified /etc/acpi/hibernate.sh to run the command 's2disk'  

hibernate is working fine, my problem is with suspend

The command that I use to suspend is 's2ram -f -p', and  I modified  /etc/acpi/sleep.sh to run that command.  When I select suspend from K > Log Out... > Suspend all I get is a blank screen, and when I move the mouse it asks me to enter a password to unlock the computer.

Does anyone know how to fix this?

Thanks

---

