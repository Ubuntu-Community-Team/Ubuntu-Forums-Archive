---
title: "Gutsy and built in Compiz Fusion won't enable!"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by gerfuls on 2007-10-18
i have Ubuntu 7.10 with 2.0 GHz AMD Processor and and ATI Radeon Xpress 200M video card. I am using the fgrlx driver, but for some reason when I try to enable visual effects under the Appearance window i get a popup box with the following message: "The Composite extension is not available."

How can i fix this?

---

### Post by sc30317 on 2007-10-18
System -> Administration -> Restricted Drivers Manager

Enable your card

Try to install XGL as well if that doesn't work

---

### Post by e78174 on 2007-10-18
Originally Posted by rh1zome  View Post
For the record, the fixes listed by others here worked for me with Gutsy Gibbon Beta running on an ATI X1800 GTO, Asus A8R32MVP, AMD X2 4400.

This is what I did:

From command line make xorg.conf backup:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Open xorg.conf in text editor:
sudo nano -w /etc/X11/xorg.conf

Change:
Option "Composite" "0"
to:
Option "Composite" "1"

Save changes and exit editor.

From command line:
sudo apt-get install xserver-xgl

Restart X-server (Ctrl+Alt+Backspace -- I assume this works although I actually rebooted)

Go to System > Preferences > Appearance > Visual Effects and enable some of the most shameless eye candy yet seen

---

### Post by gerfuls on 2007-10-18
i tried everything you suggested and i still get the error: Desktop Effects we not enabled. If i run "compiz --replace" i get the following output:
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

what does this mean?

---

### Post by diotro on 2007-10-19
I'm having the same problem, any advice would be appreciated. I'm running an X800 PCI Express Radeon.

---

### Post by Will PJ on 2007-10-19
i am also using a amd64 3200+ with ati 200m integrated graphics, and i am using gutsy. i have downloaded the compiz "Advanced Desktop Effects Settings (ccsm)", (which gives you the chance to customize the visual effects) and it still came up with the message.

"The Composite extension is not available"

any ideas?:confused::confused::confused:

---

### Post by drinkpepsi on 2007-10-19
> ```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```


I'm getting the same thing. It worked fine in the rc.

---

### Post by Megaqwerty on 2007-10-19
The answer lies here:

[http://ubuntuforums.org/showpost.php?p=3562227&postcount=10](http://ubuntuforums.org/showpost.php?p=3562227&postcount=10)

Hope that helps,

Megaqwerty

---

### Post by gerfuls on 2007-10-20
> **Megaqwerty said:**
> The answer lies here:

[http://ubuntuforums.org/showpost.php?p=3562227&postcount=10](http://ubuntuforums.org/showpost.php?p=3562227&postcount=10)

Hope that helps,

Megaqwerty
 this hasn't worked for me! i just learned that i actually have a ATI Radeon Xpress **200G**. not 200M! that could make a difference! please help!

---

### Post by Ub1476 on 2007-10-20
"The Composite extension is not available" means that you are using closed source fglrx ati drivers, but XGL is not present. Open the Synaptic package manager, search for XGL and install it. 

Also, in xorg.conf THIS is correct:

```
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by bripab007 on 2007-10-22
Just to add my $0.02:

ATI Radeon 9800 XT

I enabled and let Gutsy install the Restricted ATI drivers (appears to be using version 8.38.something), installed X-server (apt-get x-server blah blah blah) and changed Composite from "0" to "1" in xorg.conf, rebooted the machine, and everything's working like a champ.

The stock, generic ATI Rage, etc. drivers that Gutsy detected and was using allowed some of the desktop effects to work, but they were slow/not hardware-accelerated and the screensavers didn't work full-screen.

Now, however, the screensavers work great in full-screen preview, but they don't actually work when the computer is idle and they're supposed to kick in.  The power management does work to turn the monitor off, though.

---

