---
title: "Touch &quot;Show apps&quot; button cannot work normal in Ubuntu on Xorg"
date: 2024-11-13
forum: Desktop Environments
---

### Post by ginousi on 2024-11-13
Hi, Ubuntu,

We encountered a symptom with touch screen in Ubuntu on Xorg.

[IMG]https://imgur.com/g9rOPMf[/IMG]
[IMG]https://i.imgur.com/sr3rCg0.jpeg[/IMG]

When login with select "Ubuntu on Xorg", 
touch the "Show apps" button at bottom left corner,
the "app list" and "Desktop" can not switch loop.   

[IMG]https://i.imgur.com/R8XkZT9.jpeg[/IMG]

if click mouse key on the "Show apps" button,
the "app list" and "Desktop" can switch loop.
 
[IMG]https://i.imgur.com/KeMsExx.jpeg[/IMG]

When login with select "Ubuntu", 
touch the "Show apps" button or click mouse key on the "Show apps" button, the "app list" and "Desktop" can switch loop.   


Has any patch or solution to let in Ubuntu on Xorg mode,
let touch the "Show apps" button at bottom left corner,
the "app list" and "Desktop" can switch loop ?   

Thanks & Regards.
UsiGino

---

### Post by grahammechanical on 2024-11-13
I am using Ubuntu 24.04 LTS and I have just tested Ubuntu on X-Org. The show apps icon is working as it should and it behaves the same as Ubuntu on a Wayland compositor. But I do not have a touch screen.

Regards

---

### Post by ginousi on 2024-11-14
Yes, if click mouse key on the "Show apps" button, the "app list" and "Desktop" can switch loop, it is work normal both on X-Org and on a Wayland.

But if use finger to tab touch screen on the "Show apps" button, on X-Org,   the "app list" and "Desktop" can not switch loop,
on Wayland,  the "app list" and "Desktop" can switch loop.

---

### Post by ginousi on 2024-12-09
We checked, in Ubuntu old version 22.04.4 LTS, not this issue.
In Ubuntu 24.04LTS/24.04.1 LTS/24.10 , has this issue.

Is it a known issue for new Ubuntu?
And Ubuntu has fix plan for it?

---

### Post by grahammechanical on 2024-12-09
I am not being funny, but the solution that the Ubuntu developers have to problems with the X server is to stop using x.org as a display server. We only have an option to use X.Org because there are still some major applications that only work on the X server. The developers of those applications need to convert their software to use a Wayland compositor.

Red Hat Enterprise Linux is a major player in Linux and it has decided its RHEL 10 release in 2025 will not support the X Server. 

> Earlier this year (2023), as part of our RHEL 10 planning, we made a study to understand Wayland&#8217;s status ... we believe the Wayland infrastructure and ecosystem are in good shape,  and that we&#8217;re on a good path for the identified blockers to be resolved  by the time RHEL 10 is out, planned to be released on the first half of  2025 ... With this, we&#8217;ve decided to remove Xorg server and other X servers (except Xwayland) from RHEL 10 and the following releases

[https://www.redhat.com/en/blog/rhel-10-plans-wayland-and-xorg-server](https://www.redhat.com/en/blog/rhel-10-plans-wayland-and-xorg-server)

This will affect Red hat's community developed distribution of Linux called Fedora.

Some years ago Ubuntu developers produced their own display server to use instead of a display server based on the Wayland protocol. The Canonical display server is called Mir. It is still around and is the display server for a Kiosk application running on Ubuntu Core. It never became the default display server for Ubuntu Desktop. The default on Ubuntu desktop versions is a Wayland compositor from Gnome.org called Gnome Display Manager (GDM).

I found this question in Ubuntu Forums from the spring of 2024

[https://ubuntuforums.org/showthread.php?t=2496226](https://ubuntuforums.org/showthread.php?t=2496226)

I have still to find anything official from the Ubuntu developers.

Regards

---

