---
title: "Two conky questions"
date: 2009-06-03
forum: General Help
---

### Post by Lockheed on 2009-06-03
I spent last two days setting up conky and it works pretty well.
However, there are to things I cannot seem to find a solution for.

1. How to make conky display my cpu voltage?
2. I have network down/up graphs but I also want it to show 3 or 4 most active network apps and how many kb/s they are generating. Is it possible with conky?

---

### Post by pauna on 2009-06-03
> **Lockheed said:**
> I spent last two days setting up conky and it works pretty well.
However, there are to things I cannot seem to find a solution for.

1. How to make conky display my cpu voltage?
2. I have network down/up graphs but I also want it to show 3 or 4 most active network apps and how many kb/s they are generating. Is it possible with conky?

I don't think conky has built-in capabilities for either. However, if you can get the info from a shell script, you can get conky to display output from it with ```
exec
``` or its variants (execp, especially execpi).

For the voltage info, you probably need lm_sensors or something like that to get the voltage information (unless you already have a toolset specific for you laptop, for example). Somewhat dated discussion can be found in [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by Lockheed on 2009-06-03
I know nothing about programs displaying info about programs' network actigvity.

As for the voltages, I do have lm-sensors installed any my conky is displaying CPU temperature. However, I don't know how to get Voltage.

I also have cpupowerd which I am using for undervolting.
If I type "sudo cpupowerd -s" it will display this:
```
$ sudo cpupowerd -s
cpupowerd 0.2.1 written by Markus Strobl.
WARNING: This program could cause damage to your Hardware!
Vendor                      : AMD
Family                      : K8
Model                       : 4
  Mastercpuid               : 0
    Affected cpuids         : 0 1
    Current voltage (VID)   : 0.9000 V (26)
    Current frequency (FID) : 1600 MHz (8)
    Supported frequencies   : 800 1600 MHz

```

Can this info be read by conky?

---

### Post by Lockheed on 2009-06-03
I found this variable in conky 

**voltage_v**

but when I introduce it into my config, I get this error:
```
Conky: Failed to access '/sys/devices/system/cpu/cpu0/cpufreq/scaling_voltages' at get_voltage(): No such file or directory

```

---

### Post by Lockheed on 2009-06-04
Bump

---

### Post by Celauran on 2009-06-04
You could try using conky's exec to run the command, or create a script and have conky's exec call the script.

---

### Post by Lockheed on 2009-06-05
Is there any HOWTO for it?

---

### Post by pauna on 2009-06-05
> **Lockheed said:**
> 
I also have cpupowerd which I am using for undervolting.
If I type "sudo cpupowerd -s" it will display this:
```
$ sudo cpupowerd -s
cpupowerd 0.2.1 written by Markus Strobl.
WARNING: This program could cause damage to your Hardware!
Vendor                      : AMD
Family                      : K8
Model                       : 4
  Mastercpuid               : 0
    Affected cpuids         : 0 1
    Current voltage (VID)   : 0.9000 V (26)
    Current frequency (FID) : 1600 MHz (8)
    Supported frequencies   : 800 1600 MHz

```

Can this info be read by conky?

Try something like:

```

${execi 1800 cpupowerd -s | grep VID | cut -f2 -d:}

```

That takes your command output, selects the line which talks about voltage and outputs everything after the semicolon. If cpupowerd requires root privs (i.e. sudo) to run you may have to run conky with sudo.

More script examples at [http://www.64bitjungle.com/tech/conky-dual-core-processors-in-conkyrc/](http://www.64bitjungle.com/tech/conky-dual-core-processors-in-conkyrc/)

---

### Post by Lockheed on 2009-06-06
Thanks. This is almost working. However, when conky's displayed CPU frequency changes, voltages doesn't and stays at the same level as when the command was first called.

Another thing - right now conky is starting during system startup. How do I set it to start with sudo?

Also, just neatpicking, can I remove everything what's after V in this line?

---

### Post by Lockheed on 2009-06-08
bump

---

