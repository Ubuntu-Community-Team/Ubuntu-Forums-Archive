---
title: "Latitude E6500  and Docking station"
date: 2009-04-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lichtgestalt on 2009-04-06
Hi,

I got a Dell Latitude E6500 and every thing works just fine out of the box. It's really great! 

Now I'm thinking about buying a Docking station. I never before tried using one with Linux. How well are they currently supported? Is there a undock button somewhere? Can I use multiple monitors attached to the docking station?

Does anyone have some experience?

---

### Post by siouzi on 2009-04-06
I'm using E4300 with a basic dock (vga, dvi, 5 usb etc) and it seems to work just fine as a hardware extension. Dock's headphone/speaker jack won't mute the laptop speakers with this model, but adding one line to the alsa config can "fix" this (laptop speakers will be always muted...).

Biggest problem may be the external monitor(s) if E6500 also uses Intel graphics. Be prepared to spend a lot of time configuring xorg.conf and trying to get decent FPS with compiz and then giving up :/ This doesn't have anything to do with the dock so if your external monitor works fine without the dock it will work fine with the dock.

There is an undock button but there is no "out of the box" support for reconfiguring desktop resolution if you undock while running (have to logout/restart X). Still, I think it's quite convenient because you'd always have to plugin/plugout at least 4 or 5 cables (power, network, monitor, mouse and maybe a keyboard).

---

### Post by lichtgestalt on 2009-04-06
Thanks!

I don't think the monitor will pose a big problem. The laptop has an nvidia chipset and connecting a monitor online works perfectly.

---

### Post by windfix on 2009-04-28
I am using the E6500 with a dock and twin 20" LCDs.  I have some advice:

First, the Display applet does NOT work with the NVidia video card.  You have to use the NVIDIA setting applet, which requires login every time you use it.

Second, back up your /etc/x11/xorg.conf file, because only the original one has ever worked for me.  Do NOT push "Save to X Configuration File" in the Nvidia applet, because it will hose your file.

Third, docking and undocking are a pain with twin monitors, but here is how I finally (after hours of cursing) got it to work predictably:  

When undocking, log out first.  Your dipslay should go back to the laptop without incident.

After docking, open Nvidia's X Server applet.  In X Server Display configuration, Enable one external monitor with the Configure button - set it to Twinview.  Next, disable the onboard screen (called LPL 1280x800) and confirm the disable.  Finally, enable the second external monitor to twinview.  Last, hit Apply - then confirm the change within the 10-second window.

If anyone has better advice on making this work better, I'd love to hear it - but at least this process is predictable.  Deviate, you'll get one screen stretched across both monitors; or will be unable to get the display back to the laptop when undocking.

---

### Post by bobuse on 2009-08-17
Hi, I've tried today my new docking station with my E6400.

I've an intel graphic card, and the configuration switch is easily achieved with xorg. I've wroten that in a script that is launched by powerdevil (kde tool) when I switch to my created "Dock" profile, and configure my two LCD and power off my laptop screen. All is fine.

But, I've still a problem with the sound. I confirm that the laptop speakers are not muted, but external speakers doesn't work either I plug them directly in the laptop or in the dock ! (I've tried with 2 speakers known to work).
EDIT: I've found the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307086")

---

### Post by tramir on 2009-09-21
Is there a way to automate this? What I mean is that right now I dock the notebook, turn it on (during which the external monitor works), then boot up ubuntu (which disables the external monitor), open the lid to enable the external monitor, and then leave the lid open (if I close it, the computer hibernates, which is what is supposed to do). It kind of defeats the whole purpose...  Is there a way to  not have to open the notebook after docking?

---

### Post by Turbo6868 on 2009-09-24
Perhaps, tell the computer to not hibernate on lid close if on AC power.  That way, if its in the dock, it will just blink the display but not hibernate.  (This is what I do).  If only I could get it to use the Laptop display with the external (dock) display without crashing X.... but thats for another post.

Just offering something that might help ya.

---

