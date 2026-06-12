---
title: "Not Booting :("
date: 2006-01-10
forum: Desktop Environments
---

### Post by splunge on 2006-01-10
Hi all.

I've been using kubuntu for a few days now and have found it to be great.

I have tried various distros before, but none have kept my interest and made me consider switching from windows as my primary os.

I have installed a few applications with success and even updated to the latest nvidia drivers.

My problems came when I last rebooted. It booted to the kubuntu splash screen, but then dropped down to a text version and the last line I could read was 
*starting timidity++ ALSA midi emulation

The last thing I did before I rebooting was nvidia drivers and after doing some reading I think this may be the cause......but I cant fix it!!!

I have booted into recovery mode and tried apt-get remove all nvidia components I can think of, I reinstalled an older version, I removed and ran xorg reconfigure, but I STILL cant get back to KDE.

Any ideas guys or should I just bite the bullet and reinstall.

I don't want to as I think fixing it will teach me more.

Thanks in advacne for any response.

---

### Post by Robgould on 2006-01-10
You need to edit your xorg.conf file.  There should be a backup that was made when you installed your drivers.  Find it and replace the durrent with the backup.  If there is no back up you can try to edit it manually.

---

### Post by splunge on 2006-01-10
Thanks for the heads up Rob.

I'm back in kubuntu :p 

I went to the folder and as you said there were backups.

I copied one from a couple of days ago and crossed my fingers......no good :???: 

I edited the file manually like you said and changed nvidia to nv and hey presto, we're all good again.

Thanks for the pointers mate.

---

