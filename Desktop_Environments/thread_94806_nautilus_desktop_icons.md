---
title: "nautilus desktop icons"
date: 2005-11-24
forum: Desktop Environments
---

### Post by pte on 2005-11-24
Hi!

Whenever I mount my partions under some other directory then /media/xxx no icons appear on the desktop. How can I mount my partitions outside of /media and still have icons on the desktop.

thanks,
pieter

---

### Post by DonPachi on 2005-11-25
Sorry I don't have an answer to your question.  I have only another question which falls in line with what you are asking.

Is there any way to mount a disk under /media/ and have it appear in the "Places" menu under gnome, but *not* appear on the desktop?  Should I mount it outside of /media/ and somehow add it to the places menu?

Any insight into how this all ties together would be appreciated.

---

### Post by Canuckelhead on 2005-11-25
DON... It is easy to remove desktop icons for mounted drives...
unter system tools run the configuration editor... then under apps find nautilus... expand nautilus and then expand desktop you can then uncheck "volumes visible " and the icons will no longer appear on your desktop...

---

### Post by Canuckelhead on 2005-11-25
The answer to the original question is that you should right click on the desktop and create a launcher..  you then have some options... have it behave as a "link" 
then in the "URL" portion you can enter the path to the volume you wish... I have tried this on my box and it worked just fine... I hope this answers the orig. question!
In other words you will need to make a link to the new volume on your desktop manually.  Should be bretty easy...  If you are unsure of the path to the volume you can use the System/Administration/Disks option...

Good luck

---

### Post by heart_reaver on 2005-11-25
One more thing i like to add is u can add custom icon for that by clicking on icon button. ;) 

It would be good to modify ur /etc/fstab file. Make it to mout the drives u wish to mount automaticly instead of mounting manually. for help

[www.ubuntuforms.org](www.ubuntuforms.org)

_________________
[COLOR="Orange"]GNOME  = SIMPLE && CUSTOMIZALE && SIMPLE [/COLOR]

---

### Post by pte on 2005-11-25
Hi!

I solved my problem by adding the option 'user' to some partitions in my fstab. Not the icons do show up on the desktop, although the exact rules of nautilus are not clear to me. Perhaps it is a good idea to add an option to the Administration->Disks tool to handle this.

bye,
pieter

---

