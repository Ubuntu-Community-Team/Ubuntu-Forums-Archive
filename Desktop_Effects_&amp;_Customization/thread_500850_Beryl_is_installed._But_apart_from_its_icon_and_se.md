---
title: "Beryl is installed. But apart from its icon and settings theres nothing different!"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by monkey56657 on 2007-07-14
Hey. I just installed Ubuntu and everything was going fine. 

I went to get beryl from the site after seeing it in a youtube video. 

I followed the instructions [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI") as i have ubuntu and an ATI card (to which i have installed the driver with "Restricted Drivers Manager".

It seems to be installed OK. i got it to start as i login and have restarted the machine as well. From the beryl menu i sleected "Select Window Manager" then "Beryl" and "Select Window Decorator" and then "Standard Beryl Decorator". 

In the settings all the effects like "Wobbly windows" are enabled and i have tried to choose a theme. 

The problem is...nothing is happening! Not a single thing looks different to how it was before. 

Any help would be much appreciated in solving this problem. THe beryl forum was closed to new registration so i came here. 

Thanks in advance :KS

---

### Post by skaspud on 2007-07-14
Same exact thing w/ me!!! som1 help us über n00bs!

i followed these directions even
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI)
still...
i got everything right, drivers everything, i see the lil icon up top just sitting there, mocking me.
i tried right-clicking on it- window manager- beryl, and i click on it and it reloads the windows, but nothing different.

---

### Post by dreadlord_chris on 2007-07-14
to both of you...

open a terminal and enter:
```

beryl --replace

```
then post the output back here...

---

### Post by skaspud on 2007-07-14
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

