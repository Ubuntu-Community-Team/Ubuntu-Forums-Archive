---
title: "refresh rate"
date: 2005-10-06
forum: Desktop Environments
---

### Post by JohnB on 2005-10-06
i am useing 5.04 and i want to change my monitor's refresh rate but only 60 hertz is listed. I Thought it might be a driver issue. I know the monitor is capable of atleast 75.

---

### Post by darkmatter on 2005-10-06
[QUOTE=JohnB]i am useing 5.04 and i want to change my monitor's refresh rate but only 60 hertz is listed. I Thought it might be a driver issue. I know the monitor is capable of atleast 75.[/QUOTE]

Make sure you have the horizontal and vertical ranges of your monitor handy (you will need to input them)

Open a terminal and run
```
sudo dpkg-reconfigure xserver-xorg
```

When you reach the section of the dialog regarding your monitors sync range, choose advanced mode, and manually enter the horizontal and vertical ranges.

After the dialog is complete, restart x with Ctrl+Alt+Backspace.

---

### Post by Perfect Storm on 2005-10-07
Or edit the xorg.conf via gedit manually. You need your monitor specs to do so.

```
sudo gedit /etc/X11/xorg.conf
```

Fill out HorizSync and VertRefresh 
It's under Monitor section.

save and reboot.

---

