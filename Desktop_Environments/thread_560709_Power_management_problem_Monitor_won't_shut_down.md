---
title: "Power management problem: Monitor won't shut down"
date: 2007-09-26
forum: Desktop Environments
---

### Post by Vesa Paatero on 2007-09-26
Hi,

I have Edubuntu 7.04 running on a normal (non-laptop) computer and I can't get my monitor to go off (or to power-saving mode) automatically after idle time. The help texts of the power management program gave this instruction:

"You have to change the DPMS mode GNOME Power Manager uses.
Open gconf-editor, and then change the keys
/apps/gnome-power-manager/ac_dpms_sleep_method and
/apps/gnome-power-manager/battery_dpms_sleep_method
to one of the modes that work, e.g. standby, suspend or off."

I've tried all of those and reset the computer after changing, but to no avail. The display is a flat Hitachi ... I don't know when it was first purchased but it has the "TCO 99" certification sticker on it.

Any ideas?  Thanks...

Regards,
  Vesa Paatero

---

### Post by Vesa Paatero on 2007-09-27
Oh,  in case it makes any difference: My version of Edubuntu is 64-bit, running on an AMD dual-core platform.

---

### Post by glotz on 2007-09-27
I don't know much about the issue but there are some related settings in the BIOS, have you checked them? (and you can edit your own posts btw)

---

### Post by Vesa Paatero on 2007-10-12
Thanks, I checked BIOS settings but they seemed OK:

- ACPI Suspend Type:  [S1&S3]    (Possible alternatives: "S1 (POS)" and "S3 (STR)"
- ACPI APIC support: Enabled       (Gray, could not be changed)

-Power on By External Modem:  [Disabled]
-Restore on AC Power Loss  [Power Off]
(and other "power up on ..." and "power up by..." settings regarding keyboard, mouse etc,)

Any more ideas? The motherboard is ASUS M2A-VM. It supports both traditional RGB connection and DVI-D. I'm using the traditional connection.

Thanks for any help.

-Vesa

---

### Post by zoryn on 2007-10-14
I'm having this problem, but I'm using Gutsy. Feisty didn't have this problem.
Sometimes it even shuts down, then suddenly wakes up and never shuts down again. Weird.
Ubuntu Gutsy 64.

---

### Post by shields on 2007-10-24
I too have this problem.  It worked in Feisty, but when I did the upgrade, my monitor decided to stay on.  Has anyone solved this? :confused:

---

### Post by xjpvictor on 2007-10-24
is it the problem of ur graphic card driver? i'm using Gutsy and i have the same prob when i use vesa driver, then i change to another intel driver, my LCD can turn off automatically. so i think maybe u wanna change ur the graphic card driver according to ur graphic card.

---

### Post by shields on 2007-10-24
My graphics card is an NV5M64 [RIVA TNT2 Model 64/Model 64 Pro].  PCI

When I look at Restricted Drivers Management, the only other driver available for it is one that is not supported.  When I use it, I loose resolution options, finding 800x600 the highest res. 

The weird thing is that it worked fine for Feisty.  Doesn't work for Gutsy.

---

### Post by xjpvictor on 2007-10-25
can u try this:
edit /etc/X11/xorg.conf and add
> HorizSync 31-86
VertRefresh 50-160
in the Section "Monitor"

---

### Post by shields on 2007-10-25
There is no /etc/x11/ directory.

---

### Post by xjpvictor on 2007-10-25
is /etc/X11
not /etc/x11

---

### Post by shields on 2007-10-26
It's working now.

I went into /usr/share/xresprobe/xorg.conf and added this line
```
Option		"OffTime" 	"10"
```
to the Section "Monitor"

I dunno if that fixed it or if one of the recent updates did, but in any case, it's working now.

Thanks for your replies. :)

---

### Post by shields on 2007-10-29
As time goes by, I see that this did not solve the problem.  Sometimes it shuts down the monitor, other times it does not.  Moreover, this afternoon a reboot caused the monitor to come up in a very high resolution (1280x1024).  When I go in and change it, it doesn't change.  It stays in that resolution.  This thread [http://ubuntuforums.org/showthread.php?t=595073](http://ubuntuforums.org/showthread.php?t=595073) addresses that problem, but it seems there is no solution.