posted here: [http://ubuntuforums.org/showthread.php?t=500970](http://ubuntuforums.org/showthread.php?t=500970)

---

### Post by tomaasj on 2007-07-14
> **dreadlord_chris said:**
> to both of you...

open a terminal and enter:
```

beryl --replace

```
then post the output back here...


Hi dr. lord

need also help with similar issue.  Desktop effects are also not working (see output terminal and text posted earlier:

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0




Need some help,

Beryl stopped working.  The icon is still there in the bar.  I am not able to select Window manager from Metacity (default) to Beryl.  After a re-install of Beryl (using the terminal or Synaptic, tried both) I was able set the window manager to Beryl but then the screen flickers and nothing happens.

These problems occured after I solved the screen resolution issue which seems to be a topic with my Dell laptop.  Highest was 1024 768, but after installing a patch (see below) I am now able to run the laptop with a 1280 800 resolution.  Before finding the patch I was tinkering with a file named xorg.conf in /etc/X11 (followed advice from a thread here in the forums).  I made a backup of the xorg.conf file in the directory etc/X11.  Following tinkering with xorg.conf file, the resolution was not solved, so I replaced the altered xorg.conf file with the backup I made.

Maybe the two issues are not related but think it prudent to mention what I was doing before I noticed that Beryl was not behaving as it should.

Is there somebody here to help me to get Beryl running again on my laptop ?

Thanks in advance,

Tomaasj


My laptop:

Inspiron 6400 Dual Core Processor T2080 (1.73GHz,1MB L2 cache, 533MHz)
15.4" Wide Screen WXGA (1280 x 800) TFT Display
Intel Media Accelerator 950 Graphics Up to 256MB shared graphics memory


used this link to get my screen resolution fixed to 1280 800:
[http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html](http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html)

---

### Post by dreadlord_chris on 2007-07-14
> **skaspud said:**
> **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

posted here: [http://ubuntuforums.org/showthread.php?t=500970](http://ubuntuforums.org/showthread.php?t=500970)

I do believe that the ATI cards don't work with AIGLX, they require XGL. What's the output of the following in a terminal:
```

fglrxinfo

```

or you could look [here]("https://help.ubuntu.com/community/Beryl/ATI/Feisty")

---

### Post by dreadlord_chris on 2007-07-15
> **tomaasj said:**
> Hi dr. lord

need also help with similar issue.  Desktop effects are also not working (see output terminal and text posted earlier:

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0




Need some help,

Beryl stopped working.  The icon is still there in the bar.  I am not able to select Window manager from Metacity (default) to Beryl.  After a re-install of Beryl (using the terminal or Synaptic, tried both) I was able set the window manager to Beryl but then the screen flickers and nothing happens.

These problems occured after I solved the screen resolution issue which seems to be a topic with my Dell laptop.  Highest was 1024 768, but after installing a patch (see below) I am now able to run the laptop with a 1280 800 resolution.  Before finding the patch I was tinkering with a file named xorg.conf in /etc/X11 (followed advice from a thread here in the forums).  I made a backup of the xorg.conf file in the directory etc/X11.  Following tinkering with xorg.conf file, the resolution was not solved, so I replaced the altered xorg.conf file with the backup I made.

Maybe the two issues are not related but think it prudent to mention what I was doing before I noticed that Beryl was not behaving as it should.

Is there somebody here to help me to get Beryl running again on my laptop ?

Thanks in advance,

Tomaasj


My laptop:

Inspiron 6400 Dual Core Processor T2080 (1.73GHz,1MB L2 cache, 533MHz)
15.4" Wide Screen WXGA (1280 x 800) TFT Display
Intel Media Accelerator 950 Graphics Up to 256MB shared graphics memory


used this link to get my screen resolution fixed to 1280 800:
[http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html](http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html)

Honestly, I'm not really sure what's up with the Intel IGP drivers - although I have heard that beryl works well with them....

Really, and this is going to be my recommendation from now on - stop using beryl, it's merged back with it's predecessor compiz. Compiz Fusion is already the best of both eye-candy worlds. It was far easier to get up an running then beryl was - actually worked right off the bat, which beryl never did w/out tweaking. And while the former compiz installed and ran just as easily - the new merger is **far** more functional.

---

### Post by nsleiman on 2007-07-16
> **tomaasj said:**
> Hi dr. lord

need also help with similar issue.  Desktop effects are also not working (see output terminal and text posted earlier:

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0




Need some help,

Beryl stopped working.  The icon is still there in the bar.  I am not able to select Window manager from Metacity (default) to Beryl.  After a re-install of Beryl (using the terminal or Synaptic, tried both) I was able set the window manager to Beryl but then the screen flickers and nothing happens.

These problems occured after I solved the screen resolution issue which seems to be a topic with my Dell laptop.  Highest was 1024 768, but after installing a patch (see below) I am now able to run the laptop with a 1280 800 resolution.  Before finding the patch I was tinkering with a file named xorg.conf in /etc/X11 (followed advice from a thread here in the forums).  I made a backup of the xorg.conf file in the directory etc/X11.  Following tinkering with xorg.conf file, the resolution was not solved, so I replaced the altered xorg.conf file with the backup I made.

Maybe the two issues are not related but think it prudent to mention what I was doing before I noticed that Beryl was not behaving as it should.

Is there somebody here to help me to get Beryl running again on my laptop ?

Thanks in advance,

Tomaasj


My laptop:

Inspiron 6400 Dual Core Processor T2080 (1.73GHz,1MB L2 cache, 533MHz)
15.4" Wide Screen WXGA (1280 x 800) TFT Display
Intel Media Accelerator 950 Graphics Up to 256MB shared graphics memory


used this link to get my screen resolution fixed to 1280 800:
[http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html](http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html)
i have same problem, if u get it working please advise, 
thanks

---

### Post by tomaasj on 2007-07-17
sure,but I'm afraid it will take awhile.  System backup failed.  Keep you informed...

gr. Tomaasj

---

### Post by holdinout on 2007-07-18
Anybody get anywhere with this? Got the same problem, only on a nvidia. Beryl suddenly stopped working...

---

### Post by pinesol33 on 2007-07-18
I have the same problem as holdinout. I am running Kubuntu and I have an nvidia 6600GT with the newest driver installed, Beryl is installed (there is a desktop and taskbar icon), but nothing has changed. I have tried fiddling with the settings in the beryl manager, but nothing I do changes anything. Also, I get this:

~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension


Thanks for any help you can give.

---

### Post by dreadlord_chris on 2007-07-19
> **pinesol33 said:**
> I have the same problem as holdinout. I am running Kubuntu and I have an nvidia 6600GT with the newest driver installed, Beryl is installed (there is a desktop and taskbar icon), but nothing has changed. I have tried fiddling with the settings in the beryl manager, but nothing I do changes anything. Also, I get this:

~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension


Thanks for any help you can give.

could you post the contents of your **/etc/X11/xorg.conf**

you should have a section (near the end) like this:
```

Section "Extensions"
  option "Composite" "Enable"
EndSection

```
I have a feeling yours is missing....

---

### Post by tomaasj on 2007-07-19
> **dreadlord_chris said:**
> could you post the contents of your **/etc/X11/xorg.conf**

you should have a section (near the end) like this:
```

Section "Extensions"
  option "Composite" "Enable"
EndSection

```
I have a feeling yours is missing....

I've had that section though.  Meanwhile I re-installed Ubuntu because of problems with Beryl and tinkering with the xorg.conf file.  Did not install Beryl yet, but will soon...(although I'm somewhat reluctant).

gr. Tomaasj

---

