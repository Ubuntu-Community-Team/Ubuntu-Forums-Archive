---
title: "Installing Skype"
date: 2006-01-04
forum: General Help
---

### Post by kenquad on 2006-01-04
Could someone please tell me EXACTLY how to install the latest version of Skype on my Kubuntu Breezy system?

---

### Post by DoorGunner on 2006-01-04
[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

I used this link and it worked fine.

---

### Post by Saruman on 2006-01-04
There's also an entry in the Starter Guide:

[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)

---

### Post by DoorGunner on 2006-01-04
actually that is probably the better one to use

---

### Post by kenquad on 2006-01-05
Thanks, but when I attempt to install thus, I get the error: ```
skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
``` (among other syntax).  When I try ```
sudo apt-get install libqt3c102-mt
``` I get ```
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
```.  But when I try ```
sudo apt-get install libqt3-mt
``` I find that it's already installed!  (This is confirmed by a quick look in synaptic.)  ???

---

### Post by WebDrake on 2006-01-05
[QUOTE=kenquad]Thanks, but when I attempt to install thus, I get the error: ```
skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
``` (among other syntax).[/quote]

My experience was that it's best not to use the .deb installer from Skype.  Just use the precompiled  binary, unzip it, there you go.  The .deb version needs libqt3c102-mt, which clashes with stuff necessary for the Kubuntu desktop and other KDE software.

---

### Post by kenquad on 2006-01-05
The good news is: IT WORKED--almost.  The bad news is that Skype now tells me it has a problem with the sound device.  I've gone to kcontrol and told the OS to let other applications take over the sound system after 0 seconds of idleness, but that didn't fix it.  ???

---

### Post by anil_robo on 2006-01-05
[quote=kenquad]The good news is: IT WORKED--almost. The bad news is that Skype now tells me it has a problem with the sound device. I've gone to kcontrol and told the OS to let other applications take over the sound system after 0 seconds of idleness, but that didn't fix it. ???[/quote]
Skype will have sound problems if some application is using the sound card. The trick I use when skype gives this error is to open up XMMS, play some song and then press the stop button 2-3 times. This disengages the soundcard and skype can then use it.
Remember, you can add echo123 to your friends list and test the sound.

---

### Post by kenquad on 2006-01-06
Actually I just went into Kcontrol and disabled the sound system.  This fixed the problem more or less--more because Skype now has sound, less because it's scratchy and skippy.  But that might be a Skype thing.  Anyway I can talk on it now.  Thanks.:smile:

---

### Post by neoflight on 2006-01-06
[QUOTE=kenquad]Could someone please tell me EXACTLY how to install the latest version of Skype on my Kubuntu Breezy system?[/QUOTE]


here is what I did....

use **AUTOMATIX** to install skype...no headaches and as easy as jelly...

details on automatix can be found here:
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

remember to [FONT="Courier New"]**sudo apt-get update**[/FONT] before using automatix...

to test if it works...
add _echo123_ as a friend and call...follow instructions...and u r all set...

how did it go???

---

