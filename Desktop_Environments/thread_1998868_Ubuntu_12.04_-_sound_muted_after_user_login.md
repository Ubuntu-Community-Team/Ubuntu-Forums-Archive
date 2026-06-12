---
title: "Ubuntu 12.04 - sound muted after user login"
date: 2012-06-07
forum: Desktop Environments
---

### Post by ranger12 on 2012-06-07
Okay this just started today and I have never experienced this before with Ubuntu so I have no idea how to proceed. Yesterday all was well. I booted up my desktop and at the lightdm screen the login sound played and the sound was **not** muted. After I logged into my account I noticed the sound icon being displayed was the mute icon. I cannot unmute it because the sliders are grayed out. I have not idea why. It does it with all the user accounts - not just mine. The sound works fine at the lightdm screen but not after a user logs in. Does anyone have any idea of what I can check? There is no unmute in the sound settings that I can see.

Later:
Okay I just checked in the Sound Settings dialog - there is no longer any devices list for output on the Output tab and all the volume controls and the mute are disabled. It works fine at the lightdm login screen but is disabled when a user logs in. It was not doing this yesterday. I did not mess with any of the sound conrols yesterday either.

---

### Post by ranger12 on 2012-06-07
Okay this is weird. I was using my desktop as client for my ubuntu 12.04 server. I was exporting the users home directories from /home/* and then using autofs on the client to mount them to /home on the client. I had never had any problem until now. I remmed out the /home statement in the auto.master file and rebooted so that it would not mount the users home directory off the file server but use their home directories on the client. The sound works fine now. That is too weird. Something has gotten corrupted or changed somewhere and I have no idea how to tackle this. I guess I will avoid mounting their network home directories at /home and choose another mount point on the client. Unless it was some updates doing this. Who knows.

---

### Post by ranger12 on 2012-06-07
Boy is that weird. I discovered what the problem was and fixed. Apparently I had altered the /etc/idmapd.conf file on the server by remming out the DOMAIN line and did not do the same on the client's idmapd.conf file so when I rebooted that what was causing the grief. I had intended I guess to make the same change on the client and didn't. I uncommented it again on the server and rebooted both machines. The sound is back!! I have no idea why that would cause that but it did.

---

