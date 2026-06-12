---
title: "usb hd mounts fine if hotpluged but not after startup"
date: 2009-03-11
forum: General Help
---

### Post by tmesdp3 on 2009-03-11
I am running xubuntu 8.04 on a laptop and logging in as a unprivileged user (created using the 'User and Group' utility in System menu). The user has the privilege to 'Access external storage devices automatically'.

If I plugin a usb drive after logging in, I can access it with no problem. 
If i plug it before boot, it is not automatically mounted. i can mount it  using Thunar File Manager.

What i would like is that when I leave the hd connected to the laptop I do not have to use Thunar to mount it. Is there a script i can run at xfce startup to mount it or some settings that will do the trick? 

I would like to avoid editing fstab. It seems that if i can mount it using Thunar, i should be able to access it automatically without having to modify fstab or using any GUI. I am ok to have a script run after startup of xfce to solve the issue. Since i am a newbie at linux, maybe i am missing something.

Thank you for your help.
Alex.

---

### Post by tmesdp3 on 2009-03-15
After digging in Thunar i found my solution. There is a thunar utility that can mount it once i have logged in. I can be put in a script easily:
```
thunar-volman --device-added <udi-of-your-device>
```

example in my case:
```
thunar-volman --device-added '/org/freedesktop/Hal/devices/volume_uuid_01B4_4B58'
```

Thanks to me :D

---

