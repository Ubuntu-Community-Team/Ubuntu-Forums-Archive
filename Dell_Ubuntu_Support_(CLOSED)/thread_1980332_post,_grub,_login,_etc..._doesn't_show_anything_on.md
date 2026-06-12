---
title: "post, grub, login, etc... doesn't show anything on laptop display."
date: 2012-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BryanFRitt on 2012-05-15
Nothing shows up on the laptop display when I boot/post. If I hook up an external monitor, the external monitor will display the please swipe finger, etc... that should be shown on the laptop's display itself. If I go past that screen into Ubuntu, it doesn't display anything on the laptop, and the external monitor says the resolution/refresh rate is too high for it. (I normally don't use external monitors, and I have my computer/terminals set to 1920x1200(which is the resolution of the laptop), but the external ones that I have access to can't do that resolution, so the monitors are saying they can't handle the resolution/refresh rate)
If instead I switch over to the laptop's Windows Vista, once Vista starts, the laptop's display will come up fine. Post, and grub menu are still only showing up on external monitor.

Main issue:
Basically, the boot display, and fingerprint, grub menu, etc... are going to the secondary display, and not showing up on the laptop itself. (even if I unhook the external monitor, and restart.)

Secondary issue:
External monitor resolution isn't being detected/adjusted for in Ubuntu?

p.s. My labtop's a Dell Latitude D830, Nvidia NVS 140M 256MiB Video Card, ...

---

### Post by lisati on 2012-05-15
If POST is affected, it's possible that there's a BIOS setting somewhere that has been messed up instead of a Windows or Ubuntu setting. I'm not familiar with how it would be done on that particular model, but would be tempted to reset BIOS to default settings.

---

### Post by BryanFRitt on 2012-05-15
I've tried resetting the BIOS, that didn't fix it. 
Then I tried reinstalling the BIOS, A15. That didn't change anything; 
But I noticed that in the BIOS it says:
[FONT="Courier New"]Panel Type = unknown device installed
Native Resolution = 0 by 0[/FONT]
I'm sure it's a WUXGA display, 1920x1200.

So I guess this is the issue: 
The BIOS isn't detecting the laptop's display correctly anymore.
(The laptop's display is working in Vista)
I guess that'll have to be something I have to contact Dell about?

Is there anyway to adjust Ubuntu resolution settings so I can use Ubuntu on this external monitor?, for more than just POST, and GRUB? 
I can still use my computer to get into Vista.

(I think the external monitor might be a 1024x768 monitor, but I'm not sure. I might be able to alternate with 1920x1080 monitor later(note: that's not equal to the current setting of 1920x1200))

---

### Post by BryanFRitt on 2012-05-15
I just emailed the Dell tech person I had called before I tried the external monitor (He had suggested I order a new display, or try an external monitor):
my new email to him:
> I've done/figured out a few things since I've called.
I've hooked up an external monitor, which helped me to get into Vista, where apparently the laptop display works! Although, still no POST, and BIOS screens on the laptop's display.
I've tried the 'D830_A15.EXE' BIOS update. (I already had that one installed from a long time ago)
I've went into the BIOS and found it saying:
[FONT="Courier New"]Panel Type = unknown device installed
Native Resolution = 0 by 0[/FONT]
and I've posted a message here:
[http://ubuntuforums.org/showthread.php?p=11938383](http://ubuntuforums.org/showthread.php?p=11938383)

Why isn't the BIOS detecting the laptop's display? and/or How to fix it?

---

### Post by BryanFRitt on 2012-05-19
Vista seams to work fine even though the POST, BIOS, and GRUB end up going to second monitor, and NOT going to the laptop's display.

When the GUI part of Ubuntu starts, it looks like it's going to the laptop's display(because it lights up) instead of the external monitor, but nothing shows, and the external monitor now says no signal. 

When the Ubuntu GUI is supposed to be showing, I can '[FONT="Courier New"]Ctrl+Alt+F1..F6[/FONT]' and the laptop's display will cut off, and the external monitor will show the tty session. Going back to GUI '[FONT="Courier New"]Ctrl+Alt+F7[/FONT]' will cut off the external and turn on the laptop's display, but it'll still be blank.

All this happened at once, the POST, BIOS, and GRUB, etc... issues. I'm guessing there's something wrong with the BIOS. I've tried flashing it, and resetting it's settings. (had to use an external monitor to display the BIOS).

I've tried running a LiveCD, and it's got the same problems.

*Despite this, Vista still works, like nothing happened. Is there some kind of workaround that I can get Ubuntu GUI to work like nothing wrong happened too?*

Any ideas on migrating to Vista, and adding a VirtualBox of my Linux partition, or doing something else in this situation...?

I don't really want to buy a new computer until Windows 8 comes out. (not that I'm really into Windows 8, It's just that when I decided to buy a new computer)

---

### Post by BryanFRitt on 2012-06-02
I got it working again... 
I switched laptop display's with someone who had a WUXGA on a Latitude D820. (I had a WUXGA on a Latitude D830)
This fixed the POST, BIOS and Ubuntu login not showing up on my laptop.

I also had to remove the current [FONT="Courier New"]~/.Xauthority[/FONT] to login the the Ubuntu GUI. (I could still log into Ctrl+Alt+F1..F6, just not the GUI one(s?) Ctrl+Alt+F7..F12)
(guess this maybe because I powered off at the wrong time?, like when I was trying to login blind?, sounds like something that could be autofixed?)

If your feeling cautious you can 'mv' instead of 'rm'
[FONT="Courier New"]sudo mv ~/.Xauthority ~/.XauthorityBackup[/FONT]
or just straight up
[FONT="Courier New"]sudo rm ~/.Xauthority[/FONT]
[http://askubuntu.com/questions/66482/cant-login-after-installing-11-10](http://askubuntu.com/questions/66482/cant-login-after-installing-11-10)

---

