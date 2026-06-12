---
title: "Display problem"
date: 2005-08-31
forum: Desktop Environments
---

### Post by zaan on 2005-08-31
Hi!
I have just installed the new version of Ubuntu, and love it.
I have just a little problem with my display and its hard to pinepoint 
what the problem might be. 

I first notice it on the fancy login screen, The screen is really dark, or more like
fuzzy. The colors are more really grey. I turned up the gamma with xgamma but that
didnt solve my problem. 

So now i turn to you guys to help me out. I run Ubuntu on a old Toshiba Satellite Pro 4600.  Hope for help

Patrik

---

### Post by shakin on 2005-08-31
You didn't mention if you've used Linux before or not, so if my advice is too complicated just reply that you need it simplified.

I think you first need to check your video driver. You can use gedit to open /etc/X11/xorg.conf and look at which driver is setup. If it says 'vesa' then you are using a generic driver that's used when the installer can't figure out what kind of video card you have. Time to find out what video card your laptop has. Probably ATI or Intel, but check with the manufacturer to make sure. You should be able to easily change the Driver "vesa" part to Driver "ati" or Driver "i810" (use synaptic to install this driver first).

Once you're sure you're using the right driver and after you've rebooted to make sure the change takes effect, and you still have a dark screen, we can start to play around with xorg's gamma settings. In your monitor section in xorg.conf you can add a line something like this:

Gamma 2.5 2.5 2.5

The first number (2.5) is the red gamma, second is the green gamma and third is the blue gamma. See if adjusting those higher results in a better looking picture on your monitor. You'll need to reboot or hit Ctrl-Alt-Backspace after saving your change in order for it to take effect.

---

### Post by zaan on 2005-08-31
thanx for the tips.

I was able to solve the problem by turning my functionbuttons on and pushed the 
button for shared display. ( So you can use the lcd in the laptop and the tv) when i
turned that of the display went crystal sharp

---

