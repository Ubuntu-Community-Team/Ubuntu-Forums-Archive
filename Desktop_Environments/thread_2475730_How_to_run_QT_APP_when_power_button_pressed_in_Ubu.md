---
title: "How to run QT APP when power button pressed in Ubuntu 20.04"
date: 2022-06-06
forum: Desktop Environments
---

### Post by dzserviceit on 2022-06-06
[COLOR=#333333][FONT=&quot]Hello dear,
I Want to run my PowerOff Qt app when I press the power button, I have saying in this topic:
[FONT=Verdana]http://manpages.ubuntu.com/manpages/trusty/man8/acpid.8.html[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]my [power.sh]("http://power.sh/") in /etc/acpi/
contain :
./home/serviceit/PowerOff
any Solution Please[/FONT][/COLOR]

---

### Post by him610 on 2022-06-07
This is the example given in your topic link...
> This example will shut down your system if you press the power button.

       Create a file named /etc/acpi/events/power that contains the following:

              event=button/power
              action=/etc/acpi/power.sh "%e"

       Then create a file named /etc/acpi/power.sh that contains the following:

              /sbin/shutdown -h now "Power button pressed"

       Now,  when  acpid  is  running,  a  press  of  the  power  button  will  cause the rule in
       /etc/acpi/events/power to trigger the script in /etc/acpi/power.sh.  The script will  then
       shut down the system.
Why not use the the example?

---

