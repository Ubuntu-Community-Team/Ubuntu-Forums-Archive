---
title: "realplayer"
date: 2005-05-30
forum: Desktop Environments
---

### Post by pau on 2005-05-30
Hi,

I am trying to install realplayer in my centrino fujitsu siemens ubuntu hoary box but there's something that is not working...
I downloaded the file from [http://www.real.com/linux/](http://www.real.com/linux/) and did

```
 chmod u+x RealPlayer10GOLD.bin       
 sudo ./RealPlayer10GOLD.bin
```

I chose  /opt/realplayer as path and I got no errors during installation. Now I have an icon in the gnome menu but that's all... reaplayer is not lauching... From the gnome-terminal neither... I said yes to creating symbolic links, and let it use the default directory.

That's very important for me because I live abroad and I want my child to listen to radio, so that he also hears my mother language... HELP!  ](*,)

---

### Post by bored2k on 2005-05-30
If you go to your System Monitor (Applications > System Tools > Sys. Monitor), its probably running.

Try disablind sound services at startup (System > Pref. > Sound)

---

### Post by mohaham on 2005-05-30
you may have to edit /etc/esound/esd.conf  file
to change auto_spawn=0  to auto_spawn=1

here's  my esd.conf file:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100

---

