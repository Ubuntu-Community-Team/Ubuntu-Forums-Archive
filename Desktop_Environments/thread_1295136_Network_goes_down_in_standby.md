---
title: "Network goes down in standby"
date: 2009-10-19
forum: Desktop Environments
---

### Post by finnen on 2009-10-19
Hello

I have a problem with my desktop. I use it as a NAT between my 3G USB-stick and my home W-Lan. Everything works fine as long as I use the desktop, but when I leave it idle for a while, it goes into standby. Apparently the network connection goes down when in standby, because the internet connection is lost on my laptop when that happens.

I can't find anything in the power management menu to help me, what can I do to prevent this from happening? I would prefer to be able to put the monitor and drives in standby, but keep the network working, but just disabling standby mode is ok too.

Some system facts:

Ubuntu 9.04
Pentium 4, 3 GHz dual core
1 GB memory
3G modem: Huawei E180

Thanks for any help

---

### Post by ajgreeny on 2009-10-19
This may or may not help, but give it a try.

WIRELESS AFTER SUSPEND.

 In /etc/default/acpi-support there is a lot of things you can tweak. Notably what services are killed and restarted on suspend/hibernate.

Find the following line after opening this file (e.g. Alt+F2, and enter gksudo gedit /etc/default/acpi-support):

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES=""

Change STOP_SERVICES to read:

STOP_SERVICES="networking"

Save the changes and close. With any luck this will fix the problem. What this will do is kill the networking service when you suspend/hibernate but also restart it afresh when you resume

---

### Post by finnen on 2009-10-19
Thanks for the help, but my problem is not with suspend/hibernate, but standby (i.e computer still running, but screen, drives etc. shut down). Is there a way to disable standby?

---

