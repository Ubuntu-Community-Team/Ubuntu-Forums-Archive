---
title: "Newbie about Compiz/Beryl"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by voltron035 on 2007-07-31
I have looked at tutorials on installing Beryl/Compiz. I went through the options and I had it working for about 15 mins. After that, it will not work. I read about how to tell if it is crashing or no and I have come to the conclusion the Beryl/Compiz is crashing on my system. I am currently running a dual-boot of Ubuntu with Vista on a Sony Vaio laptop with an Intel GMA 950 video card with up to 224 MB shared video memory.

 Is there a command to run a diagnostic or website that can test your card to see if one can run Beryl/Compiz without crashing (or at least minimal crashes)?

---

### Post by Steveway on 2007-07-31
Open a Terminal and type:
$compiz --replace
or
$beryl --replace
Depending on what you use.
Then if it crashes, copy-paste the output into the forum.

---

### Post by The Afterdark on 2007-07-31
ok, i just recently installed Beryl.  I had used the Envy script to install the ATI drivers, I'm using an ATI X800 on Feisty.  
The drivers installed fine, but then I couldn't use the default Desktop Effects that came with Ubuntu.  
I went ahead and instealled Beryl anyways.  Here are the packages I installed through Synaptic Package Manager:

beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl settings
beryl settings-bindings
emerald
libberyldecoration0
libberylsettings0
libemeraldengine0

The beryl manager seemed to work, the red gem displays in the panel in the top right corner of the screen.  I try to switch to the Beryl windows manager, and it crashes and reverts to Metacity (Gnome).

Here are how the Advanced Settings are configured:[B]
Rendering Path:[/B] Copy
**Composite Overlay Window:** Automatic
**Rendering Platform:** Force AIGLX
**Binding:** Automatic
**Rendering:** Automatic

Then I tried the command given by Steveway "beryl -replace" but that didn't seem to be a proper command:

```
ehsun@ehsun-desktop:~$ beryl-replace
bash: beryl-replace: command not found
ehsun@ehsun-desktop:~$
```

I then tried simply "beryl" and I got the following:

```
ehsun@ehsun-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

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
ehsun@ehsun-desktop:~$ 
```


Help please?  I'm missing a file?  Or just some hardware configuration?

---

### Post by eggdeng on 2007-07-31
Type in a terminal
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
```
or
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace
``` if beryl is already running.
Thats two hyphens '--'! More options at [http://ubuntuforums.org/showthread.php?t=352350&page=2](http://ubuntuforums.org/showthread.php?t=352350&page=2)

---

### Post by jms1277 on 2007-08-01
i tried that and all iget is a plane white screen and have to restart x

---

### Post by jms1277 on 2007-08-01
oh thanks in advance

---

