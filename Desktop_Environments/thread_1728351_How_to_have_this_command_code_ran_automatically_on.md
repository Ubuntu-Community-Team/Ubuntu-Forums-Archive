---
title: "How to have this command code ran automatically on startup"
date: 2011-04-13
forum: Desktop Environments
---

### Post by ccookie66 on 2011-04-13
Hello, I have a problem with my USB port, when I plug a USB drive into the port, nothing happens. Well, I fixed it (thanks to this forum =D>) but I have to put this code in every time the computer restarts to have the USB ports work: 
[COLOR=Black][COLOR=#7A0874]**cd**[/COLOR] [COLOR=#000000]**/**[/COLOR]sys[COLOR=#000000]**/**[/COLOR]bus[COLOR=#000000]**/**[/COLOR]pci[COLOR=#000000]**/**[/COLOR]drivers[COLOR=#000000]**/**[/COLOR]ehci_hcd[COLOR=#000000]**/**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**sh**[/COLOR] [COLOR=#660033]-c[/COLOR] [/COLOR][COLOR=#FF0000][COLOR=Black]'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'

Is there a way to make it work automatically when the computer boots up? 
Thanks! 
[/COLOR][/COLOR]

---

### Post by Krytarik on 2011-04-13
I would put it into "/etc/rc.local", like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind

exit 0
```Notes:
- I combined both commands into one.
- You don't need to use "sudo" because "rc.local" is already run as root through the boot process.

---

### Post by ccookie66 on 2011-04-13
> **Krytarik said:**
> I would put it into "/etc/rc.local", like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind

exit 0
```Notes:
- I combined both commands into one.
- You don't need to use "sudo" because "rc.local" is already run as root through the boot process.

I'm sorry, I don't really know what to do.... :confused:

---

### Post by Krytarik on 2011-04-13
> **ccookie66 said:**
> I'm sorry, I don't really know what to do.... :confused:
Just open the file for editing -with root access- with this command:
```
gksu gedit /etc/rc.local
```
- copy&paste the command into it, the right position
- save/quit

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ccookie66 on 2011-04-13
> **Krytarik said:**
> Just open the file for editing -with root access- with this command:
```
gksu gedit /etc/rc.local
```- copy&paste the command into it, the right position
- save/quit

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Ok, I did that, restarted but it still didn't make my USB ports work, I still have to put the codes in manually. Here is a screenshot of what I did: [ATTACH]189001[/ATTACH]

Also, here is the link where it tells me whats codes to put in: [http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

---

### Post by 3177 on 2011-04-13
you might need sudo instead of gksu.

---

### Post by Krytarik on 2011-04-13
> **ccookie66 said:**
> Ok, I did that, restarted but it still didn't make my USB ports work, I still have to put the codes in manually.
Then just try it with "sh -c", although I thought it is not necessary in this application:
```
sh -c 'find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind'
```

---

### Post by ccookie66 on 2011-04-13
> **Krytarik said:**
> Then just try it with "sh -c", although I thought it is not necessary in this application:
```
sh -c 'find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind'
```

Nope, still nothing. :(

---

### Post by Krytarik on 2011-04-13
Then try it with the full paths this time:
```
/usr/bin/find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |/bin/sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind
```

---

### Post by 3177 on 2011-04-14
wait a sec. @Krytarik, I dont think the # should be there on the first line of your first script, as there is nothing telling the script how to run? yes? no?

---

### Post by ccookie66 on 2011-04-14
Nope, still nothing.




> **3177 said:**
> wait a sec. @Krytarik, I dont think the # should be there on the first line of your first script, as there is nothing telling the script how to run? yes? no?

That maybe true, I'm just following what gets posted, not very good at terminal stuff yet...

---

### Post by Krytarik on 2011-04-14
> **ccookie66 said:**
> Nope, still nothing.
Please try running the modified command in a terminal if you have not already done so, to test it, with "sudo" of course.

If that works as usual, then I guess you can only run it through "Startup Applications", with this command:
```
gksu sh -c 'find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind'
```> **3177 said:**
> wait a sec. @Krytarik, I dont think the # should be  there on the first line of your first script, as there is nothing  telling the script how to run? yes? no?That's just the so-called crunchbang, it specifies the shell in which the commands should be run.

---

### Post by ccookie66 on 2011-04-14
> **Krytarik said:**
> Please try running the modified command in a terminal if you have not already done so, to test it, with "sudo" of course.

If that works as usual, then I guess you can only run it through "Startup Applications", with this command:
```
gksu sh -c 'find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind'
```That's just the so-called crunchbang, it specifies the shell in which the commands should be run.

No, nothing. Here is a screenshot of what I did: [ATTACH]189065[/ATTACH]

:-s

---

### Post by Krytarik on 2011-04-14
Ok, I just yet tested a similar setup. We need to modify the command a bit:
```
sh -c 'gksu find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind'
```

---

### Post by ccookie66 on 2011-04-14
> **Krytarik said:**
> Ok, I just yet tested a similar setup. We need to modify the command a bit:
```
sh -c 'gksu find /sys/bus/pci/drivers/ehci_hcd -name "0000:00:*" -print |sed "s/\.\///" >/sys/bus/pci/drivers/ehci_hcd/unbind'
```

Wow, before you replied, I thought maybe it would be fixed in Ubuntu 10.10, so I upgraded through the update tool, but half way through I got all these errors, and when I rebooted, Ubuntu would not boot up, it needed to recover or something. So, instead of going through all the trouble, I just reinstalled Ubuntu 10.04, and plugged my USB in, and it fired right up! :p That goes to show, everything happens for a reason! So problem solved! Thanks for helping me anyways. :D

---

