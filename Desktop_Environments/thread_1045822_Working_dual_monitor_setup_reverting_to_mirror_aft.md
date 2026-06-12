---
title: "Working dual monitor setup reverting to mirror after reboot."
date: 2009-01-20
forum: Desktop Environments
---

### Post by Salmontarre on 2009-01-20
Hello.

I installed Ubuntu 8.10 lately, and have run into a problem with using my two monitors.

I have an ATI X1650, and two identical monitors.

I have installed the latest ATI driver (8.12) and I can use the Catalyst tool to enable the second monitor to function as a doublewide desktop.  It works fine, until I reset.  When I do reset, everything seems fine, until I get past the login screen (at the login screen, I have login on the left monitor, and empty space I can move the cursor to on the right monitor, as it should be).  Once I hit enter on my password, though, the screens switch back to mirror mode.

I have looked at xorg.conf before and after reset, and they remain the same, whether dualhead is working or not.

Is there some other file that is not being saved to correctly?

Here is what my xorg.conf looks like: [http://paste.ubuntu.com/107558/](http://paste.ubuntu.com/107558/)

Thanks for any help!

---

### Post by Salmontarre on 2009-01-27
bump

---

### Post by nvdm on 2009-03-04
I'm also experiencing this problem, exactly as described above.

---

### Post by issih on 2009-03-04
Not at all sure this will help, but I wonder if there is a need to run the catalyst config app as root, that was certainly the case with the nvidia application last time I used it.

Worth investigating perhaps.

---

### Post by nvdm on 2009-03-05
Running the Catalyst control panel as root doesn't correct this behaviour.

---

### Post by seesser on 2009-03-13
I two am having this problem I have to reset to duel every time I log in must be missing something.:(

---

### Post by noogs on 2009-03-22
I have this same exact problem and have googled with no success. Someone must know how to fix it. HELP!

---

### Post by noogs on 2009-03-22
Very simple fix for this actually. Go to "System>Preferences>Screen Resolution" while in the working dual monitor setup and simply click apply. This saves your current display settings and your good to go.

---

### Post by daboroe on 2009-03-22
same issue. i reboot and it goes back to mirror. not a huge thing but would like it to keep the settings. it says reboot to save settings. i do and it doesnt.

---

### Post by daboroe on 2009-03-26
> **noogs said:**
> Very simple fix for this actually. Go to "System>Preferences>Screen Resolution" while in the working dual monitor setup and simply click apply. This saves your current display settings and your good to go.

I have done that and it still will not do that. 

**UPDATE**: Screen Resolution has been removed or moved in Jaunty Alpha 6, just FYI

---

### Post by kOna on 2009-03-27
I created a separate thread about this exact issue but I haven't received any replies on the matter.

Seems that quite a few of us have this problem now, it's a show stopper for me as I simply can't do without both monitors :( I'll keep an eye on this thread to see if this issue gets resolved but for now it's back to Vista I go!

---

### Post by robobart on 2009-08-21
Similar problem- except instead of reverting to mirror - one monitor just shuts off.

I would like help.

Thanks!

---

### Post by robobart on 2009-08-24
One thing I tried was to do:

$ sudo gnome-display-properties

and then click "Apply"

However, the settings could not be set because:

Method "ApplyConfiguration" with signature "" on interface "org.gnome.SettingsDaemon.XRANDR" doesn't exist

Thoughts?

Thanks!

---

### Post by robobart on 2009-08-27
Got it working!

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

helped quite a bit:

Dual Displays in Ubuntu 9.04, Dell E4300 Laptop - docked
(Intel driver)


1) Modify the Screen section of /etc/X11/xorg.conf to include the
lines:

SubSection "Display"
Virtual 2560 1024
EndSubSection

My complete Screen section looks like:

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Virtual 2560 1024
EndSubSection
EndSection

2) Added the following file: /etc/X11/Xsession.d/85custom_xrandr-settings

-- begin file --
# If an external monitor is connected, place it with xrandr
# Use xrandr -q to determine choices for outputs
DEFAULT_OUTPUT="LVDS"
MAIN_OUTPUT="HDMI-1"
AUX_OUTPUT="VGA"
# AUX_LOCATION may be one of: left, right, above, or below
AUX_LOCATION="right"

case "$AUX_LOCATION" in
left|LEFT)
AUX_LOCATION="--left-of $MAIN_OUTPUT"
;;
right|RIGHT)
AUX_LOCATION="--right-of $MAIN_OUTPUT"
;;
top|TOP|above|ABOVE)
AUX_LOCATION="--above $MAIN_OUTPUT"
;;
bottom|BOTTOM|below|BELOW)
AUX_LOCATION="--below $MAIN_OUTPUT"
;;
*)
AUX_LOCATION="--left-of $MAIN_OUTPUT"
;;
esac

xrandr |grep $MAIN_OUTPUT | grep " connected "
if [ $? -eq 0 ]; then
xrandr --output $DEFAULT_OUTPUT --off --output $MAIN_OUTPUT --auto --output $AUX_OUTPUT --auto $AUX_LOCATION
else
xrandr --output $DEFAULT_OUTPUT --auto --output $MAIN_OUTPUT --off --output $AUX_OUTPUT --off
fi
-- end file --

3) Now for the voodoo, under

System => Startup Applications

I added the command:

xrandr --output VGA --auto --right-of HDMI-1


reboot and it works!

---

### Post by mzzpxt on 2009-10-19
Has anyone looked into this for KDE? I too cannot turn off display mirror in KDE, but have no problem turning off mirror in Gnome. I do not have the nVidia utilities as a workaround because my video is Intel 855GME. Any ideas?

---

### Post by bpickel on 2009-10-19
Same here with the nvidia driver.   I only want to use my external monitor when docked but everytime I boot I have to open nvidia control panel and disable the laptop lcd.   when I boot and it loads GDM it defaults to the laptop screen and I have to make the change after login, even with the laptops lid closed during boot. Just takes a few seconds to make the changes but it's wearing on me. So I am now in the club. Let's see how much breakage it takes to get to the center of this tootsie pop ! :mad:

---

### Post by YarDYar on 2009-11-08
I also have the same problem as mzzpxt has.

---

### Post by NicNicNicNicNic on 2013-03-20
> **daboroe said:**
> I have done that and it still will not do that.

Make sure you check both screens.  After you change your display  settings, and click apply, there is a pop up window that appears to ask  if you would like to keep the new settings, or revert to the old ones.   You have to click again to keep the new settings.  Ubuntu  checks to make sure you want to keep your new settings after you apply them.

---

### Post by overdrank on 2013-03-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

