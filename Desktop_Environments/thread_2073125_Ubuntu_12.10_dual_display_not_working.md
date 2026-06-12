---
title: "Ubuntu 12.10 dual display not working"
date: 2012-10-19
forum: Desktop Environments
---

### Post by Lukens on 2012-10-19
Hello, Im trying to get my dual displays to work, and im not having any luck. Ive searched the forums and googled away, but havent found anything close to what im trying to fix.

I have a laptop and an external monitor, an Acer x193w. It works great with my windows installation, but not my Ubuntu.

When I try to activate my second monitor, it spouts an error message: 

The selected configuration for displays could not be applied
required virtual size does not fit available size: requested=(2720, 900), minimum=(320, 200), maximum=(1600, 1600)

And then

failed to apply configuration:%s
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: required virtual size does not fit available size: requested=(2720, 900), minimum=(320, 200), maximum=(1600, 1600)

I cant make heads or tails of these error codes. Im still pretty new to Ubuntu, so forgive me if its something trivial.

Anyone have any ideas? Id love to be able to use my Ubuntu with dual monitors. Its killing me to go back to one.

---

### Post by amaz1ng on 2012-10-28
Hey Lukens, I'm in the same boat as you. I've heard people suggest all kinds of solutions, but I haven't had any luck with them. As for the error codes, I'd suggest taking a quick peek at my screenshot here: [http://ubuntuforums.org/showthread.php?t=2076972&highlight=dual+monitors](http://ubuntuforums.org/showthread.php?t=2076972&highlight=dual+monitors)

RandR is a little tool which helps you visualize where your monitors are placed in regards to where you're allowed to place them. You might try looking at that, if only to get a small idea of what those error codes are saying!

---

### Post by keelzebub on 2012-10-31
Try setting the virtual screen size in /etc/X11/xorg.conf by adding the following lines inside of the "screen"  section (if you have a "display" section already, just add the "Virtual" line):

```

Subsection "Display" 
     Virtual 4096 4096
EndSubsection

```This should set your maximum virtual screen size to 4096x4096. (I've read several posts that say to set it to the size you're  requesting, but my own card wouldn't accept anything except multiples of  1024, it seems.)

Then just restart your computer. If it works, make sure to save a copy of it - some people have reported that sometimes their xorg.conf gets overwritten, so it's smart to have an easy way to restore it.

---

### Post by amaz1ng on 2012-11-27
Thanks keelzebub! Your solution worked for me. Now I can look at linux through my two monitors. (Note: remember to change your setup in ARandR to the appropriate one).

---

### Post by stoffisimo on 2012-12-16
> **keelzebub said:**
> Try setting the virtual screen size in /etc/X11/xorg.conf 

[...]
If it works, make sure to save a copy of it - some people have reported that sometimes their xorg.conf gets overwritten, so it's smart to have an easy way to restore it.

Yeah, this worked as a charm and helped me solve my problem with my two displays. Thanks! :)

But, I believe it is better to set the virtual screen size in /usr/share/X11/xorg.conf.d/ instead of the xorg.conf-file (as long as you are missing the xorg.conf file anyway).
That way it shouldn't be overwritten by anything.

I created a new file, **/usr/share/X11/xorg.conf.d/20-custom_display.conf** where I inserted the following:
```
Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   4096 4096
        Depth     24
    EndSubSection
EndSection
```(The rest of the section is stolen from [http://smotko.si/the-amd-linux-drivers](http://smotko.si/the-amd-linux-drivers). Note that this is just an example that might work if you have an AMD/ATI-video card )

---

### Post by Halba on 2013-01-20
I have the same problem as the original poster. there is no xorg.conf file. so what do i do? i also created the new file in nautilus as [stoffisimo]("http://ubuntuforums.org/member.php?u=1766651") said. still didn't work and i come up with the same error message. i still can't get dual displays, only mirrored display. it worked fine in WIN XP but not on ubuntu =(

---

### Post by ghost1227 on 2013-01-28
Adding a bare-bones Xorg.conf results in X not loading at all :( Thoughts?

---

### Post by CodeNosher on 2013-01-28
I had/have the same problem mine.  I've got the intel 945gm/gms card in my old Toshiba.

I added the bare-bones Subsection only xorg.conf and my screens refused to display anything.

I booted in recovery so I could get rid of the xorg.conf.

I noticed it said to "rearrange the displays so that they fit..."  So, I rearranged them.  I put the secondary on top and the laptop on bottom.  Low and behold, it worked.  

I'd like to have the side by side option, but I don't have the energy to dig into it, so I'll leave it like this.

---

### Post by lebaghaloo on 2013-05-06
i tis saying i dont have the permission to change it :/

---

