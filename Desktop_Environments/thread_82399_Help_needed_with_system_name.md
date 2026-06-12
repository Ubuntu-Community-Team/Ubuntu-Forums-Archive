---
title: "Help needed with system name"
date: 2005-10-26
forum: Desktop Environments
---

### Post by vinoloco on 2005-10-26
Hi all,

Just installed the 5.10 package and made a mistake with the system name.  Now I need to change it.  Can anybody tell me where/what file I need to change to modify it?  Thanks for the help.

  -vino

---

### Post by cydizen on 2005-10-26
Hi Vino

 Okay, this should work for you:

System -> Administration -> Networking

(will ask for your password)

then you will see a small gui with network configuration options. Click on the tab called 'General'  - Now change your host name to what you want! Just a heads up, it's usually a good idea to restart X after changing a hostname.

Regards,
Bruce

---

### Post by clearnitesky on 2005-10-26
Ah you people with your GUIs! I was gonna say to edit /etc/hostname and /etc/hosts. Of course this may not be the Ubuntu way to do it...

---

### Post by vinoloco on 2005-10-26
Excellent Bruce!  

Thanks very much...

  -- vino

---

### Post by cydizen on 2005-10-26
No prob Vino.


[QUOTE=clearnitesky]Ah you people with your GUIs! I was gonna say to edit /etc/hostname and /etc/hosts. Of course this may not be the Ubuntu way to do it...[/QUOTE]

Whoa! Sure I can vi my /etc stuff all day, or create my own fstab entries and mount -t vfat /dev/sda1 /mnt/usbstick all day long, but I go with ubuntu so I don't have to. (Well since I forced out windows in the house and the wife and I share the computer, I gotta make it as easy for her to use as possible. ha ha ha)


Have a great day gents,
Bruce

---

### Post by clearnitesky on 2005-10-26
[QUOTE=cydizen]but I go with ubuntu so I don't have to[/QUOTE]

yeah, I haven't gotten used to that yet. I always leap in with the CLI before considering there may be some GUI wigdet to do it for me :)

---

### Post by Dr. Nick on 2005-10-26
EDIT
Hmm that was weird when I replied their were 0 replies I thought, Looks like I just duplicated almost word for word what I couldnt see

Great Minds think alike :)


[QUOTE=vinoloco]Hi all,

Just installed the 5.10 package and made a mistake with the system name.  Now I need to change it.  Can anybody tell me where/what file I need to change to modify it?  Thanks for the help.

  -vino[/QUOTE]

System name?

Is it called ubuntu right now?

If so open system-administration-networking and change the hostname under the general tab.

If its a different name that your trying to change post back with where the name shows up in the system so I can tell exactly which one you want to change :)

---

