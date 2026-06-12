---
title: "Problem with  Nvidia Driver on feisty"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by averino on 2007-05-23
Hi and sorry for my eng, i use feisty on a dv2164 (Hp laptop that has a "Nvidia Geforce 6150 Go") and i'm trying to enable the "Desktop effect" but i see mess. box "Desktop effects could not be be enabled". 

then... i'm  following this "how to" 
[http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)
but at the step 1, when i click on "Restricted Drivers Manager" i see this mess. box. "Your Hardware does not need any restricted drivers".
I tryed with envy, but at the reboot i see a blu screen and i have to edit the xorg.conf file to restore the ol driver "nv".

Help me please.

Thank you very much.

PS again, Sorry for my eng.

---

### Post by Kobalt on 2007-05-23
If the Restricted Drivers Manager tells you that you don't need a driver it's maybe because it's already installed (search Synaptic for nvidia-glx) but maybe it's not enabled (search your xorg.conf, you should use "nvidia" as a driver instead of "nv").

---

