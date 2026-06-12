---
title: "Dell Ultrasharp 3007WFP"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by fastnoc on 2007-07-06
Boy, I'm frustrated.

This is the first time I've ever installed Linux as a GUI. I've been managing Linux servers for a little over 9 years but never used them at home.

After some research it looks like Ubuntu is the best choice for me. But I've run into a problem I can't solve.

No matter what I do I cannot get ubuntu to run separate displays for my monitors. I have a dell 30 inch and a generic 17. The ONLY way I can get these working is if I set them up to be one big display. Well I'm sure it's obvious that's not going to work with that small and that large of monitors.

I've searched everywhere I can find and cannot find any help on this. I did locate one thread somewhere else where the user had the same problems but nobody responded.

Here's what happens when i try to configure things to use two different monitors:  (this is using the nvidia applet)

> 
root@ubuntu:/home/*******# sudo nvidia-settings &
[1] 6500
root@ubuntu:/home/******# 
ERROR: Unable to determine valid vertical refresh ranges for display device
'DELL 3007WFP' (GPU: GeForce 7900 GTX)!


ERROR: Failed to add display device 'DELL 3007WFP' to screen 1!


ERROR: Failed to add X screen 1 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file! 


If anyone can help me I'd sure appreciate it. THe other problem I have is my Soundblaster X-FI platinum doesn't have drivers but from what I gather this is th fault of creative. I've got a generic 7.1 with my mobo so i think I'll be ok there. If I can just figure this out.

Also, I downloaded the new nvidia drivers but I can't install them. I get errors saying it couldn't find my kernel. I assume I'd be ok with what comes with ubuntu's install.

Oh, the video card, if that matters, is nVidia 7900GTX 500MB

---

### Post by fastnoc on 2007-07-06
One thing I should say.

The ubuntu install process is by far the best I've ever seen. Loading a stripped version in a ramdrive allowing me to browse the web while the install is going is just beyond cool. :)

Lots of other great things so far. Just need to get this monitor issue done and i'll wipe my dual boot (which was flawlessly created by the install. I thought I'd have to edit the boot) and say goodbye to vista

---

### Post by fastnoc on 2007-07-06
Nobody can help this?

Should this be moved to a different area? I'd like to get a little help here. I've searched everywhere I could think.

---

### Post by Rocket2DMn on 2007-07-06
Dual head is still a problem for a lot of people in linux, myself included.  Limited support for graphics cards makes life difficult when you want more than just a simple screen to work on.  NVIDIA tends to have better support, but sometimes it's just not possible - you can search threads and try different approaches, or here is a basic HowTo with no guarantees
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If you are stuck without a GUI right now, you can reconfigure your xserver with:
```
sudo dpkg-reconfigure xserver-xorg
```

If you can only end up with one screen working, all is not lost.  I have found that the advantages of having multiple "workspaces" is almost as good as having dual monitors - less minimizing and covering up the screen with dozens of windows.  Although you can't view it all at once like with dual monitor, you can switch workspaces very easily.

I think people are afraid to offer help because you seem so experienced with linux.  Keep us updated and we will try to keep helping (don't give up on dual head QUITE yet).

---

### Post by Soybean on 2007-07-06
> **fastnoc said:**
> Should this be moved to a different area?
Possibly. I believe the "Ubuntu Dell Support" is aimed at the new Dell systems that come with Ubuntu preinstalled. As for where would be better... probably either "Hardware & Laptops" or "Desktop Environments" (since it's really mainly an X configuration issue). I think the sort of people who know a lot about this sort of thing are more likely to frequent those areas.

> **fastnoc said:**
> The ONLY way I can get these working is if I set them up to be one big display. Well I'm sure it's obvious that's not going to work with that small and that large of monitors.
Just to throw my opinion in here... why won't that work? It's what I would do, personally. Matching sizes is nice, but isn't a requirement by any means. Gnome + Metacity + Xinerama/TwinView handle it pretty well by default... the "maximize" button enlarges the window to fill only the current monitor, for example.

If you really want the two monitors to be separate, it's definitely possible, but I don't have any experience with that sort of configuration. It's good that you have Linux server experience, though, because you'll need to tweak your /etc/X11/xorg.conf file by hand, and if you do something wrong, you'll end up without a GUI until you can sort it out. ;)

I'd recommend starting by getting X working on just one monitor, then just the other one, making a backup of both config files. That way you know you've got the right timing and resolution settings and such. X can be pretty finnicky, so it's good to minimize the possible points of failure at any one time.

Alternately, if you can get one of those "one big display" setups working successfully, THAT config file might also be a good base for switching to the configuration you want. 

Once you're in either of those positions (either two separate working single-head configs, or one working Xinerama or TwinView config), if you're not sure how to proceed, you could try posting your xorg.conf file(s) to one of those other forum sections (Hardware & Laptops or Desktop Environments). I can't guarantee that someone will be able to help, but I've seen that work a few times for different people with similar problems. :)

> **fastnoc said:**
> Also, I downloaded the new nvidia drivers but I can't install them. I get errors saying it couldn't find my kernel. I assume I'd be ok with what comes with ubuntu's install.
Yeah, downloading the drivers (from the web, I assume?) is rarely the way to go in Ubuntu. In the case of NVidia cards, they usually work very nicely with the restricted drivers (System-Administration-Restricted Drivers Manager).

As for the sound card issue... I have no idea, but I'd post about it separately. Probably in Hardware & Laptops.

---

