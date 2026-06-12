---
title: "karmic on my laptop: Desktop effects could not be enabled?"
date: 2009-12-21
forum: Desktop Environments
---

### Post by pepe machine on 2009-12-21
hello guys, im totaly new here..

i have successfully installed karmic koala on my msi laptop. im enjoying ubuntu and planning to migrate from windows. 

i want to enable desktop effects so heres what i did. 
right click >> change desktop background >> visual effects >> normal

then a message will appear asking to enable the driver.
i clicked enable.

it loads but display the "Desktop effects could not be enable?" message 
----------------------------------------------------

i read some threads in the forums and did this.

*system >> administration >> Hardware drivers* 

then display two drivers available
[B][I]NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version 185) [Recommended[/I][/B]]

so i choose ver185 and activate

now it  displays an error message that it could not download the driver.
so i manually download it and install it from
*[http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_180.25-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_180.25-0ubuntu1_i386.deb)*

i have it installed and check if the desktop effects could be enabled.
but again, i failed. hehe..

-------------------------------------------------------------------

i tried doing a COMPIZ-CHECK heres what it displays

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C79 [GeForce 9200M G] (rev b1)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```[COLOR=Red]entering: Y, [COLOR=Black]directs me to hardware drivers.. again activating ver 185... no error message appears but it is still _disabled.._

please help me.. i really want to enable the desktop effects..
[/COLOR][/COLOR]

---

### Post by pepe machine on 2009-12-22
i have an update in my problem

after restarting, this message appears before the log-in screen appears
```

RUNNING IN LOW GRAPHICS MODE

The following error was encountered. You may need to update your confguration to solve this.

(EE) NVIDIA(0): Failed to load NVIDIA kernel module
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) Found but none have a usable configuration
```

then it give me choices
```

0 Run ubuntu in low graphics mode
0 Reconfigure graphics
0 Troubleshoot the error
0 Exit to console login
```

i chose 'run ubuntu in low graphics mode' coz i dont know what to do with the other choices.

still looking for useful threads.. fellow forumates please help me here please...!!!

---

### Post by realzippy on 2009-12-22
Try the newest driver:

[http://www.nvidia.com/object/linux_display_ia32_195.22.html](http://www.nvidia.com/object/linux_display_ia32_195.22.html)

save it to your Desktop;HowTo install:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by pepe machine on 2009-12-22
thanks... ^_^   its now working:P

---

### Post by realzippy on 2009-12-22
..so please set thread as "solved"  (threadtools),
How did you solve it?(others might be interested too..)

---

### Post by pepe machine on 2009-12-22
do some updates

system >> administration >> update manager

after updating check hardware drivers

system >> administration >> hardware drivers

choose the recommended driver

choose activate

restart.. :P

---

### Post by byStanderone on 2010-05-16
for nvidia graphics:
sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

