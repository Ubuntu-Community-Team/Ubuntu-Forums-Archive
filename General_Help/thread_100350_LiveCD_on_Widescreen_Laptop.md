---
title: "LiveCD on Widescreen Laptop"
date: 2005-12-07
forum: General Help
---

### Post by 3nigma on 2005-12-07
Hi Guys,

Thanks for your help so far in introducing me to Ubuntu.

I have burned a LiveCD successfully, and have run it on a desktop flawlessly.

However, when I try to run it on my 17" widescreen laptop, it has problems detecting the display graphic configurations.  Here's what happens:

I boot w/ the LiveCD.  It goes through the process, and eventually reaches the "Preparing Live Session" loading.  When it reaches 65% at "Configuring Graphic settings (the screen may blank)...", it blanks.  Then, I'm prompted to select what resolutions I want it to run in.  (When running on a desktop, it just works perfect.)

Now, my laptop's resolution is 1440x900, which obviously is not the norm.  The only other options it can do is 1024x768, and 800x600.  When prompted to choose resolutions, it says choose the available ones, and it will use the highest by default.  It's unclear if it wants me to select the ones I want to use, or select all the ones I *don't* want to use.  I've tried it both ways, and neither works.

It goes to the Ubuntu loading screen and afterward says "Couldn't configure Xserver with graphic configuration settings.  Would you like to see details?"  Then before I can hit 'yes' or 'no,' the screen starts wiggin' out w/ lines of text randomly spurting at the bottom of the screen, etc.

The disc works fine in a desktop, though.

Any ideas?  *shrug*

Thanks
-3nigma

---

### Post by 3nigma on 2005-12-10
^bump^

No help for the n00b?  =(

---

### Post by nelposto on 2005-12-10
Hi 3nigma,

I also have a widescreen (Dell 9300) laptop which I tried the LiveCD on. However I had no problems with it detecting my resolution.. in fact it's the only Live distro I've tried (of a whole 3, admittedly) that has gone straight to native 1920 x 1200 resolution.

However, I did have to quote an option at boot 'vga=771'. This may help you, I don't know.

For that, when it comes up with the press enter to boot part, you would type "live vga=771"

What happens when after the Xserver fails to start? Have you any control over the laptop?

---

### Post by soulestream on 2005-12-10
what kind of video card do you have?

I have never bothered checking (if possible) on a live cd, but you will need to make sure you video card configured in xorg.conf. If the 'vesa" driver is loaded then you will be limited to 1024x768. 

You will also need to add 1440x900 as an option and may have to set your hsync and vsync settings for your screen. 

/etc/X11/xorg.conf

I have a 15.4 laptop @ 1280x800 and the install system, setup the card/monitor correctly. 

soule

---

### Post by 3nigma on 2005-12-10
This stuff sounds good and like it may work, I'll give it a shot.

I have an ATI Radeon X700 mobile graphics card (laptop), with 64 MB dedicated, PCI express (I believe).

Thanks guys!

---

### Post by bcollignon on 2006-08-27
Same problem with a ViewSonic N2050w, starts up to load menu, but the monitor goes flaky when GNome starts.  Display reads NOT SUPPORTED, which translates to out-of-spec refresh rate/resolution, I would assume.  How do you change the refresh rate from the command line at boot?

---

