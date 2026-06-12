---
title: "Resolution change at startup"
date: 2010-02-21
forum: Desktop Environments
---

### Post by dave_didlydodo on 2010-02-21
I'm running Karmic with an NVIDIA GeForce 6600, normally at 1280x1024. Just during the past week, the resolution has started spontaneously changing to 1024x768, just after I type the password to login. I get the  Ubuntu splash screen with the animated light thingy underneath, then the screen flickers and it goes to 1024x768. I have tried changing driver but this has no effect.

I then have to change it manually using the Nvidia X Server settings utility, which is fine. I can then save X settings into /etc/x11/xorg.conf but next startup it does exactly the same again. I have seen a lot of posts in which Ubuntu leaves users stuck in a low res, or even tries to put them into an unsupported res, but nothing quite like this.  Is there a Gnome setting somewhere that defines screen res at startup??

Help! :confused:

---

### Post by dave_didlydodo on 2010-02-21
Just found out that this is account-related. I just logged out and logged back in as a different user and the problem didn't happen.  Any ideas anyone?

---

### Post by 23dornot23d on 2010-02-21
When you try to change your display settings and write the new xorg.conf file what does it look like can you post it ...... here .... use this in a terminal to see it .....

gedit /etc/X11/xorg.conf

save it to your Desktop as a copy to have a look at ......

if its account related though ... the xorg.conf will not change for each user ....

---

### Post by dave_didlydodo on 2010-02-21
ok, I have attached it but I don't think there is anything wrong with it, especially due the account-specific nature of the problem.

I now have a quick  fix using xrandr. I have put launcher on the desktop that runs:

xrandr -s 1280x1024 and that puts it back fine. But i really want a 'proper' fix!

Cheers

---

### Post by kemsiro on 2010-02-21
what about remove other resolutions option and leave only
Option         "metamodes" "1280x1024 +0+0"

---

### Post by dave_didlydodo on 2010-02-21
ok, I'll give it a whirl

---

### Post by dave_didlydodo on 2010-02-21
...and no effect whatsoever.  In fact the list of screen resolutions in xorg.conf (now down to one) has no effect on the large list of possible resolutions the the Nvidia X Server utility thinks are available. And a not-very-scientific random selection of those do all seem to work.

---

### Post by 23dornot23d on 2010-02-21
The only thing that seems a bit odd ,,,, is the twinview settings .... as from what I can make out you are not running two monitors ..... 

The xorg.conf  - would work the same for both users .... though .....



Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024 +0+0; 1280x1024_60 +0+0; 832x624 +0+0; 800x600 +0+0; 720x450 +0+0; 640x480 +0+0; 640x400 +0+0; 1024x768 +0+0"
    # Option         "metamodes" "1280x1024 +0+0;  832x624 +0+0; 800x600 +0+0; 720x450 +0+0; 640x480 +0+0; 640x400 +0+0; 1280x1024_60 +0+0;
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


I will leave this for someone that understands how each of the users screen settings are stored separately, although I will continue searching for more information for you ...... on this matter ........

Old link ..... but its all I can find at present ..... [https://blueprints.launchpad.net/ubuntu/+spec/xorg-options-editor](https://blueprints.launchpad.net/ubuntu/+spec/xorg-options-editor)

[https://wiki.ubuntu.com/X/OptionsEditor](https://wiki.ubuntu.com/X/OptionsEditor)

From what I keep reading HAL now has taken over most of the tasks in xorg.conf ........ but my understanding was that if you had a xorg.conf then this took priority
but I may be wrong .....  

Where are the new settings stored and are they manually editable ..... ?

---

### Post by dave_didlydodo on 2010-02-21
ok, thanks for your efforts. I'll take a look at that twinview setting.

---

### Post by rnsc on 2010-12-25
I am having the same problem in lucid (10.04).  Did you ever learn how the an individual user's desktop is controlled, or why different users should have different resolutions?  In my case, the resolution is fine, it is the refresh rate that is odd...

Thanks.

---

