---
title: "Adjusting mousepad sensitivity settings using xconf.org"
date: 2009-06-09
forum: General Help
---

### Post by theturbanator on 2009-06-09
Hi everyone!

I have a Dell Vostro 1400 running Ubuntu 9.04, and my mousepad is currently way too sensitive. I installed gsynaptics and have read that (for Ubuntu 7.04, at least -- I'm assuming it is the essentially the same for 9.04) my xorg.conf file should have the following section: 
Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Option          "SHMConfig"             "on"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection

However, my xorg.conf file does not have such a section.  Is it OK to add
it in? If it is, how can I customize / correct it for Ubuntu 9.04?  For example, I believe that instead of "on", SHMConfig has to be set to "true".

Any help would be much appreciated!

---

### Post by murray92 on 2009-06-09
It might be easier for you to go to System>Preferences>Mouse and adjust the sensitivity from there, or have you already tried that?

---

### Post by theturbanator on 2009-06-09
you're right... I didn't realize that touchpad sensitivity would be in the Mouse Preferences window... thanks for that (by changing it to the lowest sensitivity, it definitely seemed to help)

out of curiosity though (and because I now have a System>Preferences>Touchpad menu option), how can i modify the xorg.conf file to correctly have the touchpad menu option implemented / available?

---

### Post by murray92 on 2009-06-09
I'm not sure what you mean sorry. I don't have a Touchpad option in Preferences, but i do have a Touchpad tab in the Mouse menu, is that what you mean?

Did you add that last piece of script to your xorg.conf?

---

### Post by theturbanator on 2009-06-09
Well... I HAD added it to my xorg.conf file, and, thus, the Touchpad menu option became available, but I couldn't access it because it said "you have to set 'SHMConfig' 'true' in xorg.conf"... so i did that and deleted some of those options... and then I had a major problem with the X and had to delete my xorg.conf file... but the Touchpad menu option is still there in System>Preferences...

but yeah, so now I want to know the correct way of doing it

and this edit that I had to do might show that the touchpad is still sensitive haha

---

### Post by murray92 on 2009-06-09
I don't have anything similar to that in my xorg.conf and my touchpad seems fine. It might be worth trying to just take it out and edit the mouse preferences. If that doesn't help then I'm not sure what to do sorry.

Edit: You have probably already tried this but above the Sensitivity option is the Acceleration option, which affects the speed more, reducing that will definitely help if you haven't already

---

### Post by theturbanator on 2009-06-09
I appreciate your help greatly!  I don't think I was entirely clear on what adding that to my xorg.conf file is supposed to do:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings)

adding it is supposed to create this System>Preferences>Touchpad menu option which, presumable, has more options / detail in dealing with touchpad sensitivity than the "Mouse" menu option does...

---

### Post by murray92 on 2009-06-09
Just googled GSynaptics and its apparantly obselete. That guide probably is too seeing as it refers to 7.04 and a lot of changes have been made since then.

The GSynaptics site says to use GPointing Device. The link to that is below.

[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

---

### Post by theturbanator on 2009-06-09
OK, so i removed the GSynaptics package and downloaded the GPointing Device tarball... any idea of how to install it? There isn't a README file (or at least under that name), and I'm sort of a Ubuntu beginner...

Thanks for all of your help!

---

### Post by murray92 on 2009-06-09
This is quite confusing. Generally what one does with a tar.gz is extract it

cd the-folder-you-extracted
./configure
make
sudo make install

But this isn't working for this. I'm not sure i can help further really sorry. The only solution really is to reduce acceleration and sensitivity as low as possible for now. Maybe try contacting Dell about it, chances are you're not the only person with the problem and they'll have a solution
Sorry I couldn't help more

---

### Post by michy99 on 2009-06-09
There is a package called tpconfig in the repositories that might do what you want.

---

### Post by theturbanator on 2009-06-12
thank you murray, you did help quite a bit!  i was able to run the commands you gave me, after installing a few packages (such as libgtk2.0-dev)... so now is GPointingDevice correctly installed? how can I check? and now how do I access the touchpad settings GUI (back with GSynaptic it was in System > Preferences > Touchpad)?

I appreciate all of your help! Thanks!

---

