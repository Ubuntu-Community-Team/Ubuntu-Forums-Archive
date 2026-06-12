---
title: "Why do I have no desktop effects"
date: 2007-11-22
forum: Desktop Environments
---

### Post by np101 on 2007-11-22
i just logged onto Ubuntu gusty and i found some updates to install, so i installed them and then went to change my background and in the same window i say a tab called visual effects and i went to it and found that nothing was selected so i selected the option extra. After that i found my cube to be gone and also the bar on top of a window for closing and minimizing and moving windows was gone. I thought this was an error so i rebooted and on start up i found i new large nvidia logo just before my login screen and then i logged in and played around with the visual effects for a while longer trying to get them to work and now nothing works at all except for the option of no visual effects.

Can someone please help me to get back my wobble and my cube and any other visual effects thanks.

---

### Post by Znort_Ubern00b on 2007-11-22
Open terminal and type

compiz --replace

then type ccsm

this should start comipz then open the compiz manager.should then be able to set up wobbly windows and cube again.

---

### Post by np101 on 2007-11-22
That isn't working when i type compiz --replace into the terminal all of my windows no longer have that bar up the top of a window for closing minimizing and moving windows but i can wobble the windows by holding alt and moving them about but still no cube. Also the terminal sometimes crashes and goes completely white and other times it displays this.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:0d.0 0300: 10de:03d2 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure

also when i go into visual effects no option is selected and when i select none i get the bar up the top of a window for closing, minimizing and moving windows back which is good but i then have no visual effects at all.

any other suggestions thanks.

---

### Post by Tenken on 2007-11-22
```
Checking for Xgl: not present. 
```

Did you make sure to install the nVidia proprietary driver?

In Gnome System->Administration->Resitriced Drivers Manager

---

### Post by jhenager on 2007-11-23
I don't know if this has any bearing on your issue, but after installing some updates today, my theme was reset to a standard one, and I really liked my old theme. I think it had to do with an update to compiz. I recall seeing one called compiz-core.
Anyway, I found another theme that is ok, but I'd sure love to have my old one back.

---

### Post by Junk_head on 2007-11-24
I got the same problem as the OP, i installed the compiz updates and lost my theme and was left boarder-less. Anyway to perhaps downgrade maybe?

---

### Post by babygirl on 2007-12-07
> **Znort_Ubern00b said:**
> Open terminal and type

compiz --replace

then type ccsm

this should start comipz then open the compiz manager.should then be able to set up wobbly windows and cube again.


I successfully updated compiz, and had the same issue as Np101. I have a neurological disorder from a broken neck and found this solution completely by accident.

Open the advanced settings, and here's where it got weird. I had a muscle spasm that caused me to randomly click between none and normal. All the sudden my title bars were back and I had access to a limited ammount of the full features. It only allows me to use those listed under "extra. It will not do the custom settings.


Does anyone know how to enable them all? :confused:

---

### Post by approaching on 2007-12-07
when you go to the ccsm, make sure that you have windowing enabled, its one of the plugins. once you do that, a good workaround/upgrade is to install emerald. but since the windows are in fact wobbling, that means that compiz is running, thats a good thing. just head on over to synaptic and install emerald and you should be fine.

---

### Post by babygirl on 2007-12-08
Ok, different system, almost the same problem as before. This time the desktop effects won't stay enabled, and while they are enabled I loose my title bars. Any ideas?

---

### Post by khurrum1990 on 2007-12-08
> **babygirl said:**
> Ok, different system, almost the same problem as before. This time the desktop effects won't stay enabled, and while they are enabled I loose my title bars. Any ideas?
I don't know why ur desktop effects don't stay enabled. Which card r using? If u r using Nvidia do u have the latest drivers?

