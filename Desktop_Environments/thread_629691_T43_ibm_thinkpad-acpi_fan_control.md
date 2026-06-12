---
title: "T43 ibm thinkpad-acpi fan control"
date: 2007-12-02
forum: Desktop Environments
---

### Post by Bill N. on 2007-12-02
Hello everyone, I have a clean install of Gutsy on an IBM T43 laptop and noticed that the fan is always running. I read somewhere that IBM created a program called Thinkpad-acpi that is supposed to give some control over the fan. Being the newest kid on the block, I'm not sure how to go about installing this or if that is the real answer to the fan working OT. Also does anyone know if the suspend issue has been resolved for T43"s with the ATI M300 card? So far everything I've read puts this issue with ATI's drivers. Please remember I'm real new to Linux so simple... real simple answers would be helpful. Thanks in advance. Bill N.

---

### Post by swerner on 2007-12-02
This is taken from [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR40-2681](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR40-2681), it works for an IBM R40, but will probably also work for the T43.

I suggest CPU throttling, this will reduce the heat the CPU generates.  The CPU can run at different speeds (CPU frequency scaling), however, the default configuration is such that CPU frequency scaling does not work. This will save a lot of power, and reduce the amount the fan runs. Edit /etc/modules:

```

sudo gedit /etc/modules
```

then add the follow lines to the end of the file and restart your PC:

```

# enable frequency scaling
thinkpad_apci
p4_clockmod
cpufreq_ondemand
```

Now, when you restart you will have the CPU changing frequency. To test, use the frequency scaling applet in Gnome, right click on the gnome panel and click "Add to Panel...".

Frequency scaling is great, but I find that when the frequency drops down to 200MHz there is a little bit of lag when clicking somewhere with the mouse, since the CPU sits at 200MHz for a few to many milliseconds. Others may not notice, or may not be bothered by it, but it annoys me. One way to fix this is to raise the minimum frequency to 600MHz. To do this you will need to install the cpufrequtils package :

```

sudo apt-get install cpufrequtils
```

Then you will need to run 'cpufreq-set -d 600MHz' command to set the minimum frequency. To do this at boot time add the following line to an appropiate file in the /etc/init.d/ directory :

```

cpufreq-set -d 600MHz -g ondemand
```

---

