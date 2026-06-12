---
title: "Is it possible to resume from suspend using keyboard in Hardy?"
date: 2009-03-19
forum: General Help
---

### Post by sushman007 on 2009-03-19
I know this is possible in Intrepid, but since I reverted to the Hardy build, I miss this functionality.

---

### Post by sushman007 on 2009-04-01
bump

I have yet to find a solution to this... any ideas?

---

### Post by sdennie on 2009-04-01
What is the output of:

```

cat /proc/acpi/wakeup

```

My guess is that you simply don't have the keyboard set as an ACPI wakeup event.

---

### Post by sushman007 on 2009-04-01
> **sdennie said:**
> What is the output of:

```

cat /proc/acpi/wakeup

```

My guess is that you simply don't have the keyboard set as an ACPI wakeup event.

Here's what I've got, although it's Greek to me:

Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:06.0
XVR0	  S5	 disabled  pci:0000:00:0f.0
XVR1	  S5	 disabled  pci:0000:00:0e.0
XVR2	  S5	 disabled  pci:0000:00:0d.0
XVR3	  S5	 disabled  pci:0000:00:0c.0
XVR4	  S5	 disabled  pci:0000:00:0b.0
XVR5	  S5	 disabled  pci:0000:00:0a.0
UAR1	  S5	 disabled  pnp:00:08
USB0	  S4	 disabled  pci:0000:00:02.0
USB2	  S4	 disabled  pci:0000:00:02.1
AZAD	  S5	 disabled  pci:0000:00:06.1
MMAC	  S5	 disabled  pci:0000:00:08.0
MAC1	  S5	 disabled  pci:0000:00:09.0

---

### Post by sushman007 on 2009-04-07
Update: I checked out some other threads that looked at /proc/acpi/wakeup and figured out how to set my keyboard to wake from suspend.

However another question has come up--when I reboot, the system goes back to not recognizing my keyboard as a wakeup event.  I have to manually enable it again to get it to work.

Is there a way to permanently set my keyboard as a wakeup event (perhaps through a startup script or otherwise?)

---

### Post by sdennie on 2009-04-07
Yes.  Rather than set it as a startup script, you can set it as a suspend script.  See this post: [http://ubuntuforums.org/showpost.php?p=5195465&postcount=17](http://ubuntuforums.org/showpost.php?p=5195465&postcount=17)

---

### Post by sushman007 on 2009-04-07
> **sdennie said:**
> Yes.  Rather than set it as a startup script, you can set it as a suspend script.  See this post: [http://ubuntuforums.org/showpost.php?p=5195465&postcount=17](http://ubuntuforums.org/showpost.php?p=5195465&postcount=17)

Works like a charm now, thanks for all your help!

---

