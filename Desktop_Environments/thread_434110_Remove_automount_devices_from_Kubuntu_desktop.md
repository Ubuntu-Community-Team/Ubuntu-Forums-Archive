---
title: "Remove automount devices from Kubuntu desktop"
date: 2007-05-05
forum: Desktop Environments
---

### Post by Surkow on 2007-05-05
I can't find any documentation how to remove  automount devices from the KDE desktop. The only thing I can think about is the following:

- Right click
- Click "Configure Desktop"
- Select "Behavior"
- Select "Device Icons" tab
- Disable the devices you don't want to see on the desktop

But why doesn't it work at all?

---

### Post by Surkow on 2007-05-06
This is only about the icons from devices that appear on your desktop when mounted.

---

### Post by Surkow on 2007-05-06
I heard lots of people had the same problem. The only solution I can find is a workaround for Suse.

---

### Post by Nythain on 2007-05-06
the easiest way, but it has a problem... is to change them in /etc/fstab and mount them somewhere like /mnt instead of /media... the problem is then they dont show up in things like the storage media panel applet

---

### Post by Surkow on 2007-05-06
> **Nythain said:**
> the easiest way, but it has a problem... is to change them in /etc/fstab and mount them somewhere like /mnt instead of /media... the problem is then they dont show up in things like the storage media panel applet

Good to know that it will only look at the devices mounted in Media. But I don't think I want to remount all things somewhere else because of an icon. ;D

---

### Post by Surkow on 2007-05-08
Nobody has a different solution?

---

### Post by Surkow on 2007-05-10
Bump.

---

### Post by HeavyIron on 2007-05-13
I found an easy solution here: [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/]("http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/")

---

### Post by Surkow on 2007-05-17
> **HeavyIron said:**
> I found an easy solution here: [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/]("http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/")

I know how it works in Gnome (desktop environment). But I can't remove the drive icons from the KDE desktop (that guide is only about Gnome).

---

### Post by clk99 on 2007-06-18
I have this same problem.  I guess it isn't bothering me a whole lot but I like not to have icons on my desktop.  If there is a decent fix for this that anyone knows of I'd love to hear about it.  Thanks.

---

### Post by muzikjock on 2007-06-19
I dont know if this helps, but i had a similar problem on my desktop. I have ubuntu fiesty fawn 7.04. Some how i did something and all of my home folder contents showed up on my desk top and couldnt figure out how to stop it. I read some where about the configuration editor (applications/system tools/configuration editor). I played around with it and navigated to apps/nautilus/desktop/preferences. Some how the column "desktop_is_home" was checked. i unchecked it and all my home folder icons went bye bye and went back home where they belonged. :)
I dont know if this will help anyone, im a nubie myself and i sometimes get into trouble i cant get out of. Why else am i here? lol.

---

