---
title: "Gnome panel hides application title bar"
date: 2009-06-23
forum: General Help
---

### Post by WitchCraft on 2009-06-23
Hi, question:

Lately, Google chrome crashed on my Linux.
Unfortunately, it seems to have had a lasting effect even after  restarting...

The problem is that the top gnome panel is over the application title bar (i cannot close anything anymore, because I can't click on the x at the right side on the top because there now is gnome panel...). I have to go to the bottom, right click and select close if I want to close anything.

If I switch gnome-panel to autohide, I see the application title bar, and it's really that the gnome-panel is over it...

Is there anything in gconf that I have to switch back?

---

### Post by TeoBigusGeekus on 2009-06-23
Press Alt+Click on the window. You can now drag it anywhere you want, thus making the close button visible.

---

### Post by WitchCraft on 2009-06-23
> **TeoBigusGeekus said:**
> Press Alt+Click on the window. You can now drag it anywhere you want, thus making the close button visible.

I want the gnome panel to not be but over the application title bar, not some Alt+Click workaround that's even more annoying than right clicking on the panel at the bottom.

---

### Post by WitchCraft on 2009-06-24
bump. Probably somebody knows what the problem is.

---

### Post by WitchCraft on 2009-06-25
bump. Anybody has the slightest idea how to fix it?

---

### Post by IG0RK0 on 2009-06-26
i had the same problem. Gnome-panel was hideing all maximized windows. I was using:
Debian testing
gnome 2.26.1
gnome-panel 2.24.3

The problem  solved after upgrade gnome-panel from version 2.24 to 2.26

Hope this help

---

### Post by WitchCraft on 2009-06-27
> **IG0RK0 said:**
> i had the same problem. Gnome-panel was hideing all maximized windows. I was using:
Debian testing
gnome 2.26.1
gnome-panel 2.24.3

The problem  solved after upgrade gnome-panel from version 2.24 to 2.26

Hope this help

Hi, thanks for that, I'm on debian testing, too.

I also have 2.24

I tried to reinstall, that didn't help, I've even reinstalled gnome-desktop-environment

How did you get 2.26, I can only get 2.24 ?

> 
all:~# apt-get install --reinstall gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/492kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 326115 files and directories currently installed.)
Preparing to replace gnome-panel 2.24.3-1+b1 (using .../gnome-panel_2.24.3-1+b1_i386.deb) ...
Unpacking replacement gnome-panel ...
Processing triggers for man-db ...
Setting up gnome-panel (2.24.3-1+b1) ...
all:~# apt-get upgrade gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Tews on 2009-06-27
```

metacity --replace

```

That should take care of your problem  :)

---

### Post by WitchCraft on 2009-06-27
> **Tews said:**
> ```

metacity --replace

```

That should take care of your problem  :)

Wow, thanks, problem solved!

Why is that?

---

