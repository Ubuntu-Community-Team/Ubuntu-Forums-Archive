---
title: "New! :) No sound and dual monitor support?"
date: 2009-03-18
forum: General Help
---

### Post by SeeonX on 2009-03-18
Hello! Thanks for taking the time to review my post! 

I have searched for both of these topics but seem to be having an issue finding any articles or HOWtos on my exact issues. 

I have two issues first I can't get my Creative Blaster X-fi Titanium PCI express to work at all. No sound in anyway shape or form with any programs. 
My second issue is with NVIDIA Driver Version 177.82 and my dual monitors. I can't seem to just simply have my second monitor be and extension to my first one. If I try to drag a window to the second monitor I switch over to the second desktop on the first monitor... 0_o

If you guys have any insight or links that can lead me in the right direction that would be great! 

Thank you very much for taking the time to read this! I'm going to still search if I find anything I'll let you all know. :)

---

### Post by psablo on 2009-03-19
Have you played with the nvidia settings?
try opening a terminal and type:
gksudo nvidia-settings
then configure your 2nd monitor to "TwinView" and adjust the "Position"

---

### Post by miegiel on 2009-03-19
Some stuff to try if you have no sound :

```
lspci
```
Verify that your soundcard is in the list, if it's not either your PC didn't see it during boot or ubuntu has no drivers installed for it.

If it's a card try sticking it in a different slot on your motherboard and verify if there is a linux driver for your card. [http://www.linuxquestions.org/hcl](http://www.linuxquestions.org/hcl) is a good place to start i assume :)

If your card is listed by lspci, than go to "System > Preferences > Volume control" to see if your sound might be muted. Under "Edit > Preferences" you can select channels that are hidden by default.

You can find more to read, including troubleshoot suggestions, at [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by SeeonX on 2009-03-19
Thanks for your suggestions! I will follow up with them to night and let you all know how they worked! :popcorn:

---

### Post by SeeonX on 2009-03-20
> **psablo said:**
> Have you played with the nvidia settings?
try opening a terminal and type:
gksudo nvidia-settings
then configure your 2nd monitor to "TwinView" and adjust the "Position"

 This worked perfectly! 


The lspci command is also very important!

The computer is not picking up my creative sound card at all but is picking up my:

0:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

I plugged my speakers in and it worked perfectly fine. I'm not even going to try to use the creative card. I couldn't tell any difference with it even on Vista.. -_-

Thank you both very much! I hope this info helps others as well.

---

