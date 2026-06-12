---
title: "Error with Compiz in Kubuntu"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by FooAtari on 2008-02-04
I know there is probably a hundred posts about this, but I couldn't see one that fixed this particular problem.

When I start compiz I get this;

pc@linux:~$
 /usr/bin/compiz --replace
Checking for Xgl: present.
**Checking for nVidia: not present.**
Checking for Xgl: present.
Enabling Xgl with nVidia drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Does anyone know the problem here?  I have the Nvidia drivers installed through the restricted drivers manager.  Im running a 7300GT.  I can run glxgears and also Alien Arena.

Thanks

---

### Post by dabl on 2008-02-04
Couple of ideas here:

1. Open a console window and run ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` to overwrite your xorg.conf with the needed glx and compositing options.  Then try running compiz again.

p.s. you only need to enter ```
compiz --replace
``` not the whole path


2. If that doesn't work, I have not had good luck with the restricted drivers manager for installing the Nvidia driver, but Envy works fine.  I'd give it a shot if I were you, and then after the driver is re-installed, run the command in #1 above again and try compiz again.  Get Envy here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the download on the bottom right of his table of operating systems.  :)

---

### Post by FooAtari on 2008-02-04
i couldnt get envy to work in kubuntu. ill try again

---

### Post by FooAtari on 2008-02-05
Same problem...

When I run Copmiz before installing xserver-xgl it says xgl is not preset.  But nvidia is present.  So I installed xserver-xgl.  When I run compiz it says xgl is present but not nvidia isn't present! Even after doing what you suggested.

So there is obviously a problem between nvidia and xgl...

Envy doesn't seem to work well with Kubuntu at all.  Maybe I should just forget about KDE for the moment and install Ubuntu as help for Kubuntu is thin on the ground in both forums and guides.

---

### Post by dabl on 2008-02-05
> **FooAtari said:**
> Same problem...

  So I installed xserver-xgl.  



No no no!  If you have an Nvidia card, you don't want xserver-xgl.  The fact that compiz reports "no xgl" is not a problem for you -- you'll be using GLX. Remove the xserver-xgl package, for starters.

> 

Envy doesn't seem to work well with Kubuntu at all. 



That is an odd observation, in my experience.  What do mean "doesn't work well" -- does it intall the Nvidia driver, or not?  If it fails, what are the errors?  It sounds to me like you might actually have the Nvidia driver installed correctly -- do you see a green Nvidia splash right before your login GUI?  In your KMenu>System folder, is there an Nvidia Settings item?

---

### Post by FooAtari on 2008-02-06
It won't install.  I read elsewhere that it has issues with Kubuntu, or maybe that would just be the KDE desktop.  when I try and run it it says it can't find some required dependencies and offers to install them.  This then fails but it doesn't say which dependencies are missing.

I'm sure I could find out but I installed Ubuntu yesterday and had the restricted drivers installed and Compiz/emerald fully working in about half an hour.  Very straight forward in comparison to Kubnuntu...

I do prefer the KDE desktop, but as with 6.10 I have experienced many issues with Kubuntu that do not seem to exist in Ubuntu.  Maybe there is less resources put Kubuntu's way as it's less popular or something.

---

### Post by dabl on 2008-02-06
That's odd.  The last time I installed Envy on Kubuntu 7.10 it went on with no issues -- pulled in all of its own dependencies.  In prior versions, I used to have to write down the missing dependencies and then install them first, then install Envy.

Also, I think that restricted drivers manager now works the same in Kubuntu as Ubuntu.  Although I use "nvidia-glx-new" and get the same result.

Well, it's good that you got something running Compiz!  :)

---

