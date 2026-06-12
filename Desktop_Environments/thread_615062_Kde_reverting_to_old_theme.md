---
title: "Kde reverting to old theme"
date: 2007-11-16
forum: Desktop Environments
---

### Post by BWF89 on 2007-11-16
I have all my system settings to make Kde look and feel like windows.

Colors = Windows XP
Style = MS Windows 9x
Window decorations = Redmond

But for some reason even though the style is set to MS Windows 9x when I launch Adept or any other program the progress bars and buttons are using the default Kubuntu style.

I've tried switching it to another theme and back to MS Windows 9x but it doesn't work.

---

### Post by miggols99 on 2007-11-16
Create a symlink for the .kde folder:

```
sudo ln ~/.kde /root/.kde
```

So it will copy your kde settings for root run programs.

---

### Post by BWF89 on 2007-11-16
I tried that and got:

```
bwf89@bwf89-desktop:~$ sudo ln ~/.kde /root/.kde
[sudo] password for bwf89:
ln: `/home/bwf89/.kde': hard link not allowed for directory
```

---

### Post by D-EJ915 on 2007-11-16
use a symlink "-s"

sudo ln -s ~/.kde /root/.kde

---

### Post by BWF89 on 2007-11-16
It went in alright.

I think Adept is the only program that uses the Keramic progress bars regardless of what settings you have. Because I loaded up the GIMP on Keramic and it used it's progress bars. And than I switched to the Windows theme and it used it's progress bars.

---

