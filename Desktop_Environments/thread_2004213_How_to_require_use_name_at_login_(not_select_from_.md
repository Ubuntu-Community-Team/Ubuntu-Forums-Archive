---
title: "How to require use name at login (not select from list)"
date: 2012-06-15
forum: Desktop Environments
---

### Post by taylorkh on 2012-06-15
Ubuntu 12.04 running gnome-session-fallback. 

I would like to require full credentials at login. That is, to require the use to supply username and password. I was able to do this in 10.04.  I think it was called "simple greeter" or something like that. I have a script which enabled it. Of course, does not work in 12.04 with Unity, Gnome 3 etc.

Can anyone provide me with some guidance?  I have searched around but have not come up with anything. Perhaps I am not searching for the correct magic words.

TIA,

Ken

---

### Post by kanikilu on 2012-06-15
Are you still using LightDM? If so, just add the the **greeter-hide-users=true** option to the conf file: ```
sudo sh -c 'echo "greeter-hide-users=true" >> /etc/lightdm/lightdm.conf'
```

---

### Post by taylorkh on 2012-06-15
Thanks kanikilu, > Are you still using LightDM?I have no idea but I guess I am. I tried your suggestion and logged out and still had the names. I then rebooted and the names are gone :biggrin:

Thank you so much!!! Another problem bites the dust.

Ken

---

