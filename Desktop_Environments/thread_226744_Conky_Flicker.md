---
title: "Conky Flicker"
date: 2006-07-31
forum: Desktop Environments
---

### Post by theredmoose on 2006-07-31
Hi there, 

I am trying to get Conky (resouce monitor) working without having it flicker.  I have done my research on the net and found the following three suggestions.  However, none of them have been successful so far.  Does anyone have any suggetions?  Your help is most appreciated, thank you.

I have done the follwing, and tried to get it working after each step but no success so far:
1) double_buffer yes
>> I set the double buffer to yes in conkyrc and restarted.

2) own_window yes
>>Conky will launch in its own window but the flickering continues.

3) Updated xorg.conf file
>> I added the following lines to my /etc/X11/xorg.conf file, but no noticeable change.

Section "Module"
        Load    "bde"


Thank you.

---

### Post by 5-HT on 2006-07-31
> **theredmoose said:**
> 
Section "Module"
        Load    "bde"


Thank you.

Almost there!
Try changing ```
Load "bde"
``` to ```
Load "dbe"
```
You'll need to either restart X or reboot for the changes to take effect.

Hope that helps.

---

### Post by theredmoose on 2006-07-31
oh my...i can't believe I am so dyslexic.  I guess that is what I get trying to troubleshoot at 4am last night.   Thank you for your help.

---

