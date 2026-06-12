---
title: "3D Effects"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by Graham1 on 2007-04-03
Hi Guys :)

Just upgraded my graphics card (Nvidia FX5200) to the latest drivers and am now wondering where to go next :confused:. To get 3D effects, which components do I need to install? XGL? Compiz? ... . Btw, I'm running Ubuntu 6.10. Hopefully, someone can point me in the right direction :D.

:)

Edit: Forgot to mention that I'm running the 64-bit version of Ubuntu 6.10.

---

### Post by haricharan on 2007-04-03
hope this should help [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia")

---

### Post by Graham1 on 2007-04-03
> **haricharan said:**
> hope this should help [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia")

Thanks for the link haricharan :). Are there any tutorials just for getting the desktop cube / wobbly windows, etc working without Beryl? 

:)

---

### Post by Graham1 on 2007-04-03
Am I right in saying that if I'm running Xorg 7.1 (which I should be able to tell from the Nvidia applet), then all I need do is enable AIGLX? 

:)

---

### Post by Shoubidouw@@@ on 2007-04-03
AIGLX is loaded by default.
The only thing you need is to install BERYL packages and run Beryl-manager from menu

Should work!

---

### Post by Graham1 on 2007-04-03
> **Shoubidouw@@@ said:**
> AIGLX is loaded by default.
The only thing you need is to install BERYL packages and run Beryl-manager from menu

Should work!

Without Beryl, should I get the desktop cube and wobbly windows, etc? I've tried Beryl before (on openSUSE) but I'm only really after the basics (I'm easily pleased).

:)

Edit: In openSUSE 10.2 and Fedora Core 6, I had to enable "Desktop Effects". Is there a switch in 6.10?

---

### Post by haricharan on 2007-04-03
Beryl and Compiz( aka Desktop Effects) are two programs with which you could those cube and wobbly effects. I use Beryl and its easier to configure. I tried compiz but couldn't make it work. I am happy with beryl anyway.

If you are keen on installing Desktop Effects, use these instructions [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29)

---

### Post by Graham1 on 2007-04-03
> **haricharan said:**
> If you are keen on installing Desktop Effects, use these instructions [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29)

Followed the instructions but unfortunately, it killed X server :sad:. Tried restoring to a previous xorg.conf but the same error. Anyhow, this gave me a good excuse to try out 7.04 :D. Hopefully, I just need to upgrade my Nvidia drivers and I'll be ready to go. I'll let you know how I get on.

:)

---

### Post by Graham1 on 2007-04-03
Wow, that was so easy :D. Upgraded Nvidia driver using "Restricted Drivers Manager" and that was it. I'm already liking this version.

:)

---

