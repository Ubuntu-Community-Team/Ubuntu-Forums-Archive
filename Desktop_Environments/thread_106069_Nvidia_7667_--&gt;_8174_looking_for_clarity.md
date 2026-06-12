---
title: "Nvidia 7667 --&gt; 8174: looking for clarity"
date: 2005-12-19
forum: Desktop Environments
---

### Post by rosslaird on 2005-12-19
I thought I'd post a new thread because some of the existing threads involving my issue are getting horribly long, difficult to follow, and with many diversions.

I followed tseliot's helpful how-to for upgrading the NVIDIA driver (using "method 3") from 7667 to 8174. I want to experiment with transperency and such. It's an excellent guide. However, it did not quite work for me -- I had already tried an upgrade before finding the guide and was probably already working with a mixed/borked system. Anyway, I uninstalled my previous attempt with the package from nvidia  (using --uninstall on the package and running the script again), uninstalled all the debian/ubuntu packages (remembering to use --purge) and followed the various tips about how to do it right. So far so good. The second-try install of the new nvidia driver, with the guide's assistance, worked perfectly: no errors, no issues. I rebooted.

X won't start -- or, it starts into the "black screen" about which there are many, many posts on the nvidia forums. No one seems to know how to fix this. So I decided to go back (using --uninstall again, and using apt to recover all the debian/ubuntu packages). OK, back to version 7667 of the driver. But now my system boots only until "Checking battery state," an issue about which there are many, many posts here on the ubuntu forums. Again, no one seems to know exactly how to fix this (the dpkg-reconfigure fix did not work on my system). I have to ctl-alt-f1 into a terminal and go from there.

So I'm stuck: I can't go forward with the upgrade (black screen) and I can't seem to get back to a fully working system ("checking battery state" halt). This is a bit frustrating. Not that it probably matters much, but I'm working with a GeForce4 MX onboard video rig.

Suggestions are most welcome.

Ross

---

### Post by dto on 2005-12-19
Whenever I tried upgrading from 7667 to 8174, I'd always end up at the "Checking battery state" hang and frustrated.

What I just did (that finally worked!) was take the advice I've seen from one of the NVidia guys and removed restricted-modules-common, which ends up removing a number of other restricted-modules packages. After I did that, I booted back into recovery mode, recompiled and installed the 8174 module, and it worked. 

If you try this, make sure you let the NVidia installer create it's own new xorg.conf (the last step in the install process). The first time I skipped this step, and X booted with a funky resolution and clock speed. After I went through the install process again, it was fine. 

After that, I decided to upgrade my laptop as well. In this case, I *didn't* remove restricted-modules-common, but instead went into /etc/init.d/ and made linux-restricted-modules-common non-executable. I think this might be the safer way to try, since you're not actually removing anything.  

After adding RenderAccel and other options to xorg.conf, I'm happily playing with transparency.

---

### Post by rosslaird on 2005-12-20
Thanks for the suggestions. I think I already tried something like this, but I will give it another shot.

The list of things that need removing is getting pretty long...

  linux-restricted-modules-2.6.12-10-386*
  linux-restricted-modules-2.6.12-10-k7* 
  linux-restricted-modules-common*
  nvidia-glx*
  nvidia-kernel-common*
  nvidia-kernel-source* 
  nvidia-settings*

Also, I notice that I have something called "nvidia-glx-legacy" in /etc/init.d. I'll rename it.

Will try to post back, if I can get the system to boot...

---

### Post by dto on 2005-12-20
I don't think I had the nvidia packages that you show installed.

Looking at File -> History in Synaptic, here's what it removed/installed for me:

[INDENT][COLOR="Green"]Removed the following packages:
linux-386
linux-686
linux-restricted-modules-2.6.12-10-686
linux-restricted-modules-2.6.12-9-386
linux-restricted-modules-386
linux-restricted-modules-686
linux-restricted-modules-common

Installed the following packages:
linux-image-2.6.12-10-386 (2.6.12-10.24)[/COLOR][/INDENT]

It still booted into recovery mode just fine after that, and I was able to re-install the 8174 nvidia driver from there. 

Also, during the initial boot-up splash, I got a "failed" for "Loading modules". After I made /etc/init.d/linux-restricted-modules-common non-executable that went away.

Edit: Looking at it some more, /etc/init.d/linux-restricted-modules-common gets called from rc0.d, rc6.d and rcS.d. It might be better to make those non-executable instead (or maybe delete them?).

---

### Post by rosslaird on 2005-12-20
I am in X now with the new driver. Woohoo!

I just removed the restricted-modules, since it's so easy to get them back with apt and it was faster than looking up the correct permissions to make it non-executable.

I think the thing that made the difference -- and it was something you wrote that made me think of it -- was to reboot before running the script (after removing the relevant applications). I had not rebooted before, but just went ahead with the script after removing the apps. (Also, I had not removed the legacy bit in init.d, so maybe that makes a difference.) There's something about "creating TLS links" in the bootup that I think messes with the installation.

Now, I don't yet have rendering/composite enabled. That's next. But the driver is working.

---

### Post by rosslaird on 2005-12-20
OK, composite effects enabled. Very nice. I'm using xfce, and I use the xfce window manager (xfwm) in gnome, so I'll get composite effects by default in both. And KDE also now has composite effects built-in. So I think I'm set.

I still have the "checking battery" issue, by the way, but I can live with it until I can find a solution.

Thanks for the help.

Ross

---

### Post by dto on 2005-12-20
Cool -- glad it's working for you now.

I had actually given up on it until I saw your initial post, and decided I would give it one more shot. Glad I did! :)

---

