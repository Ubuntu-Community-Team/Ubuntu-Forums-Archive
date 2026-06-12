---
title: "How can I get higher resolutions?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Hoffmann on 2006-08-02
Hello:

I have an IBM ThinkPad laptop. I installed Ubuntu 6.06 on it, and all is working fine. After conneting my laptop to a 20" monitor, I realized that the resolution is not as good as it is on the laptop screen. 
I have tried to increase the resolution (System -> Preferences -> Screen Resolution), but all I have is:

Resolution: 1024x768
Refresh rate: -25862 Hz

I have no option to change those values. 

Could anyone tell me how to get higher resolutions in order I make my laptop work better with my new (larger) monitor? 

Thanks

---

### Post by Ramses de Norre on 2006-08-02
You'll need to add the higher resolutions in /etc/X11/xorg.conf.
Find the lines starting with "Modes" in the screen section and add the higher values to all of those lines.

---

### Post by Hoffmann on 2006-08-02
> **Ramses de Norre said:**
> You'll need to add the higher resolutions in /etc/X11/xorg.conf.
Find the lines starting with "Modes" in the screen section and add the higher values to all of those lines.

Hi Ramses,

I followed your suggestion, but nothing changes. I mean, after adding the higher values in /etc/X11/xorg.conf file, I restarted my machine. However, I didn't get any additional options for changing the screen resolution. Am I missing anything?

Thanks

---

