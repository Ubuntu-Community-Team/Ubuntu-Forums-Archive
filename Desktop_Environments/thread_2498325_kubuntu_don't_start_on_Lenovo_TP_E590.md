---
title: "kubuntu don't start on Lenovo TP E590"
date: 2024-06-09
forum: Desktop Environments
---

### Post by msauer75 on 2024-06-09
Hi,
I installed the latest kubuntu 24.04 on my Lenovo Thinkpad E590. After the last update today, the system didn't start anymore. The screen will be black and nothing more happens.
How can I find out where the problem is?
THank you for your help
BR
martin

---

### Post by Bashing-om on 2024-06-09
msauer75; Hello

I too am experiencing the same issue. To this time I have yet to know the cause - no faults found in the journal log.
I can give you my work-around to boot the system.
Boot to grub's boot menu and type e to edit the boot parameter.
in the next screen edit the linux boot line:
remove "quiet splash" and insert the parameter systemd.unit=multi-user.target
key combo ctl + x to boot to terminal.
Log in here with your credentials

Now to start the GUI, in the terminal enter:
```

sudo systemctl start graphical.target

```

in my case my GUI is F7, yours is likely different - you might have to try all the F keys to see the GUI login screen.

Is my hope that another update fixes this issue. 
In the meantime

[INDENT]make things happen
[/INDENT]

---

