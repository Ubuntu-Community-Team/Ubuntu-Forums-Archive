---
title: "[SOLVED] Can't disable emulation of 3 buttons"
date: 2008-12-16
forum: General Help
---

### Post by noerrorsfound on 2008-12-16
This stupid option that's useless for most people and a hindrance to gamers is still enabled by default, and there's no way to turn it off in **System | Preferences | Mouse**. In my xorg.conf I have emulate3buttons set to off/false/no but it doesn't disable the "feature". That method worked before version 8.10 of Ubuntu.

**Solution:**
[http://alientrap.org/forum/viewtopic.php?p=48471#48471](http://alientrap.org/forum/viewtopic.php?p=48471#48471)
> Add the following inside the <device> section in /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi: 
 
```

   <match key="info.capabilities" contains="input.mouse"> 
      <merge key="input.x11_driver" type="string">mouse</merge> 
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" 
             string="Linux"> 
        <merge key="input.x11_driver" type="string">evdev</merge> 
      </match> 
 
      <!-- this here is what actually disables the 3 button emulation - the rest above is just the default stuff found in this file --> 
      <merge key="input.x11_options.emulate3buttons" type="string">False</merge> 
    </match>

```
     
 
It will get picked up once the system-wide HAL instance is restarted, easiest is to reboot. 

Also, see [Ubuntu bug #54191](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-Configinput-mouse/+bug/54191).

---

