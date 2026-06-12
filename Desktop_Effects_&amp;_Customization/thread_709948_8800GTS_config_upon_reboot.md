---
title: "8800GTS config upon reboot"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by thewalrus34 on 2008-02-27
I successfully installed my nvidia 8800 gts driver from the nvidia website.  However, it is not enabled in the restricted drivers.  After enabling it and rebooting it loads to the loading screen (w/ ubuntu and the orange bar).  After completely loading that a blank screen appears with a message asking me to configure my graphics settings (the cursor is a black X btw) , i set the monitor and resolution along with the graphics card driver, i click ok, and the screen completely fades out (cursor is gone) after this nothing happens and i'm force to manually reboot. I reboot and everything loads fine however the driver is still not enabled!  In addition i tried "sudo nvidia-xconfig" and that allowed it to enable without reboot.  but when i try to enable desktop effects, it says unable to enable desktop effects (or something similar) after typing in "sudo compiz" (i think) i got the following: Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Yellow Pasque on 2008-02-28
Maybe try Envy to install the driver? 'nvidia' is on the whitelist by default, so it sounds to me like your driver isn't properly installed. If the Envy thing doesn't work, post your /etc/X11/xorg.conf and /var/log/Xorg.0.log

Also, make sure your /usr/bin/compiz is set up correctly: [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