:(

---

### Post by bingoUV on 2007-10-29
Vesa Paatero,
    What happens when you run the following command from a terminal within your desktop? If it works properly, the monitor will immediately power off. Just move mouse/press key to bring it back to life.
```

xset dpms force off

```

If this does not switch off your monitor, DPMS may not be compiled in your X server.

---

### Post by shields on 2007-10-29
Thanks.  

That shuts it off quite nicely.  Moving the mouse turns it back on -- so that's not the problem.  (sigh)

---

### Post by bingoUV on 2007-10-30
Then just do the following in your X startup script, or after graphical login. 
```

xset dpms 120 300 1800

```

This will turn the monitor to standby after 120 seconds of inactivity, suspend after 300 seconds of inactivity, and shutdown after 1800 seconds of inactivity. Most monitors that I know of do not support three different kinds of power savings, so all these values can be the same too, depending upon your monitor. 

Let me know if you need help regarding identifying your X startup script.

---

### Post by shields on 2007-10-30
> **bingoUV said:**
> Then just do the following in your X startup script, or after graphical login. 
```

xset dpms 120 300 1800

```
...
Let me know if you need help regarding identifying your X startup script.

LOL -- yes.  I need help identifying my X startup script.

Thanks!

---

### Post by chuvisco on 2007-10-30
Try adding
```
Option        "DPMS"
```
to the Monitor section of /etc/X11/xorg.conf.  I think this is usually there by default, but for some reason it was not there in my Gutsy install.

---

### Post by bingoUV on 2007-10-30
What do you log in to (Gnome, KDE, XFCE etc.?). 
Easiest option is :  add the command in your ~/.bashrc, but it is bad , only because it will run needlessly every time you open a terminal. Not that it causes any harm. It will also give an unnecessary error when you log in from non graphical terminal.

Otherwise, distros play with the X startup script a lot. I believe, in Ubuntu , you could add it in ~/.gnomerc, if you run Gnome. 

If it does not work, try ~/.xsession.  This was used by old fashioned distros (debian and redhat of yore).

Do let us know which one worked.

---

### Post by chuvisco on 2007-10-31
Something strange is happening.  I can use xset as mentioned by bingo above, and the settings stick and work, but all three parameters revert to 0 after a few minutes (check this with xset q), therefore disabling DPMS.  Why is this?

---

### Post by bingoUV on 2007-10-31
> **chuvisco said:**
> Something strange is happening.  I can use xset as mentioned by bingo above, and the settings stick and work, but all three parameters revert to 0 after a few minutes (check this with xset q), therefore disabling DPMS.  Why is this?

Are you playing video in those few minutes? mplayer is known to try to stop screen from going to screensaver or power off, but I am not sure. Some such program might not set the configuration back.

---

### Post by vmaric on 2007-10-31
hi everyone .

I just upgraded ubuntu feasty 7.04 on version 7.10 and i have a litl problem like in 7.04
i havent sam things, like a can not see battery on gnome panel and i cant put it there.

meesage of my ubuntu is:

The panel encounterd a problem, while loading. (And when reboot it I have same things)

OAFIID:GNOME_MixerApplet_BattstatApplet

Have somebody eny idea?

I reinstall gnome-panel and gnome-panel-data and it dont help my!
:confused:

---

### Post by chuvisco on 2007-10-31
vmaric, you're probably better off posting your question in a new thread (or one related to  your issue, perhaps in the Laptops subforum?).

No, I'm not playing video, but I did make some progress in narrowing down the problem:

The DPMS settings work the first time.  It is when the monitor comes back *on* (upon moving the mouse or hitting a key) that all three parameters are set to 0.  I figured this out with the help of a little script I wrote to monitor the DPMS settings (is there a real log file for this?).  I do have to leave the monitor off for 30 s to 2 min. to see this--that is, if I bring the monitor back quickly (within 30 s - 2 min.), the parameters are not set to 0.  But *every time* I leave the monitor off for at least 2 minutes, this happens.  I didn't have this problem with previous Ubuntu releases.

shields and zoryn, can you confirm this?  bingo and others, any ideas?

---

### Post by vmaric on 2007-11-01
Thenks for answer!
I think thet is non functionality(like bug) of ubuntu feisty 7.10.
maybe problem disappear with update.
Thenks anyway!!!

---

### Post by Vesa Paatero on 2007-11-01
> **bingoUV said:**
> Vesa Paatero,
    What happens when you run the following command from a terminal within your desktop? If it works properly, the monitor will immediately power off. Just move mouse/press key to bring it back to life.
```

xset dpms force off

```

If this does not switch off your monitor, DPMS may not be compiled in your X server.


Thanks for writing. The command did nothing in my system.  I tried "locate dpms" and "locate DPMS" but found nothing. Should I have found something?  Anyway, the file /usr/share/xresprobe/xorg.conf contains these three lines:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
 
Maybe I should check for some drivers when time permits.

Regards,
Vesa

---

### Post by shields on 2007-11-03
> **chuvisco said:**
> 
The DPMS settings work the first time.  It is when the monitor comes back *on* (upon moving the mouse or hitting a key) that all three parameters are set to 0.  I figured this out with the help of a little script I wrote to monitor the DPMS settings (is there a real log file for this?).  I do have to leave the monitor off for 30 s to 2 min. to see this--that is, if I bring the monitor back quickly (within 30 s - 2 min.), the parameters are not set to 0.  But *every time* I leave the monitor off for at least 2 minutes, this happens.  I didn't have this problem with previous Ubuntu releases.

shields and zoryn, can you confirm this?  bingo and others, any ideas?

When I run ```
xset dpms force off
``` and let it sit for a couple minutes then move the mouse, it comes back on.  Running the same code again within a few seconds makes it go off for a moment, then come back on by itself.  Then running the same code a few minutes later makes it go off and stay off until the mouse is moved or a key is pressed.

Too weird.

---

### Post by chuvisco on 2007-11-03
It seems that my monitor turns off as expected when the screensaver is enabled.  When the screensaver is disabled, my monitor stays on regardless of the setting in Power Management > Display.

---

### Post by chuvisco on 2007-11-04
> **Vesa Paatero said:**
> Thanks for writing. The command did nothing in my system.  I tried "locate dpms" and "locate DPMS" but found nothing. Should I have found something?  Anyway, the file /usr/share/xresprobe/xorg.conf contains these three lines:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
 
Maybe I should check for some drivers when time permits.

Regards,
Vesa

DPMS has been enabled by default in Ubuntu for a long time.  Some LCD monitors can be stubborn, though.  You could experiment with vbetool.  For example, try:
```
sudo vbetool dpms off
```
But note that the screen will not come back with mouse or keyboard activity.  You need to do
```
sudo vbetool dpms on
```
to get the screen to come back on.

---

### Post by shields on 2007-11-05
> **chuvisco said:**
> It seems that my monitor turns off as expected when the screensaver is enabled.  When the screensaver is disabled, my monitor stays on regardless of the setting in Power Management > Display.

Mine does not stay off as expected when the screensaver is enabled. 

In fact, I enabled a screensaver option called "distort" and watched it become active.  When the screensaver began to run it immediately stopped and the screen became normal.  I don't think it ran for more than one second.

---

### Post by chuvisco on 2007-11-05
> **shields said:**
> Mine does not stay off as expected when the screensaver is enabled. 

In fact, I enabled a screensaver option called "distort" and watched it become active.  When the screensaver began to run it immediately stopped and the screen became normal.  I don't think it ran for more than one second.

Yes, I had that problem right after enabling the screensaver.  Logging out and then logging back in corrected it for me.

---

### Post by Vesa Paatero on 2007-11-07
> **chuvisco said:**
> DPMS has been enabled by default in Ubuntu for a long time.  Some LCD monitors can be stubborn, though.  You could experiment with vbetool.  For example, try:
```
sudo vbetool dpms off
```
But note that the screen will not come back with mouse or keyboard activity.  You need to do
```
sudo vbetool dpms on
```
to get the screen to come back on.

Hey, it works!  :-)   The commands switched my monitor off and on ... I wonder if there is any way to make a viable system out of them. Could they be connected to the normal screen saver / power-down mechanism?  The sudo requirement seems problematic. Could it be circumvented by a root-owned daemon process that would execute the sudo-requiring commands as triggered by a (non-root) user application..?
Thanks, Chuvisco.

Vesa

---

### Post by chuvisco on 2007-11-07
> **Vesa Paatero said:**
> Hey, it works!  :-)   The commands switched my monitor off and on ... I wonder if there is any way to make a viable system out of them. Could they be connected to the normal screen saver / power-down mechanism?  The sudo requirement seems problematic. Could it be circumvented by a root-owned daemon process that would execute the sudo-requiring commands as triggered by a (non-root) user application..?


There's a script at the bottom of [this page]("http://gentoo-wiki.com/HOWTO_Automatically_turn_off_your_monitor") that should give you a start.

---

### Post by Ux64 on 2007-11-15
I think that tips in this thread will fix my Ubuntu 7.10 64 bit DPMS problem too.

**DPMS Screen blanking should be one check box and that's it.**

Option DPMS and OffTime were missing from xorg.conf in my case. 

 - Thanks for tips

---

### Post by shields on 2007-11-15
> **chuvisco said:**
> It seems that my monitor turns off as expected when the screensaver is enabled.  When the screensaver is disabled, my monitor stays on regardless of the setting in Power Management > Display.

Yes. This works.  It didn't at first, but a reboot caused it to work well.

It's been working for more than a week.

Thanks chuvisco.

---

