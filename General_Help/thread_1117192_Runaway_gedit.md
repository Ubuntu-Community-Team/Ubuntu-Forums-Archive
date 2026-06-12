---
title: "Runaway gedit"
date: 2009-04-05
forum: General Help
---

### Post by dohcdoh on 2009-04-05
Previously this computer ran Ubuntu 6.10 without a problem. A fresh install of Ubuntu 8.10 a few weeks back went well. Two days ago I did some html editing with gedit. Yesterday, I opened gedit to do some more editing. Things slowed down. Could not activate a button. I have the System Monitor Meter on the bottom panel. The processor window was filled. It was difficult to get a new Desk Top  and Terminal to kill gedit. If allowed to continue, it may have crashed everything.

I shutdown the computer and rebooted, started gedit. Gedit ran away with processor, rapidlly demanding more from the CPU. This is just starting gedit without entering a single letter or anything for editing.

I shutdown all open programs. Started gedit and ran "top" in the terminal (while I still had some control). Below is a copy.

All other programs run fine.  No other editors, TEA or Leafpad demonstrate this problem. This is being edited in TEA, and the monitor shows 11% CPU usage. History: Sometimes Nautilus slowed when searching, but that was because I had it in text mode (This text problem did not show in Ubuntu 6:10). After being switched to icons, Nautilus is fine..

     
The CPU:
Pentium III, 800MHz

From "top":
Cpu(s): 99.0%us,  1.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514096k total,   443872k used,    70224k free,    35388k buffers
Swap:   746980k total,     1772k used,   745208k free,   191356k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5882 mike      20   0 38724  19m  10m R 96.9  3.9   0:33.72 gedit              
 4780 root      20   0  106m  16m 8240 S  1.7  3.3   6:50.09 Xorg               
 1201 root      15  -5     0    0    0 S  0.7  0.0   0:07.42 scsi_eh_1          
 5407 mike      20   0 99.2m  25m  13m R  0.7  5.1   0:04.34 gnome-terminal     
 5884 mike      20   0  2412 1132  884 R  0.7  0.2   0:00.14 top                
    1 root      20   0  3056 1888  564 S  0.0  0.4   0:02.68 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd         

If I read the above right, gedit was using 96.9% of the processor within 33.72 seconds. Is that right? Any other clues found here? How do I slow down Gedit?

One more thing, I am on dialup so I may not give quick replies.

---

### Post by adult swim on 2009-04-05
this comes from the sticky on known intrepid bugs and workarounds.  it fixed my issue with gedit on 8.10

gedit loading takes very long and 100% CPU load
- Bug Report : [https://bugs.launchpad.net/ubuntu/+s...it/+bug/280411](https://bugs.launchpad.net/ubuntu/+s...it/+bug/280411)
- Workaround : [http://ubuntuforums.org/showpost.php?p=6136071&postcount=38](http://ubuntuforums.org/showpost.php?p=6136071&postcount=38)

---

### Post by dohcdoh on 2009-04-05
Thanks for the quick response. I have the links and will try the fix.

---

### Post by dohcdoh on 2009-04-05
adult swim,

That was a fix. Although I had to work fast to get to the Preferences before gedit hogged all of the processor. Unchecked "browser pane", and gedit let go of the processor. Thanks again.

---

