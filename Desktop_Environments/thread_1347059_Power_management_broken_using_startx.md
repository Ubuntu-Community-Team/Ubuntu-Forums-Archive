---
title: "Power management broken using startx"
date: 2009-12-05
forum: Desktop Environments
---

### Post by galatians on 2009-12-05
I decided to disable GDM and just start X from the command line using the startx command.

This works great and X starts up into gnome with openbox as my WM.

Everything seems to work great except for the power options. When I close my laptop lid the screen turns on but when I open it again it doesn't come back on so I have to reboot to get it back.

Also when I select Suspend or Hibernate from the gnome menu it just locks the screen.

Any ideas? I specifically installed Ubuntu instead of Gentoo specifically because I knew that power management would work great.

---

### Post by Greenwidth on 2009-12-05
Do you have a swap partition or swap file?

---

### Post by galatians on 2009-12-05
Actually I don't have a swap partition or swap file. I have loads of RAM I decided against one. I've been using Linux a long time and never ran out of memory.

Note that suspend, hibernate and closing the lid works perfectly as expected when I login using GDM.

Thanks.

---

### Post by Greenwidth on 2009-12-05
Strange. It might be worth adding a swapfile to be sure, you can always remove it afterwards if it doesn't help:

[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by galatians on 2009-12-06
Why would adding a swap file fix it when it works perfectly using GDM but it doesn't work from startx?

---

### Post by falconindy on 2009-12-06
Create an .xinitrc file in your home directory. Add the following line to it:
```
exec ck-launch-session gnome-session
```

---

### Post by galatians on 2009-12-06
> **falconindy said:**
> Create an .xinitrc file in your home directory. Add the following line to it:
```
exec ck-launch-session gnome-session
```

Thanks so much, that worked perfectly.

It really is incredible to me how people like you know these perfect 1 line fixes to weird problems.  I'm used to getting to the bottom of issues in Gentoo but the Ubuntu Gnome world is a huge maze for me.

---

### Post by falconindy on 2009-12-06
> **galatians said:**
> Thanks so much, that worked perfectly.

It really is incredible to me how people like you know these perfect 1 line fixes to weird problems.  I'm used to getting to the bottom of issues in Gentoo but the Ubuntu Gnome world is a huge maze for me.
Meh. I don't even use Gnome anymore. You learn an awful lot in a short time when you try to break Arch on a daily basis.

---

