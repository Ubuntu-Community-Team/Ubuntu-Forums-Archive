---
title: "No W**dows settings in 'Networking'?"
date: 2005-05-20
forum: Desktop Environments
---

### Post by upekshapriya on 2005-05-20
Hi

Reading how to set up Samba

[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba)

I see a picture of the 'Network Settings' that doesn't match the one I have in Ubuntu 5.04. And I can't find anything anywhere that allows me to "Enable windows networking". (See attached pic). 

Can anyone tell me how to do this so I can start a Samba Server on Ubuntu so that Windows can see me?

Regards

Upekshapriya

---

### Post by mtron on 2005-05-20
You want to activate samba? 
sudo apt-get install samba smbfs

then System - Administration - shared folders
Create e.g. /home/public
click on properties - general windows sharing settings and here you go...

see:
[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by upekshapriya on 2005-05-20
Thanks very much mtron  :) - it's all working now. That was pretty easy.

I had seen the ubuntuguide.org advice but hadn't really understood it and was completely confused by seeing the wiki with the Warty instructions.

---

### Post by mtron on 2005-05-20
No prob  ;-)

---