Visit this page, its for OpenSuse but it talks about the beryl title bar problem for Nvidia and should work on Ubuntu as well.
[http://en.opensuse.org/Beryl](http://en.opensuse.org/Beryl)

There r a few things u have to enter to ur xorg file using a terminal, the commands u need to enter r written shortly after the " Beryl with nVidia drivers - no Xgl/AIGLX" title.

I hope this works!

---

### Post by babygirl on 2007-12-08
> **khurrum1990 said:**
> I don't know why ur desktop effects don't stay enabled. Which card r using? If u r using Nvidia do u have the latest drivers?

Visit this page, its for OpenSuse but it talks about the beryl title bar problem for Nvidia and should work on Ubuntu as well.
[http://en.opensuse.org/Beryl](http://en.opensuse.org/Beryl)

There r a few things u have to enter to ur xorg file using a terminal, the commands u need to enter r written shortly after the " Beryl with nVidia drivers - no Xgl/AIGLX" title.

I hope this works!

The water effects were doing it. As soon as I disabled it everything worked, but I'm still missing my title bars. Any ideas?

---

### Post by khurrum1990 on 2007-12-08
Try these commands, just open terminal and paste them in one by one:
sudo nvidia-xconfig --composite
sudo nvidia-xconfig --allow-glx-with-composite
sudo nvidia-xconfig --render-accel
sudo nvidia-xconfig --add-argb-glx-visuals

I think the reason water effects crash compiz for u is maybe because ur vga card doesn't support them and u didn't mention ur nvidia driver version.

---

### Post by babygirl on 2007-12-08
> **khurrum1990 said:**
> Try these commands, just open terminal and paste them in one by one:
sudo nvidia-xconfig --composite
sudo nvidia-xconfig --allow-glx-with-composite
sudo nvidia-xconfig --render-accel
sudo nvidia-xconfig --add-argb-glx-visuals

I think the reason water effects crash compiz for u is maybe because ur vga card doesn't support them and u didn't mention ur nvidia driver version.

Both machines run the Nvidia Geforce 7300 GT. They are installed and fully enabled. The only real difference with these machines is my MB has AMD chipset and the other has Intel. I still haven't gotten more than "extra" on it, but would looooove custom on both machines.

---

### Post by khurrum1990 on 2007-12-08
Hi again, ok did ur title bars appear though after running these commands u have to disable desktop effects and restart xserver by pressing Ctrl+Alt+Backspace key. Then login again start desktop effects. If ur title bars r back that great. Your nvidia card is fine.

How much ram do u have?

Have u installed compizconfig-settings-manager? Do that by typing:
sudo apt-get install compizconfig-settings-manager

---

### Post by numbah_one's on 2007-12-08
i have problem with compiz and its seems it's also causing problem with awn,is there anyone who can help me?

laptop:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

laptop:~$ avant-window-navigator
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x380002a (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by khurrum1990 on 2007-12-08
> **numbah_one's said:**
> i have problem with compiz and its seems it's also causing problem with awn,is there anyone who can help me?

laptop:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

laptop:~$ avant-window-navigator
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x380002a (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
You r using ATI aren't u? Ok there has been a bug report that latest updates to Gutsy blacklist the AT1 driver so u have to whitelist it, don't ask me how cause I own an Nvidia card. Used to have ATI and it was nothing but trouble.

Once u have Compiz Fusion running then only can u use Avant Window Navigator as that requires compiz fusion or beryl. 

I will search for that bug report and tell u.

---

### Post by khurrum1990 on 2007-12-08
> **khurrum1990 said:**
> You r using ATI aren't u? Ok there has been a bug report that latest updates to Gutsy blacklist the AT1 driver so u have to whitelist it, don't ask me how cause I own an Nvidia card. Used to have ATI and it was nothing but trouble.

Once u have Compiz Fusion running then only can u use Avant Window Navigator as that requires compiz fusion or beryl. 

I will search for that bug report and tell u.
Here visit these pages for more help.
The first one is a howto:
[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz)
The second one is a thread with a similar problem like yours:
[http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+gutsy+compiz](http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+gutsy+compiz)
I hope this helps.

---

### Post by khurrum1990 on 2007-12-08
> **babygirl said:**
> Both machines run the Nvidia Geforce 7300 GT. They are installed and fully enabled. The only real difference with these machines is my MB has AMD chipset and the other has Intel. I still haven't gotten more than "extra" on it, but would looooove custom on both machines.
Hey is ur compiz fusion working now?

---

### Post by babygirl on 2007-12-08
> **khurrum1990 said:**
> Hi again, ok did ur title bars appear though after running these commands u have to disable desktop effects and restart xserver by pressing Ctrl+Alt+Backspace key. Then login again start desktop effects. If ur title bars r back that great. Your nvidia card is fine.

How much ram do u have?

Have u installed compizconfig-settings-manager? Do that by typing:
sudo apt-get install compizconfig-settings-manager

My system is NOT in question. If it was I would have asked specifics. I build custom systems as a hobbie. I'm running AMD athlon 64 X2 4600+, 1 gig DDR2 533 and will be upgrading that to 4 gigs of DDR2 800, AMD chipset, nvidia Geforce 7300 GT, running on SATA. I do NOT use ANYTHING intel. My housemate/landlord has an intel chipset on his MB and I rarely use it. But it seems his intel chipset is accepting things better than mine, which is odd considering I had an Intel MB and CPU before this, and I had trouble just getting it to boot from live disc. I've NEVER had a good experience with Intel. I sold that MB and CPU 2 weeks after I bought it for half what I payed, and replaced everything with AMD. This is the only problem I've had with AMD, which makes me think I'm screwing up somewhere. :confused:

---

