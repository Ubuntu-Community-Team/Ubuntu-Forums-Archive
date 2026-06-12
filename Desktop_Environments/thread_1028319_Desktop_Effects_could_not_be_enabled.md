---
title: "Desktop Effects could not be enabled"
date: 2009-01-02
forum: Desktop Environments
---

### Post by hcastellanos22 on 2009-01-02
I want to use the 3D cube and its amazing effects, but nothing happends when i use the Keys and i want also to view the desktop effects.

These are the facts:

1. **Installed:** Compizconfig manager is installd and  
   editable for 3D cube.
2. **General Setting:** "Horizontal Virtual Size" = 4
3. **Can not enable:** Preferences/Appereance/Visual effects/Extras says "Desktop effects could not be enabled". I dont know if this has to be enabled.

4. **Compiz:** compiz command gives: 

Checking for xlg:not present
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

5. **VirtualBox:** Using ubuntu on VirtualBox as guest and
   Windows XP SP3 as host.
6. System: Ubuntu 8.10 (intrepid) 
   Gnome 2.24.1
   Kernel 2.6.27.9 generic
7. **Video:** According to windows xp I use Mobile Intel(R) 915GM/GSM,910GLM Express Chipset Family 
8. "sudo apt-get install compizconfig-settings-manager" already used.


I am completely new to Ubuntu I did not know what was even the "Terminal" and its commands.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

Please help to know if can be done something to get the "Cube" working. Thank you.

---

### Post by hcastellanos22 on 2009-01-02
Additional Information>

I also tried to used the compiz-check mentioned in this forum to get additional information to solve the problem. i got this in the terminal

:~$ ./compiz-check
./compiz-check: line 892: unexpected EOF while looking for matching `"'
./compiz-check: line 893: syntax error: unexpected end of file


I followed the instructions mentioned in the webpage to download,compile and then to run the code. I do not know if is not working or is due to the same error:confused:

---

### Post by gjoellee on 2009-01-02
Have you installed a video card driver? You can install it with a program find in you System menus. It is called something with "Hardware"

---

### Post by Navarre on 2009-01-02
I would focus on getting compiz-check to work first.

With that error at 892 I think you have an incomplete compiz-check script.  I would re-download it from here [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check") there are directions for downloading and changing permissions on that page.

---

### Post by Therion on 2009-01-02
> **hcastellanos22 said:**
> 7. Video: ... Intel(R) 915GM/GSM,910GLM Express Chipset Family 
There's your problem.  You MIGHT get Compiz working under this integrated graphics chipset, but it's not going to be easy from what I've seen in the past.  I'm not sure that chipset sets aside enough video memory for Compiz or if it supports 3D Acceleration.  It's something like that that prevents it from working smoothly with Compiz without some additional effort.

I'd suggest googling your chipset (Intel 915G) +Compiz and see what you can find.

---

