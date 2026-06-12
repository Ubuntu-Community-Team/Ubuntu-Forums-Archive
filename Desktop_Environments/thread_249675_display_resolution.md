---
title: "display resolution"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Rumpty on 2006-09-02
After a lot of research and the installation of required programs, I finally managed to install the NVidia driver for my GeForce 6100 on-board graphics.

But, I still cannot change display resolution from the Administrator mode of System Settings, whereas if I am running as Root (i.e. stated x from Recovery Mode at the # prompt) I can change Display Resolution no problem! 

Can anyone sort this out please? Being stuck at 60Hz refresh rate is not good.

---

### Post by croak77 on 2006-09-02
Run sudo dpkg-reconfigure xserver-xorg from a terminal. It will ask you questions about mouse, keyboard, video driver (select nvidia), and resolution. Or you can manually edit /etc/X11/xorg.conf and put the correct values.

---

### Post by brim4brim on 2006-09-02
Yeah I'd recommend editing the xorg.conf (sure there is a howto here if you search) and add the resolutions if you know what the resolutions you want are.  It's pretty handy as they'll be one there already to work off.

---

### Post by taurus on 2006-09-02
To edit /etc/X11/xorg.conf, open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Rumpty on 2006-09-03
Ok, I have run sudo dpkg-reconfigure xserver-xorg, and things are making more sense now. xorg.conf is simpler, no monitor modelines, for instance, and a clear indication of possible resolution settings. 

Going to System settings - Display - Admin mode, it all works now. I have the same resolution options available as are in the xorg.conf. No options in the refresh rate box, but it gives me either 75 or 85Hz, depending on the resolution selected, so I can live with that. 

There is still something flaky about setting up the display though, I reckon. Occasionally, after selecting Admin mode, there is no box coming up asking for my password. Another odd thing, if I try Kcontrol, which some prefer anyway, (as r00t), there is no screen for the display options coming up after selecting Display, just a generic KDE Control Center window. The options above (digital camera) and below (joystick) work as expected. So something is still not right?

Anyway, thanks for the help. Things are a lot further ahead now.

---

