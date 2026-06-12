---
title: "muliple monitors with ATI"
date: 2005-06-06
forum: Desktop Environments
---

### Post by smittyhead on 2005-06-06
Installed Ubuntu and it sees my ATI 9600 and secondary view in the hardware list but I dont get the option in my resolution properties.  How can I get this working?

---

### Post by shakin on 2005-06-06
Backup your /etc/X11/xorg.conf file, then install the fglrx drivers with Synaptic, then run fglrxconfig. At some point fglrxconfig will ask you about multi monitor setup and you should select dual head for two separate desktops or big desktop to have your desktop span both monitors (like it does in Windows).

---

### Post by smittyhead on 2005-06-07
Thanks for the reply but I did this and tried replacing the xorg.conf with the results and tried replacing just the parts I needed but neither worked, x wouldnt come back up so I would have to got to the  backup.  Is there just a basic amount that I can replace in the config to get it working and build up from there? 

I'm new to linux and a graphics person so new to all this manual stuff but I'm determined to give it a go.  \\:D/

---

