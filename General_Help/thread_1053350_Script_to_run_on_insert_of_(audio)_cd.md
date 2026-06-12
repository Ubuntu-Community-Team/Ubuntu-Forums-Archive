---
title: "Script to run on insert of (audio) cd"
date: 2009-01-28
forum: General Help
---

### Post by AbsolutIggy on 2009-01-28
Hello,

does anyone know if it possible to set which script is run when a CD is inserted into a drive? Preferably depending on type, eg. I want to run the script automatically when an audio CD is inserted, but not when CD containing images or whatever is inserted.

I know about the 'preferred applications' menu, but that's not quite what I'm looking for..

---

### Post by khedron on 2009-01-28
The HAL (hardware abstraction layer) handles stuff like the CD-ROM drive.
Look into **ivman**. 
[http://ivman.sourceforge.net/](http://ivman.sourceforge.net/)
From the homepage:
> Ivman is a generic handler for [HAL]("http://freedesktop.org/wiki/Software_2fhal") events. Originally for automounting, it can now be used to run arbitrary commands when events or conditions occur or properties are modified on your hardware (e.g., run a command when you close your laptop's lid, run a command when a particular device is attached or a particular CD is inserted, etc).If this seems a bit too involved, you can always try continuously checking for the disk:
```

while ! head -c1 /dev/cdrom &>/dev/null; do 
sleep 1; 
done
# Put code here

```

---

### Post by khedron on 2009-01-28
So what you would do is
```

sudo aptitude install ivman
sudo vim /etc/ivman/IvmConfigActions.xml
# Read the file and try your own concoctions

```Example from the file given above:
```

    <!-- example - autoplay CDs with audio tracks and no data tracks -->
    <!--
    <ivm:Match name="hal.volume.disc.type" value="cd_rom">
        <ivm:Match name="hal.volume.disc.has_audio" value="true">
            <ivm:Match name="hal.volume.disc.has_data" value="false">
                <ivm:Option name="exec" value="/usr/bin/cdplay -d '$hal.block.device$' -c" />
            </ivm:Match>
        </ivm:Match>
    </ivm:Match>
    -->

```Just replace the "/usr/bin/cdplay -d '$hal.block.device$' -c" with your own command and remove the** <!--** and** -->** comment lines.

* Edit: from that same file it says that you can also try a local config file:*
> 
         For autoplaying of CDs etc, it is recommended to put an entry in the
         file ~/.ivman/IvmConfigActions.xml and have that user run their
         own instance of Ivman (e.g. in ~/.kde/Autostart).


---

### Post by AbsolutIggy on 2009-01-29
Thanks, I'll try that out a bit later..

---

### Post by geirha on 2009-01-29
It shouldn't be necessary to change the HAL configuration. The default configuration of HAL already alerts gnome-volume-manager when an audio cd is inserted, so you'll only need to configure gnome-volume-manager.

From a terminal or Alt+F2, run ```
gconf-editor
``` then browse to /desktop/gnome/volume_manager/ and look at the keys autoplay_cda and autoplay_cda_command.

---

### Post by AbsolutIggy on 2009-01-29
geirha, that does seem quite a bit simpler for this purpose (but ivman seems interesting for other things.. may end up using it anyway)

I've disabled 'autoplay_cda' in gconf-editor for now. However, rhythmbox still starts when I insert an audio CD. Anybody know how to stop it doing this? Can't find any options for this. I tried changing the default multimedia player, but that doesn't make a difference. (I'm on 8.04, if it makes any difference..)

---

### Post by AbsolutIggy on 2009-01-29
Nevermind that last question, I found the answer. Apparently, Nautilus also checks what you insert and has its own actions.

(Edit->Preferences->Media)

---

### Post by mc4man on 2009-01-29
It's pretty easy to set a script to run on inserting an audio cd (or any thing that triggers an auto run event actually

For instance on I run a script to allow amarok to autoplay cd's from either drive. On 8.10 it only takes a few seconds to set up , 8.04 needs a few steps.
Read here for general idea, (links a bottom for non traditional uses
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

use with amarok, (you can adapt, just an example of line you'd use in mimeapps, you can use an existing .desktop that's unused for autorun, copy one with a name change, or create a new one.

[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

I'm sure you can get the idea

In 8.10 you'd just use the custom command box in preferences -> media (creates a userapp.desktop

---

