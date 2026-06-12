---
title: "HOW TO: Setting up xfce xft font rendering settings"
date: 2007-10-24
forum: Desktop Environments
---

### Post by TuxCrafter on 2007-10-24
#Version:       0.0.2
#Date:          24-10-07
#Description:    Setting up xfce xft font rendering settings
#Solution:      This script will fix bad rendering of fonts on xfce

This script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

When you monitor resolution and dpi settings are correct, and you use xfce and some xfce applications have bad font rendering then you can use this script to correct some settings like anti aliasing and hinting.

example of correct motinor and dpi settings:

```
 xdpyinfo | grep resolution
```resolution:    100x100 dots per inch
```
 xdpyinfo | grep dimension
```dimensions:    1024x768 pixels (260x195 millimeters)

If your settings are not correct you can try my other script first:
[http://ubuntuforums.org/showthread.php?t=589574](http://ubuntuforums.org/showthread.php?t=589574)

I hope this script will help a lot of people! :KS

---

### Post by K.Mandla on 2007-10-26
Moved to Desktop Environments.

---

### Post by K.Mandla on 2007-10-26
Thread title changed at the request of the OPer. :)

---

### Post by TuxCrafter on 2007-10-26
> **K.Mandla said:**
> Thread title changed at the request of the OPer. :)

Thanks Mandla, I just read your speed tweak documentation to see if i could learn something new. I only did not know about the pango tweak in firefox :-p

---

### Post by Dwood108 on 2007-10-30
This just seemed to trash my system.
I fresh installed xubuntu 7.10 ran this script and was stuck with a 640x400 resolution and no option to increase it.
When restarting it couldn't identify my monitor and gave me an option to manually configure X, again with only a 640x400 max resolution. The keyboard settings were also reset from UK to US.
What is this script supposed to do?
How can I uninstall it/ restore my previous settings?

---

### Post by TuxCrafter on 2007-10-30
> **Dwood108 said:**
> This just seemed to trash my system.
I fresh installed xubuntu 7.10 ran this script and was stuck with a 640x400 resolution and no option to increase it.
When restarting it couldn't identify my monitor and gave me an option to manually configure X, again with only a 640x400 max resolution. The keyboard settings were also reset from UK to US.
What is this script supposed to do?
How can I uninstall it/ restore my previous settings?

Just to be clear on this, but this could never be the fault of my script. I don't know what you did to your computer but it had nothing to do with the script! If it somehow did change something else I will try to find it and fix it, but the change the script did something wrong is very small.

The script only changes some font settings that are used by the xfce-mcs-manager.

To undo the changes just restore the backup the script created.

```
cp $HOME/.config/xfce4/mcs_settings/gtk.xml.backup $HOME/.config/xfce4/mcs_settings/gtk.xml
```Maybe if you provide more information what you did on you system I will gladly be able to help you fix it.

---

### Post by Dwood108 on 2007-10-31
Thanks for replying.

Just to double check - to run the script you use the following command:
chmod +x xfce4-xft.sh; ./xfce4-xft.sh

In the file there it mentions a bash command as well:
bash /media/sda3/scripts/clean-installations/xfce4-xft.sh

I don't know what bash commands are, do I need to run this one .

I am not quite sure what went wrong exactly - do you have to run the script from the home directory or could it be run from anywhere.
I ended up re-installing.

The problem I have (the original one - not caused by the script) is that if I have a screen resolution of 88x640 and font size of smaller than 9 the fonts become unreadable, not too small, but very poorly defined, as does the firefox display. This seems to destry the fonts so that even when I increase the font size again they still don't look right.
Will thescript fix this?  I will have another go with it.
Thanks for your time.

The main problem is that I have a small monitor and would like to use 800x640 as a screen resolution. When I do this and lower the font size in user interface settings so that it doesn't seem too 'clunky' this, for some reason effects how Firefox displays webpages, the text is very small, poorly defined and unreadable. The system fonts when set to 8 don't render very well either.

---

### Post by TuxCrafter on 2007-10-31
> **Dwood108 said:**
> 
The problem I have (the original one - not caused by the script) is that if I have a screen resolution of 88x640 and font size of smaller than 9 the fonts become unreadable, not too small, but very poorly defined, as does the firefox display. This seems to destry the fonts so that even when I increase the font size again they still don't look right.
Will thescript fix this?  I will have another go with it.
Thanks for your time.

The main problem is that I have a small monitor and would like to use 800x640 as a screen resolution. When I do this and lower the font size in user interface settings so that it doesn't seem too 'clunky' this, for some reason effects how Firefox displays webpages, the text is very small, poorly defined and unreadable. The system fonts when set to 8 don't render very well either.

Ok, the first thing you have to do is to make sure the xserver is running correctly, with the correct video driver and monitor settings.

This is controlled by the xorg.conf file. When you monitor resolution and dpi settings are correct, and you use xfce then you can use this script to correct some settings like anti aliasing and hinting.

Your current problem is unrelated to this script or xfce. It has to do with the xserver and the xorg file, and is far to of topic. I think when you google on xorg configuration you can find a lot of useful information.

---

### Post by Dwood108 on 2007-10-31
I have sorted things out now.

Not exactly sure what the problem was as I have fiddled with so many settings and things I have lost track of them all.

However now I have run your script and it has done what it should do, make the font sizes in the system toolbars etc and application windows all the same size. Previiously the application fonts were a lot smaller than the system ones making it difficult to find a setting that was comfortable to look at.

