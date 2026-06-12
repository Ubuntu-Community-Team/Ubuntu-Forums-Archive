---
title: "problem with Gnome 3 on Ubuntu 11.10"
date: 2011-11-16
forum: Desktop Environments
---

### Post by robertsatya on 2011-11-16
I tried installing Gnome 3.2 according to the common guidelines given on many websites. but when i login using the gnome settings, the desktop looks plain lame. i've seen many sceenshots of gnome 3 on web, they look awesome and mine doesnt look like them. there is no launcher and even the top bar looks different. and there is a taskbar too.

i've included my desktop's screencap alongside. can you help me get the gnome 3 that i find on web.

---

### Post by Perfect Storm on 2011-11-16
That looks like Gnome fallback.

Did you login into the right session?
Any chance you have an ATI card?

---

### Post by robertsatya on 2011-11-16
i logged into the Gnome session. the others were Gnome classic, Gnome classic (without effects),ubuntu, ubuntu 2D. i made sure i logged into Just Gnome.

and yea i have an AMD Radeon 6490M

---

### Post by robertsatya on 2011-11-16
How do i get the gnome 3 desktop ?
i've installed this one from the software center.

and yea i've read something called fallback when i clicked on system properties or display properties. how to get the gnome 3 then ?

---

### Post by Perfect Storm on 2011-11-16
I have heard there's problems with some of the ATI card and Gnome Shell. I suggest you search for ATI cards and Gnome Shell for more info.

---

### Post by lakosshoots on 2011-11-17
Hi there. I've had some issues with ATI as well in 11.10 64bit version.

I installed the proprietary ATI drivers, but changes in the AMD Catalyst Control Center (administrative version) were not saved. Even though the kernel generic drivers worked, the quality was low.

I managed to fix it by installing the ATI drivers and running AMD Catalyst Control Center (administrative version) as SU. Even thought it was supposed to run with SU privs, it does not work.

So type  
$gksudo amdcccle

and AMD Catalyst Control Center (administrative version) will open. Manage your ATI card from there. Apply-> OK -> Reboot and you should be OK.

I have noticed that it might be a user policy issue in 11.10.

There is a similar problem with ntfs mounts. If you mount a ntfs formated HDD, you' ll propably have only read rights.

I am waiting an update to fix this, because I am bored doing it manually, every time I have to mount an external drive. (unmount must be made with SU or equivalent right as well, so it's @#$%$ grr )

More info can be found here.

[http://just-more-thoughts.blogspot.com/2011/11/ubuntu-1110-ati-drivers-and-ntfs-mounts.html]("http://just-more-thoughts.blogspot.com/2011/11/ubuntu-1110-ati-drivers-and-ntfs-mounts.html")

I hope it helps.

---

