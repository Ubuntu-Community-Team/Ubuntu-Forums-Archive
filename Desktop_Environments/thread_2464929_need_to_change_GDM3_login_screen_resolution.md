---
title: "need to change GDM3 login screen resolution"
date: 2021-07-16
forum: Desktop Environments
---

### Post by jfaberna on 2021-07-16
I can find lots on hits on this subject, but none seem to be right for Ubuntu 20.04.2

I have a 4K monitor with the scale factor set to 200% so it viewable for me but still allows 4K pictures and videos to be viewed correctly.

However, this has no effect on the login screen.  It's still way too small. How can I tell gdm3 to scale or use HiDPI?

---

### Post by deadflowr on 2021-07-16
Which things have you tried?
So no one posts repeat failures and wastes both their's and your time.

---

### Post by jfaberna on 2021-07-16
> **deadflowr said:**
> Which things have you tried?
So no one posts repeat failures and wastes both their's and your time.[https://askubuntu.com/questions/912052/how-do-i-change-gdm3-login-screen-resolution](https://askubuntu.com/questions/912052/how-do-i-change-gdm3-login-screen-resolution)
 goes back to 17.04 and I'd looked at what they pointed to and those files didn't exist on 20.04.

I know that Kubuntu 20.04 has a login setting and you can choose sync and that works, but I have not found any settings for GDM3 that compare to SDDM.

---

### Post by deadflowr on 2021-07-16
Look at this then:
[https://askubuntu.com/questions/906797/scaling-gnome-login-screen-on-hidpi-display]("https://askubuntu.com/questions/906797/scaling-gnome-login-screen-on-hidpi-display")

---

### Post by jfaberna on 2021-07-16
> **deadflowr said:**
> Look at this then:
[https://askubuntu.com/questions/906797/scaling-gnome-login-screen-on-hidpi-display]("https://askubuntu.com/questions/906797/scaling-gnome-login-screen-on-hidpi-display")
Thanks, that helped. The specific steps I did were:
```
sudo nano /usr/share/glib-2.0/schemas/org.gnome.desktop.interface.gschema.xml
```
1.change the default in the code block to '2' as listed below:
```
    <key name="scaling-factor" type="u">
      <default>2</default>
      <summary>Window scaling factor</summary>
      <description>
        Integer factor used to scale windows by. For use on high-dpi screens.
        0 means pick automatically based on monitor.
      </description>
    </key>
```
2. run the following command.```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
3. reboot

---

