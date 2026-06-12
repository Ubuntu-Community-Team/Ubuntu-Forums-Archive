---
title: "/dev/*/ disappearances"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Dagonus on 2005-11-28
How do i create a folder(and files) insdie /dev/ such that they will not be deleted upon restart?

---

### Post by Brent Dax on 2005-11-28
[QUOTE=Dagonus]How do i create a folder(and files) insdie /dev/ such that they will not be deleted upon restart?[/QUOTE]
/dev is for special device files, not for user data.  May I ask why you want to do this?  I'm not entirely sure it's even possible...

---

### Post by Dagonus on 2005-11-29
i'm trying to use Longrun which throttles a transmeta crusoe processor(on a TC100) to cut down on power usage and increase battery life and it expects things to be in /dev

---

### Post by Brent Dax on 2005-11-29
[QUOTE=Dagonus]i'm trying to use Longrun which throttles a transmeta crusoe processor(on a TC100) to cut down on power usage and increase battery life and it expects things to be in /dev[/QUOTE]
If you're trying to access a legitimate device file, the udev daemon should create the devices already.

The instructions on [this page](http://www2.zacharywhitley.com:8080/linux/installation/Compaq_TC-1000.php#hardware_configuration-longrun) may be of some use.

---

