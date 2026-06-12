---
title: "Use graphics driver vendor's tools (NVidia)"
date: 2009-04-10
forum: General Help
---

### Post by skbeez on 2009-04-10
When I log into Ubuntu, my screen is pretty "fuzzy" for lack of a better word and the only thing that seems to fix it is for me to manually go to:

System -> Preferences -> Display  and the following message pops up, 

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor’s tool instead?"

I click "OK" or whatever and immediately, my screen is crystal clear. But then when I log out/restart/shut down the computer and try to get back in the fuzziness comes back and I have to manually tell Ubuntu to use the NVidia tool 

I was wondering if there was anyway for me to make Ubuntu use the Nvdia's graphics tool by default when I log in to the system.

If it's any help, it seems that the "fuzziness" is coming from the forced full GPU scaling. When I turn it off, the screen becomes clear. I am using a resolution of 1680x1050.

Thanks in advance for all the help.

---

### Post by Chrys7 on 2009-06-17
I have the same problem. Any ideas?

---

### Post by Swerve1000 on 2009-07-01
I'm having the same issue. 

My graphics card is an Nvidia 6800GT.

Does anyone know how I could remove the Nvidia driver and go back to the default one installed by Ubuntu 9.04 when the OS is installed.

Thanks for any help.

---

### Post by XaversPSP on 2009-11-05
Same trouble at all.
I am very new to Ubuntu (currently 9.04) (switched from Xp because of some virus captured my laptop)
I got Nvidia GeForce 8400m G 128 mb in my acer aspire 4720ZG so its actually pretty good graphic system for me.
But then I got flash player problem in internet so I go to System > Preferences > Display and got busted with the same message. It all confuses me. If someone can help us, please do it.

---

### Post by AaronP_ on 2009-11-07
For the original posters in this thread, you can load the configuration that the NVIDIA control panel saves by running "nvidia-settings --load-config-only".  You can put that in your startup programs to make it apply your settings when you log in.

@XaversPSP: I'm not sure I understand the problem you're having.  Does the display properties dialog not launch nvidia-settings properly?

---

### Post by P4man on 2009-11-07
to change nvidia settings after installing the drivers you must use the nvidia applet. System > Administration > nvidia X settings

Now problem is to save those settings to your X config file, you need root permission, and the nvidia app doesnt ask for permission to obtain that so will fail when you try to save to xorg.conf file. To solve that, just press alt F2 and run

```
gksudo nvidia-settings
```

that will launch the nvidia settings app with root permission so you can change resolution and stuff then click the option to save the x config file.


Mind you, none of this has anything to do with flash. If you have a problem with flash please explain what. If you want to install it, install it from the ubuntu software centre (install "ubuntu restricted extras" while you're at it, it will install flash, java, and other stuff you need anyhow)

---

### Post by 3rdalbum on 2009-11-07
The last time I tried it, the Nvidia Config program put some nonsense into my xorg.conf file (to do with "metamodes"), and it wasn't the right nonsense to tell X what resolution to use! In the end I had to manually add the "Modes" to xorg.conf; you might want to look up a HOWTO because I can't remember exactly where to put it in the file, and when I clean-installed Ubuntu it got the correct mode first time.

---

### Post by phildini on 2009-11-08
I'm having a similar problem, and am not sure if I should make a new post for it or not. I have a laptop with an nvidia mobile card and am using the nvidia x settings manager to set options with it. 

Is there a way to make the nvidia x settings manager auto-detect when I've plugged in or removed my second monitor, and change settings accordingly?

---