Thanks for your help.
I will cast another vote for the script!
Cheers

---

### Post by TuxCrafter on 2007-10-31
> **Dwood108 said:**
> I have sorted things out now.

Not exactly sure what the problem was as I have fiddled with so many settings and things I have lost track of them all.

However now I have run your script and it has done what it should do, make the font sizes in the system toolbars etc and application windows all the same size. Previiously the application fonts were a lot smaller than the system ones making it difficult to find a setting that was comfortable to look at.

Thanks for your help.
I will cast another vote for the script!
Cheers

Perfect, nice it helped and thanks for giving the feedback.

---

### Post by snap on 2007-11-04
Hi TuxCrafter
This script worked perfect for me, but maybe you should put a plug to the other nice script of you'rs here the "[Setting up xorg LCD 96 DPI native monitor settings]("http://ubuntuforums.org/showthread.php?t=589574")"?

these two go hand in hand in my opinion.
Thanks for these.

---

### Post by TuxCrafter on 2007-11-04
> **snap said:**
> Hi TuxCrafter
This script worked perfect for me, but maybe you should put a plug to the other nice script of you'rs here the "[Setting up xorg LCD 96 DPI native monitor settings]("http://ubuntuforums.org/showthread.php?t=589574")"?

these two go hand in hand in my opinion.
Thanks for these.

Yes thats true, i think I will make a note in both scripts, btw i think i will change 96 dpi to 100, i got better results with this.

---

### Post by adlin5000 on 2007-11-04
Wow, that really made a difference in how the fonts look. Unfortunately they are still very small. No mater how I change my xorg.conf "xdpyinfo |grep resolution" still gives me 46x49. Can you give me any help on this?

[EDIT] BTW I've tried adding Xft.dpi: 96 to Xft.xrdb, it dosen't work.

---

### Post by TuxCrafter on 2007-11-04
> **adlin5000 said:**
> Wow, that really made a difference in how the fonts look. Unfortunately they are still very small. No mater how I change my xorg.conf "xdpyinfo |grep resolution" still gives me 46x49. Can you give me any help on this?

[EDIT] BTW I've tried adding Xft.dpi: 96 to Xft.xrdb, it dosen't work.
jup i tried that to but it will not work developers say that it may be possible in xfce 4.6

Have you tried my xorg script to set the dpi?

---

### Post by hotweiss on 2007-11-04
Didn't work, when I type xdpyinfo | grep resolution I get this:

  resolution:    64x64 dots per inch

When I type  xdpyinfo | grep dimension I get this:

  dimensions:    1024x768 pixels (408x306 millimeters)

Any ideas?

---

### Post by TuxCrafter on 2007-11-04
> **hotweiss said:**
> Didn't work, when I type xdpyinfo | grep resolution I get this:

  resolution:    64x64 dots per inch

When I type  xdpyinfo | grep dimension I get this:

  dimensions:    1024x768 pixels (408x306 millimeters)

Any ideas?

This script does not change your dpi or resolution but alters font rendering like anti alias, hinting etcetera. So the script probably did work...

You can try my xorg script for getting the dpi settings right before using this script. Read the OP post for more information.

---

### Post by hotweiss on 2007-11-04
> **TuxCrafter said:**
> This script does not change your dpi or resolution but alters font rendering like anti alias, hinting etcetera. So the script probably did work...

You can try my xorg script for getting the dpi settings right before using this script. Read the OP post for more information.

I tried that other script, but it didn't work.

---

### Post by TuxCrafter on 2007-11-04
> **hotweiss said:**
> I tried that other script, but it didn't work.

than i cant help anymore, maybe try a new modeline or buy a new monitor and video card. both scripts worked fine by a lot of people

---

### Post by adlin5000 on 2007-11-04
I've tried many different xorg settings and have gotten a whole range of dpi settings (I checked the xorg log file), problem is that xfce seems to override the xorg settings with its own. Your xfce script deffinitly made the fonts look a lot better and eiser to read, but I still get 46x48 dpi. At lest with the better looking fonts I can get a readable font size and not have web pages go too nuts.

---

### Post by hotweiss on 2007-11-04
> **adlin5000 said:**
> I've tried many different xorg settings and have gotten a whole range of dpi settings (I checked the xorg log file), problem is that xfce seems to override the xorg settings with its own. Your xfce script deffinitly made the fonts look a lot better and eiser to read, but I still get 46x48 dpi. At lest with the better looking fonts I can get a readable font size and not have web pages go too nuts.

I had the same problem... Download the other display script that the OP linked in the first post... Reboot... If it fails to change your DPI to a normal level keep on changing your resolution (not script, but in XFCE settings) until it comes back to normal. That's how it worked for me.

PS-Xubuntu is much nicer than Ubuntu for what I use it for...

---

### Post by adlin5000 on 2007-11-05
I DID IT!
Finally got it to work. It seems that XFCE used the EDID info from the monitor to determine the display size and then calculates the DPI from that. I had to edit the xorg.conf file to ignore EDID and DDC and put in all the monitor settings (H/V rates, display sixe, and resolutions). After that XFCE had to go from those settings because there was nothing else for it to use. Now I have 96x96 DPI, readable text and web sites look like they should.

I'll post this with the other script as this deals with both XFCE and Xorg.

Thanks for all your help.

---

### Post by keratos on 2008-03-15
BRILLIANT.

excellent rendering quality.

:-)

---

### Post by TuxCrafter on 2008-03-15
thanks, i will look for some better solutions in hardy

---

