---
title: "Alsamixer master volume"
date: 2005-05-01
forum: Desktop Environments
---

### Post by mirtux on 2005-05-01
Hi,
   i've got a question regarding the use of alsamixer. Whenever i start up the system the master volume of the alsamixer is set up at 65%. How is possible to set it up in order to be, by default, at 85%? I cannot find the configuration file in which these infos are stored....

Thanks and regards,
MC

---

### Post by Nob on 2005-05-01
set the volumes manually, then do next:

# alsactl -f /var/lib/alsa/asound.state store
# echo alsactl -f /var/lib/alsa/asound.state restore > /etc/init.d/sound_restore
# chmod a+x /etc/init.d/sound_restore
# ln -s /etc/init.d/sound_restore /etc/rc2.d/S59sound_restore
# ln -s /etc/init.d/sound_restore /etc/rcS.d/S59sound_restore
# reboot

---

### Post by mirtux on 2005-05-01
Hi,
   thank you very much for your help, now it works just fine!. The only point i've modified is to use the nice **update-rc.d **command instead in symbolically linking the file to start at boot up
```

** update-rc.d sound_restore defaults**

``` 
Regards,
MC

---

### Post by Nob on 2005-05-01
why to do it simple way when we can do it complicated way? :D

---

