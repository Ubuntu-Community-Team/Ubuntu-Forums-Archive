---
title: "gkrellm not reading sensors in Ubuntu 9.10"
date: 2009-11-26
forum: Desktop Environments
---

### Post by Mark Phelps on 2009-11-26
Been using GKrellm for years, primarily because it was easy to setup and use.

Installed Ubuntu 9.10 clean this weekend and have been going through my customization efforts, including installing and customizing gkrellm.

Got the latest version of lm-sensors (3.1.1-4) and installed it.  Ran "sudo sensors-detect". Rebooted. Ran "sensors" -- and got the same long list of readings that I see in my other Jaunty install.

Got the latest gkrellm (2.3.2-5), installed it, went to configure it (using same settings as in Jaunty) -- and noticed that it does not show any temp, fan, or voltage sensors!

My box has k8temp and it8712 sensors, and "sensors" displays the full output from both sensors -- just like it does in Jaunty.  So, it's not a sensor detection or reading problem, per se.

I tried using modprobe to remove the k8temp modules, and although the command claims to work, using modprobe to check for modules shows it still there -- even though it's no longer present in /etc/modules.

I tried removing gkrellm and reinstalling it, but that makes no difference.

Anyone expert enough with gkrellm to suggest anything I can try?

Oh, and BTW, before anyone suggests I use XSensors instead, I tried that -- and all I get is an empty window, no readings at all.

And yeah, I know about conky and have used it, but I'd like to get gkrellm working before I have to resort to digging out my old conky config files.

---

### Post by Mark Phelps on 2009-12-02
No replies?? bump ...

---

### Post by skaramanger on 2009-12-06
Greetings Mark Phelps,

I am experiencing the same problem that you are.  I searched my directory tree for i2c-core.ko and noticed that their is no kernel module for 2.6.31-16-generic kernel. However there is one the -15-generic kernel.  I'm curious why that is.  I am not sure, but I think the i2c-core module has the necessary code for fans and voltages. 
That's all I have. You have any luck at your end?

---

### Post by Mark Phelps on 2009-12-07
> **skaramanger said:**
> You have any luck at your end?

No, absolutely none.  I did notice that in Jaunty, the sensors command returns a list of values from the IT8712 sensor.  When I boot into Jaunty (same machine), gkrellm works fine.

But in Karmic, the list of values is returned from ACPI (ATK110), not the IT8712 sensor.

When I installed Karmic, I also installed the most current version of gkrellm.  So, I removed that and installed the same version I have in Jaunty.  No success.

What I have NOT yet done, due to lack of time, is remove the lm-sensors package and associated libs, and replace them with the same package and libs as in Jaunty.  Perhaps that would make a difference.

Also, I've been trying to find a forum or email address for gkrellm tech questions -- but no luck so far.

This is disappointing because I've used gkrellm for years and would hate to have to go back to hacking conky scripts because this is yet ANOTHER thing that no longer works in Karmic.

---

### Post by skaramanger on 2009-12-07
I've posted a new thread asking about i2c-core modules.  Yeah this has got me a little miffed. 
I'll post back here any news to this thread.

Later

---

### Post by pjbgravely on 2009-12-07
This is probably a problem with lm-sensors. When I run sensors-detect I get 
```

#----cut here----
# Chip drivers
f71882fg
# no driver for AMD K10 thermal sensors yet
#----cut here----

```

This worked fine in 9.04. I have no idea why the driver is no longer available. 

Paul

---

### Post by skaramanger on 2009-12-17
Any clues out there?

Bump

---

### Post by pjbgravely on 2009-12-17
While it worked before using the K8 driver it wasn't calibrated correctly, so instead of giving you wrong temperature values they decided to write a proper driver and that is what we are waiting for.

---

### Post by skaramanger on 2009-12-19
PjbGravely

I'll be waiting.

Thanks

---

