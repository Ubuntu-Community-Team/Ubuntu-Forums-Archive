---
title: "Help with Xgl/Beryl"
date: 2006-12-03
forum: Desktop Environments
---

### Post by towync on 2006-12-03
Hi, I'm using Kubuntu 6.10, and I've got some questions trying to get beryl to work. (Btw, do I need xgl at all since isn't aixgl installed on Edgy already?) 

Anyway, when I followed the instructions here: [http://www.biodesign.com.ar/blog/?p=23](http://www.biodesign.com.ar/blog/?p=23), my screen freezes when I type in beryl-manager command. The error log indicates that beryl-manager is trying to find xgl and nvidia, it says something similar to: xgl: absent, nvidia present, and then all hell freezes over lol.

So to get xgl, I went to [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit), but I can't find the equivalent command in KDE for: sudo gedit /etc/gdm/gdm.conf-custom, if someone knows that equivalent command that'd be great :) .

I skipped that last step because it didn't seem essential for beryl to run, and typed beryl-manager again, with the same bad result as before. (still says xgl not installed. nvidia installed) 

Could someone point me in the right direction? Thanks alot:)

---

### Post by towync on 2006-12-03
Actually here's the entire error msg after I type beryl-manager at command prompt:

Bad device, invalid or uninitialized input device 169
    major opcode: 147
    minor opcode: 3
    resource id: 0x0
Failed to open device
X Error: Bad device, invalid or uninitialized input device 169
    major opcode: 147
    minor opcode: 3
    resource id: 0x0
Failed to open device
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extention
Bad device, invalid or uninitialized input device 169
    major opcode: 147
    minor opcode: 3
    resource id: 0x0
Failed to open device
X Error: Bad device, invalid or uninitialized input device 169
    major opcode: 147
    minor opcode: 3
    resource id: 0x0
Failed to open device

From the error message, it appears that beryl can work without xgl, but is mostly concerned with beryl: No composite extention. Could someone tell me if that's true? I find in my xorg.conf file that composite extension value is "disable". 

What then is the opposite of "disable" that I should enter for the composite extension value, it's "enable" right? (Just making sure before I make the changes.)

Also I find on one install guide I should add: 

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

to end of xorg.conf "Screen" section, if someone could confirm that, that'd be great as well :) . 

In general, when I type commands like kwrite at command prompt, which would work fine, but then will also output errors like: 

Bad device, invalid or uninitialized input device 169
    major opcode: 147
    minor opcode: 3
    resource id: 0x0
Failed to open device
X Error: Bad device, invalid or uninitialized input device 169
    major opcode: 147
    minor opcode: 3
    resource id: 0x0
Failed to open device

It's just an annoyance, but I'd appreciate it if anyone could shed some light on how to get rid of these errors. Thanks so much for reading this entirely long thread, thanks in advance for any hints and help :) .

---

