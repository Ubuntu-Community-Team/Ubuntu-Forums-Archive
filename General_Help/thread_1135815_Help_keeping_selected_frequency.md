---
title: "Help keeping selected frequency"
date: 2009-04-24
forum: General Help
---

### Post by brandon88tube on 2009-04-24
I need some help keeping the selected frequency for my laptop. Whenever I choose something other then ondemand and do a restart, it resets itself back to the default of ondemand. This is annoying changing it everytime I reboot. I would like to just keep what I had selected.

---

### Post by dcstar on 2009-04-24
> **brandon88tube said:**
> I need some help keeping the selected frequency for my laptop. Whenever I choose something other then ondemand and do a restart, it resets itself back to the default of ondemand. This is annoying changing it everytime I reboot. I would like to just keep what I had selected.

[http://ubuntuforums.org/showpost.php?p=3189740&postcount=10](http://ubuntuforums.org/showpost.php?p=3189740&postcount=10)

---

### Post by brandon88tube on 2009-04-25
> **dcstar said:**
> [http://ubuntuforums.org/showpost.php?p=3189740&postcount=10](http://ubuntuforums.org/showpost.php?p=3189740&postcount=10)

Umm, yeah that doesn't exist in Ubuntu 9.04

---

### Post by brandon88tube on 2009-04-29
Its been 5 days since someone replied to this. I need to keep the selected frequency in 9.04 and cpufreq,powernowd are no longer used in this version so the above comment has done me no good whatsoever.

---

### Post by codeseer on 2009-04-29
> **brandon88tube said:**
> Its been 5 days since someone replied to this. I need to keep the selected frequency in 9.04 and cpufreq,powernowd are no longer used in this version so the above comment has done me no good whatsoever.

Post the output:

```
cat /boot/config-[Insert Your Kernel Version] | grep -i cpufreq
```

---

### Post by brandon88tube on 2009-04-30
Here is the output ```
cat /boot/config-2.6.28-11-generic | grep -i cpufreq
CONFIG_X86_ACPI_CPUFREQ=y
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
```

---

### Post by codeseer on 2009-04-30
> **brandon88tube said:**
> Here is the output ```
cat /boot/config-2.6.28-11-generic | grep -i cpufreq
CONFIG_X86_ACPI_CPUFREQ=y
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
```

```
cat /etc/modules | grep cpufreq
```

---

### Post by brandon88tube on 2009-04-30
Nothing prints out from that command.

---

### Post by codeseer on 2009-04-30
> **brandon88tube said:**
> Nothing prints out from that command.

Try adding this:

```
acpi-cpufreq
```

...to your /etc/modules file, then do this:

```
sudo modprobe acpi-cpufreq
```

...and restart. Then try setting it again.

---

### Post by brandon88tube on 2009-04-30
What exactly am I doing here?

---

### Post by codeseer on 2009-04-30
> **brandon88tube said:**
> What exactly am I doing here?

Ensuring kernel support of scaling.

---

### Post by brandon88tube on 2009-04-30
modprobe failed with this```
FATAL: Module acpi_cpufreq not found.
```
You are aware that I am talking about 9.04 here? It doesn't come with cpufrequtils, cpufreqd or powernowd. Though the cpu frequency monitor panel object from gnome still works. Thats how I've been setting it, but like I said that won't stay.

---

### Post by codeseer on 2009-04-30
> **brandon88tube said:**
> modprobe failed with this```
FATAL: Module acpi_cpufreq not found.
```
You are aware that I am talking about 9.04 here? It doesn't come with cpufrequtils, cpufreqd or powernowd. Though the cpu frequency monitor panel object from gnome still works. Thats how I've been setting it, but like I said that won't stay.

Not sure then. I've read a few reports of that very process working in Jaunty. ACPI is enabled in your BIOS, correct?

---

### Post by brandon88tube on 2009-04-30
I have no idea. HP doesn't give me any freedom with my BIOS. I have limited options.

---

### Post by WorLord on 2009-05-05
The tool doesn't keep your choices (as I'm sure you've found out).  Ubuntu 9.04 sets the value to "ondemand" after 60 seconds of being booted.  This is done via a script called ondemand, located here:

/etc/init.d/ondemand

However, what I did, was modify line 27 from 

echo -n ondemand > $CPUFREQ

to 

echo -n performance > $CPUFREQ

and after a reboot, this has taken... my computer starts in performance mode, and stays there.  :-)

---

### Post by dcstar on 2009-05-05
> **brandon88tube said:**
> Umm, yeah that doesn't exist in Ubuntu 9.04

Gee, if you had specified what version you were using in your profile or in your post then people wouldn't have to guess, would they?

---

### Post by codeseer on 2009-05-06
> **WorLord said:**
> The tool doesn't keep your choices (as I'm sure you've found out).  Ubuntu 9.04 sets the value to "ondemand" after 60 seconds of being booted.  This is done via a script called ondemand, located here:

/etc/init.d/ondemand

However, what I did, was modify line 27 from 

echo -n ondemand > $CPUFREQ

to 

echo -n performance > $CPUFREQ

and after a reboot, this has taken... my computer starts in performance mode, and stays there.  :-)

Great discovery.

---

### Post by brandon88tube on 2009-05-07
> **dcstar said:**
> Gee, if you had specified what version you were using in your profile or in your post then people wouldn't have to guess, would they?

Yeah, you are correct so I tried to clear it up with that post.

---

### Post by brandon88tube on 2009-05-07
> **WorLord said:**
> The tool doesn't keep your choices (as I'm sure you've found out).  Ubuntu 9.04 sets the value to "ondemand" after 60 seconds of being booted.  This is done via a script called ondemand, located here:

/etc/init.d/ondemand

However, what I did, was modify line 27 from 

echo -n ondemand > $CPUFREQ

to 

echo -n performance > $CPUFREQ

and after a reboot, this has taken... my computer starts in performance mode, and stays there.  :-)

Is this really the only file? I mean what tells it to run ondemand to begin with? Couldn't we just edit the file that says run /etc/init.d/ondemand ?

---

### Post by WorLord on 2009-05-10
> **brandon88tube said:**
> Is this really the only file? I mean what tells it to run ondemand to begin with? Couldn't we just edit the file that says run /etc/init.d/ondemand ?

You probably could.

Ondemand is a startup script - it is referenced in different runlevels.  I suppose one could remove /etc/init.d/ondemand entirely, and remove the runlevel symlinks, and the whole thing would just be gone at that point.  

In fact, you probably could just delete /etc/init.d/ondemand full stop, and leave broken symlinks in your rc.x directories, and everything would still be golden.

However, one day I might want to actually have this functionality, so I opted to keep the script and symlinks there and just change the one word I need to change.  It's just a matter of preferece - I like my changes to be as low-impact and reversible as possible, and this seemed the easiest and safest thing.

---

