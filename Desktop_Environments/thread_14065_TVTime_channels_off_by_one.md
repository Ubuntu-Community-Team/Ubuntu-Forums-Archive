---
title: "TVTime channels off by one"
date: 2005-02-04
forum: Desktop Environments
---

### Post by wmfox3 on 2005-02-04
I tried posting this in the hardware forum but did not get any answers. 

I'm experiencing what TVTime says is a common issue. Channels are off by one detuned so that they appear in black and white. TVTime solution says it's a problem with the bttv card getting set to PAL. But I'm not sure how to fix. Says:

To fix this, the tuner type must be told explicitly when loading your capture driver. For example, with the bttv driver use the following:

modprobe bttv tuner=2

You may have to first remove the bttv module if it is already loaded. To make this change automatic, in your /etc/modules.conf file, add the following line:

options bttv tuner=2

But the modules.conf file seems to suggest not making edits to that file. And even when I do add options bttv tuner=2 and reboot, it doesn't seem to work.

---

### Post by Ervin on 2005-02-16
I have the same problem. I checked dmesg and, although the card is properly detected (Leadtek TV2000 XP), the tuner type is 5. Adding "options bttv tuner=2" to any file in /etc/modprobe.d and running update-modules did not help.

Update: I created a new file, /etc/modprobe.d/bttv and added the line "options bttv card=34 tuner=2" then ran update-modules and rebooted. Problem solved.

---

### Post by ametade on 2005-02-16
Hi there,

to install my bttv card I edited the **/etc/modules** file and added the following line at the end:

```
bttv card=1 tuner=0 radio=1
```

To check wich values to use for **card**, **tuner** and **radio**, check the following website:

[http://www.tldp.org/HOWTO/BTTV-4.html#ss4.5](http://www.tldp.org/HOWTO/BTTV-4.html#ss4.5)

---

