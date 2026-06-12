---
title: "Close lid behavior on laptop with external monitor."
date: 2009-10-31
forum: Desktop Environments
---

### Post by Axios on 2009-10-31
Hi

Summed up, I think I need a 'do nothing' when I close my laptop lid in Settings > Power Management. Is this possible? Now this is why I think, I need this:

I just installed Ubuntu 9.10 with Wubi on my HP 8510W laptop.
When I'm at home, I plug in an external monitor, a 24" Samsung SyncMaster 245B, to the laptops HDMI port, with a HDMI to DVI converter to the monitor.
Now usually in Windows XP i connect the monitor with HDMI, and close the lid on my laptop, and XP figures out, that I want to use the Samsung at it's native resolution as my single screen. The native resolution of my laptop screen and monitor is both 1920x1200.

Now as the 8510W has Nvidia graphics, I use the nvidia driver for it. So I set the Administation > 'Nvidia X Server Setting' to display on my Samsung and set my laptop screen to off, this is working and I am using my Samsung rigth now, with the laptop display turned off. The problem is, when I close the lid on my laptop. First time I did this, the laptop went to sleep mode, now I changed this behavior to 'Blank screen' in Power management. The problem is, this turns of my Samsung, and there is no option to do nothing, when I close the lid.

With the laptop lid open, I can use the PC as I would like to, but I would like to have the laptop running with the lid closed, as I will have far less dust on my laptop screen and in my keyboard. If there would be an option to, 'Do Nothing' in Power Management, when I close my laptop lid, that would be perfect. Can I do this?


Thanks.

---

### Post by aberdeenjetman on 2009-11-12
Having the same problem with a HP530 and intel945 graphics.

Ubuntu didn't recognise the lid button before but 9.10 does which is causing the issue for me.

Thanks

---

### Post by Boondoklife on 2009-11-12
I have a 1420 that I hook up to my tv and use a bluetooth keyboard/mouse with, I have mine set to blank screen and it does just that if i close the lid, but if I press a button on my bluetooth keyboard, the tv screen lights up. Seems like it is working just fine for me. 

Also just a word to the wise, laptops tend to run hot with the lid closed which will lessen the life of your laptop.

---

### Post by xantus on 2010-01-11
This option was hidden.  Here's how you can set it:

```
#$ gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
```


Reference: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236")

---

### Post by seth556 on 2010-03-08
Sweet, this option worked perfectly for me on my Acer Aspire One running UNR. Just went to display in the settings and disabled the laptop monitor and turned up the resolution on the other monitor.

---

### Post by dhondiba on 2010-08-09
Thanks! Worked for me as well.

---

### Post by jcrawford on 2010-09-17
I have this working on my macbook pro install of Ubuntu 10.04.  However I must ask is there not an automated way to have all of this work?

I would love for it to turn off my internal laptop display and set the external to be primary when the lid on the laptop is closed.  This is the default behavior for Windows/Mac but for some reason not Ubuntu/Linux.

I find it to be a pain to manually turn off the laptop display in the Nvidia settings every time I wish to use my external display.  What happens when I forget to turn it back on and head off on the road with the laptop.  The display is turned off so I will not be able to see anything or do anything.  Chances of forgetting to turn the display back on are high because I am used to other OS's doing this automatically for me.

Is there not a script or something that could be executed upon closing the lid?

---

### Post by topgun98 on 2010-09-20
> **jcrawford said:**
> I have this working on my macbook pro install of Ubuntu 10.04.  However I must ask is there not an automated way to have all of this work?

I would love for it to turn off my internal laptop display and set the external to be primary when the lid on the laptop is closed.  This is the default behavior for Windows/Mac but for some reason not Ubuntu/Linux.

I find it to be a pain to manually turn off the laptop display in the Nvidia settings every time I wish to use my external display.  What happens when I forget to turn it back on and head off on the road with the laptop.  The display is turned off so I will not be able to see anything or do anything.  Chances of forgetting to turn the display back on are high because I am used to other OS's doing this automatically for me.

Is there not a script or something that could be executed upon closing the lid?

Bump.

---

### Post by collin2010 on 2010-10-09
> **xantus said:**
> This option was hidden.  Here's how you can set it:

```
#$ gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
```


Reference: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236")
Exactly what I was looking for.
Thanks.

---

### Post by Schuby007 on 2010-11-03
Thankyou! Now I am able to use my external with my laptop lid closed.

HOWEVER... I've found that when I close my laptop "lid" the screen saver and gnome-power-manager "put the display to sleep" functions stop working on the external. It's weird, cause the screen goes dark after 5 minutes (which is  what I set in screen saver settings) and it asks for password when I  shake the mouse (which is what I want) but I don't get the actual screen  saver nor does the display turn off after 30 minutes which is what I set in gnome-power-management. NOTE: these two items DO WORK when I have my laptop lid OPEN.

It seems to me that the gnome-screensaver and power management are  getting confused between my internal and external monitors. Perhaps it  could be because display settings are handled by nvidia-settings?? If  thats the case then I consider it bad practise for Ubuntu to include the  proprietary nvidia drivers without proper support.

I'd be very interested in knowing if anyone else is having this problem. And would be thrilled if anyone had any solutions.

