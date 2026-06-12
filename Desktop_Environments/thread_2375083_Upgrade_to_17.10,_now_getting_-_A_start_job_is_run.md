---
title: "Upgrade to 17.10, now getting - A start job is running for Hold"
date: 2017-10-21
forum: Desktop Environments
---

### Post by spliton2102 on 2017-10-21
Hi All,

Hoping for some help please. My system will boot quite happily and then after some hours, suddenly receive a SIGINT to restart, at which point it goes into nose dive and I see a message saying 
                   (1/2)[***   ]A start job is running for Hold for boot processes to finish up(5min30/no limit)

Box then needs a reboot to come back to life. I have just upgraded 17.04 to 17.10 - Internet searches suggest it is a GDM problem often associated with Nvidia devices (which I don't use). 
I do connect my system to my LG TV via HDMI and see a time correlation between when I switch to the HDMI channel that the system is connected to, but it's weird to think that changing channel 
on my TV could trigger a SIGINT

I see loads of GTK errors in my syslog, but have zero idea what they mean

I have attached syslog and output from HardInfo below...any insight would be great - 

thanks

---

### Post by mc4man on 2017-10-21
If not already try using an xorg session for "some hours" or more & see if you get this crash
(- the systemd hang on a no limit stop job isn't that important compared to the crash

---

### Post by spliton2102 on 2017-10-23
> **mc4man said:**
> If not already try using an xorg session for "some hours" or more & see if you get this crash
(- the systemd hang on a no limit stop job isn't that important compared to the crash

Thanks for the reply, you are correct that it's the crash that is most significant. I am therefore closing this thread and starting a new correctly titled one.

---

