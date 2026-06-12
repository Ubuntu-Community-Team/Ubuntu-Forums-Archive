---
title: "Monitor is not correctly recognized."
date: 2005-10-15
forum: Desktop Environments
---

### Post by Ifaistos on 2005-10-15
Hello everyone :-)

I installed Ubuntu Linux, and updated everything.  I did this with a Nokia 15'' monitor supporting 1024x768.

Now I connected a Solarism 17'' monitor which supports 1280x1024, but Linux does not recognize it, since (I believe) it still believes that I have the Nokia monitor connected.  How can I force a detection of the monitor from scratch.

If this is not the problem, does anyone have any other suggesion?

Thank you in advance for your help :-)

---

### Post by Ampersand on 2005-10-15
Run 
```
sudo dpkg-reconfigure xserver-xorg
``` 
and you'll be given the opportunity to reconfigure your graphics related hardware,

---

### Post by Ifaistos on 2005-10-15
Nope ! I wasn't ready for that :-)

I tried but the GUI could not be loaded...
So I reinstalled Linux from the beginning (right now I am updating files).

The good thing is that the new installation recognized the monitor and now I have 1280x1024.  Problem is that in the future I will not be able to do that!

Isn't there like a program that can graphically let you reconfigure your settings like the one in Windows that you get when you right click on the desktop.

I do understand that Linux is not windows, but I can't be doing this everytime I might change something in my hardware.  In order for the reconfig to work I had to answer a lot of obscure questions which obviously I did not answer correctly.

Is there a program that will show me what Linux has identified as hardware for my machine.  One that would allow me to change settings, drivers etc.  That would be of a great help to a newbie like me, and generally to newbies around the globe.

I believe that one of the fears that people have concerning Linux, is installation!  If installation was out of the way, then only gaming will stop us from completely converting to Linux, which in time, it will eventually happen.

Thank you everyone in advance :-)

---

### Post by Ifaistos on 2005-10-16
bump

---

### Post by jetpeach on 2005-10-17
I completely agree that this should be VERY HIGH priority for the next Ubuntu release.  The sudo dpkg-reconfigure blah blah thing is very helpful and saved me just now, but it is extremely suboptimal.  An "advanced mode" needs to be added to the screen resolution customization in gnome where monitor refresh rates can be set- these refresh rates should be tested and if the hardware is not compatible it defaults back to a lower resolution/slower refresh rate.  I've mentioned this before, apparently many people don't feel it is a big deal (perhaps they are all using LCDs and 60hz is not blinding them, as it does to me on my CRT.)
jet

---

### Post by Sleeper Service on 2005-10-29
Agreed.

I work for an organisation that recycles older computers and installs them with Linux.  I've installed probably around 40 different machines with Ubuntu in the last year or so; with Warty, Hoary and now Breezy.  These machines are only around 2-4 years old and there's a range of hardware, but I've found Ubuntu to be quite inconsistent in how it picks up and configures graphics cards and monitors.

By contrast, Mandrake/Mandriva (the other distro we regularly use) seems to get it right almost always on the same hardware.

So it can't be an insurmountable problem.

---

### Post by xs650 on 2005-11-04
[QUOTE=Ifaistos]Nope ! I wasn't ready for that :-)
at!

Isn't there like a program that can graphically let you reconfigure your settings like the one in Windows that you get when you right click on the desktop.

 but I can't be doing this everytime I might change something in my hardware.  In order for the reconfig to work I had to answer a lot of obscure questions which obviously I did not answer correctly.
[/QUOTE]

I'm a newb myself and had resolution problems because the 5 year old 1280x1024 LCD monitor wasn't recognized so the best resolution the standard setup would let me have was 1024x768 @ 60hz

After trying lot of things I finally fixed it by manually editing the etc/X11/xorg.conf file HorizSync and VertRefresh lines (new values shown in red) to match my monitor specs. Your rates will probably be different.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       [COLOR="Red"]31.5-80[/COLOR]
        VertRefresh     [COLOR="Red"]56.3-75[/COLOR]
```

Then I added the 1280x1024 resolution (added values shown in red)  to all 6 mode lines, one of which is shown below. You may need to add something different.
```

SubSection "Display"
                Depth           24
                Modes          [COLOR="Red"] "1280x1024"[/COLOR] "1024x768" "800x600" "640x480
```"

It sounds like a PITA, but once you learn you way around one the many editors available in UBUNTU it's pretty quick. And, the good news is that by making the above changes, abunch of option between 1024x768 and my new iupper limit show up in system/prefrences/screen resolution. I suspect that my monitor won't support some of them and you need to be sure you don't overdrive and old CRT monitor or you might fry it.

From a practical standpoint, I have learned in the couple of days I have been trying to use Linux that if one isn't familiar with using an editor as su they need to learn how to use one to survive.

---

