---
title: "Problem with gnome-splashscreen-manager and gnome-art"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by coldzero1120 on 2007-10-09
I can not start gnome-splashscreen-manager and gnome-art :

> /usr/bin/gnome
/usr/bin/gnome-splashscreen-manager:22:in `require': no such file to load -- gnome_splashscreen_manager (LoadError)
        from /usr/bin/gnome-splashscreen-manager:22-splashscreen-manager:22:in `require': no such file to load -- gnome_splashscreen_manager (LoadError)
        from /usr/bin/gnome-splashscreen-manager:22
> 
root@Delly:/boot/grub# gnome-art
/usr/bin/gnome-art:22:in `require': no such file to load -- gnome_art (LoadError)
        from /usr/bin/gnome-art:22
root@Delly:/boot/grub# gksudo gnome-art
/usr/bin/gnome-art:22:in `require': no such file to load -- gnome_art (LoadError)
        from /usr/bin/gnome-art:22

I have tried to re-install these packages many times but I got the same problem. Any help?

---

### Post by kyphi on 2007-10-09
If you have splashscreen manager installed, a menu entry should be present under System -> Preferences.

You can also invoke it from the command line by typing 

```
gnome-splashscreen-manager
```

followed by pressing 'Enter'.

Same goes for gnome-art.

---

