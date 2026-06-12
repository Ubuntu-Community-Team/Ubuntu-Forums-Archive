---
title: "invalid hostname and Intel® 945GMS Chipset.."
date: 2009-05-11
forum: General Help
---

### Post by vikativehkleja on 2009-05-11
hi!
I tried to change my computer name for closed network, but it wont allow me to use "3_1_jaan" as a name. Is there any way to force it to use it? And im getting awfully low video performance with my dell lat. d430 with Intel® 945GMS chipset. 
If anyone could help me i would be thankful. :)

---

### Post by aksheyjawa on 2009-05-11
What is the output of this command on your machine?
```
lspci -nn | grep VGA
```

---

### Post by vikativehkleja on 2009-05-11
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

---

### Post by aksheyjawa on 2009-05-13
Sorry for a late response, I am new to this forum so could not keep a track of this thread.
Hope you have figured out the problem(with the graphics card). If you have not then let me tell you that the problem is with jaunty's support for intel graphics card. I also had a similar problem and putting the following lines in xorg.conf worked for me- 

```
Section "Device"
        Identifier    "Configured Video Device"
        # ...
        Option        "AccelMethod" "uxa"
EndSection
```

Source:
1) [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
2) [http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html) 


If the above thing does not work for you then you can try this option-
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