Thankyou
P.S. Is there any way to disable the "lid-close" switch in Ubuntu at least while I have my external connected. I would like the system to be aware that I close my laptop lid when I'm using the laptop by itself, but it seems to be a problem here when I'm using only my external monitor.

---

### Post by memckimmy on 2010-12-06
I'm having the same problem as you, Schuby007. I'm running 10.10 on a Thinkpad X61 Tablet. Just as you described, I have the lid action set to "nothing" when on AC power, and when the lid is closed and the external monitor functioning as the only monitor it refuses to sleep properly. If I leave the lid open (not changing any monitor settings) it sleeps just fine. Quite frustrating.

---

### Post by mdwy62 on 2010-12-06
> **Boondoklife said:**
> I have a 1420 that I hook up to my tv and use a bluetooth keyboard/mouse with, I have mine set to blank screen and it does just that if i close the lid, but if I press a button on my bluetooth keyboard, the tv screen lights up. Seems like it is working just fine for me. 

Also just a word to the wise, laptops tend to run hot with the lid closed which will lessen the life of your laptop.

I have the same effect - where the external monitor is darkened when I close the lid on my inspiron 1420, but as soon as I hit a key, it turns back on again. Thanks for noticing this. I have had my notebook open collecting dust for about 6 months.

---

### Post by HarryG123 on 2010-12-16
Thanks to all who have posted. I am a Linux newbie.  I have an Acer Aspire One D0255 Netbook

I entered the command [sudo gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_ac "nothing"] (w/o brackets] in a terminal window, but nothing seemed to happen. 

Am I supposed to reboot in order to see any changes in the power configuration screen?

But I was able to close the lid without the screen shutting off (provided I kept moving the mouse) or causing the screen to update in some other way, e.g., by typing.

But the remark about extending laptop life be leaving the lid open--- that was something to think about. Now I leave the lid ajar.

=Thanks

---

### Post by tkzv on 2010-12-30
> gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"  

worked for me without sudo just fine, when no power management windows were open.

My question is: how to do that in desktop environments different from GNOME? Will it work in any GTK environment? What about non-GTK?

---

### Post by Mangey on 2011-01-29
I'm having similar problems to other users on here, using Lucid.

I have an Alienware M11x R1, and it is hooked up to an ASUS VH236H (I had the problems when hooked up to another monitor as well).  When it boots up, it defaults to mirroring the screen, or not showing in the external monitor at all (there is probably a pattern here, but I have not yet detected it).  I dutifully open the lid, turn the laptop screen off, set the monitor back to its native resolution, and close the lid again.

Even when set to "do nothing," closing the laptop lid turns the screen back on and resets it to "mirror."  I have to once again reset the resolution, etc.  As with others, this means that when I unplug the laptop, if I don't fix the monitors first, the laptop screen remains off.  It is not able to automatically detect the absence of a monitor.

What I really need (if there is no easy option in Ubuntu) is some sort of script that tells it the default behavior if the monitor is plugged in (laptop screen off, monitor set to native resolution), and then the default behavior if the monitor is not (laptop screen on at its native resolution).  Is anyone aware of any such fix?  Thanks!

---

### Post by Schuby007 on 2011-01-29
I'm wondering if this problem only occurs with laptops running Nvidia graphics and thus the Nvidia X Server Settings control panel?

I'm running Ubuntu 10.04.1 64bit on an Alienware m15x with Nvidia driver version: 195.36.24.

My monitor is connected via HDMI to my laptop.

---

### Post by Mangey on 2011-01-30
I'm actually not running on the nVidia card at all while in Ubuntu, and am running off the integrated graphics.  I am also running through the VGA port while in Ubuntu, because the HDMI does not work at all (I have no HDMI output, though I do when I boot into Windows).

---

### Post by Schuby007 on 2011-01-30
> **Mangey said:**
> I'm actually not running on the nVidia card at all while in Ubuntu, and am running off the integrated graphics.  I am also running through the VGA port while in Ubuntu, because the HDMI does not work at all (I have no HDMI output, though I do when I boot into Windows).

I have an Nvidia 8800M GTX card and I also have an integrated Intel graphics card. I think on these types of laptops (discrete AND integrated configurations) the HDMI port is tied to the Nvidia card and will not work when using Intel graphics.

I have another question: is it possible that this issue with the external displays not sleeping perhaps related to compiz desktop effects?

I installed Ubuntu 10.04.1 on an older Dell laptop with an Nvidia card and was hooked up to an external and the external would sleep UNTIL I installed Compiz effects. After installing compiz the external monitor no longer went into DPMS and the screensaver wouldn't show anymore.

---

### Post by olwe on 2011-04-26
The gconftool worked for me too (U10.04/Gnome2.3). Now I can shut the lid on my Thinkpad T61 and still have the computer running and my external monitors run. Q: Now what if I put my computer in suspend, is there a way to have it come out of suspend with something besides reopening the lid and pressing the On button? I'd just like to hit something on my external keyboard or move my external mouse.

---

### Post by sermoja on 2011-08-28
Thank you all, that worked great

It's an honor to use linux and that community users help each other.

All best
Sergio

---

### Post by greg.fordyce on 2011-11-29
Is there a way to do this while using Unity in 11.10? Following these instructions I was able to get this working in 11.10 by rolling back to the gnome desktop which is fine, but there must be a unity configuration for this as well. I installed the dconf-tools package but couldn't find the required settings in dconf-config.

---

