---
title: "Is there a terminal command to edit system preferences?"
date: 2009-03-28
forum: General Help
---

### Post by Pipps on 2009-03-28
Can anything be in a Ubuntu system be edited using a command in the terminal?

For instance, I would like to be able to effect a command, which will do exactly the same as if I were to click:

Menu > Preferences > Sound > Sounds tab > Untick 'Play alerts and sound effects'.

Can this sort of thing be done?

---

### Post by sekinto on 2009-03-28
Almost all settings in Ubuntu are stored as text files, which can be edited from a console (with something like Nano or Vim).


There is also the gconf command which can be used to edit many settings, gconf-editor is like regedit in Windows and gconf can edit the same things but from a console.

---

### Post by ddrichardson on 2009-03-28
Most of these settings apps are available with options from the command line. If you do ```
gnome-sound-properties --help-all
```You'll get a list of what can be done from the command line. Haven't used this in a while so your mileage may vary.

---

### Post by Pipps on 2009-03-28
Thanks for your help. Ok, that command returns the following output for me:

```

Usage:
  gnome-sound-properties [OPTION...] - GNOME Sound Preferences

Help Options:
  -?, --help                        Show help options
  --help-all                        Show all help options
  --help-gst                        Show GStreamer Options
  --help-gtk                        Show GTK+ Options
  --help-bonobo-activation          Show Bonobo Activation options
  --help-gnome                      Show GNOME options
  --help-gnome-session              Show session management options

GStreamer Options
  --gst-version                     Print the GStreamer version
  --gst-fatal-warnings              Make all warnings fatal
  --gst-debug-help                  Print available debug categories and exit
  --gst-debug-level=LEVEL           Default debug level from 1 (only error) to 5 (anything) or 0 for no output
  --gst-debug=LIST                  Comma-separated list of category_name:level pairs to set specific levels for the individual categories. Example: GST_AUTOPLUG:5,GST_ELEMENT_*:3
  --gst-debug-no-color              Disable coloured debugging output
  --gst-debug-disable               Disable debugging
  --gst-plugin-spew                 Enable verbose plugin loading diagnostics
  --gst-plugin-path=PATHS           Colon-separated paths containing plugins
  --gst-plugin-load=PLUGINS         Comma-separated list of plugins to preload in addition to the list stored in environment variable GST_PLUGIN_PATH
  --gst-disable-segtrap             Disable trapping of segmentation faults during plugin loading
  --gst-disable-registry-update     Disable updating the registry
  --gst-disable-registry-fork       Disable the use of fork() while scanning the registry

GTK+ Options
  --class=CLASS                     Program class as used by the window manager
  --name=NAME                       Program name as used by the window manager
  --screen=SCREEN                   X screen to use
  --sync                            Make X calls synchronous
  --gtk-module=MODULES              Load additional GTK+ modules
  --g-fatal-warnings                Make all warnings fatal

Bonobo Activation options:
  --oaf-ior-fd=FD                   File descriptor to print IOR on
  --oaf-activate-iid=IID            IID to activate
  --oaf-private                     Prevent registering of server with OAF

GNOME Library
  --disable-sound                   Disable sound server usage
  --enable-sound                    Enable sound server usage
  --espeaker=HOSTNAME:PORT          Host:port on which the sound server to use is running
  --version                         

Session management:
  --sm-client-id=ID                 Specify session management ID
  --sm-config-prefix=PREFIX         Specify prefix of saved configuration
  --sm-disable                      Disable connection to session manager

Application Options:
  --apply                           Just apply settings and quit (compatibility only; now handled by daemon)
  --init-session-settings           Just apply settings and quit (compatibility only; now handled by daemon)
  --get-legacy                      Retrieve and store legacy settings
  --display=DISPLAY                 X display to use

```
I'm not sure exactly how I might change the sound alerts with this, though! Can you help me further please?

---

### Post by ddrichardson on 2009-03-28
I don't really understand why you want to use this particular app to control audio properties nor a circumstance where from the command line alsactl or alsamixer wouldn't do it.

What are you trying to do?

---

### Post by Pipps on 2009-03-28
Thank you for your reply. I should provide a little background to my question.

I have recently found myself regularly reinstalling Ubuntu for various reasons which I need not expand upon here. As a safety measure for future potential installations, and as a mechanism which would hopefully save time, in order to customise the system exactly to my liking each time I reinstall it from fresh, and thereby instead of having to click around in the system preferences, I would prefer to simply be able to effect all of the desired changes using commands in the terminal, or possibly scripts, if either route would provide the desired results.

What do you think of this approach? Would a terminal command be available to simply turn off the sounds and alerts in the Ubuntu sound settings?

---

### Post by ddrichardson on 2009-03-28
You sound though you'd be better creating hard disk images to restore from. I use System Rescue CD to boot in and partimage to image the drive to a USB hard disk.

Then every time the machine needs reinstalled I restore the image.

If it's purely desktop settings then tarring your home folder would back up all your settings.

---

### Post by dcstar on 2009-03-28
> **Pipps said:**
> Thank you for your reply. I should provide a little background to my question.

I have recently found myself regularly reinstalling Ubuntu for various reasons which I need not expand upon here. As a safety measure for future potential installations, and as a mechanism which would hopefully save time, in order to customise the system exactly to my liking each time I reinstall it from fresh, and thereby instead of having to click around in the system preferences
......

Simply have a separate /home partition, all those settings are stored there in your user profile and this will not be touched during any re-installation.

There are numerous HOWTOs in the forum on this.

---

### Post by ethoxyethaan on 2009-03-28
most options are stored in Configuration files,

you can edit them from a terminal in Vi or nano

some configuraitonfiles use sqlLite or mysql and they require that you know mysql queries.

some app's provide command line parameters to edit settings.

---

### Post by Saibot Sivad on 2009-05-27
I apologize for bringing this back to the top, but this is the same question that I have, and no answer was ever found/given. I will restate the question in my words, although it is the same as before:

Is there a way to modify the "System > Preferences > Sound" properties completely from the terminal? For example, and specifically, I want to toggle the check-mark "Play alerts and sound effects" without having to open the graphical interface.

In the Sound Preferences, it implies that the sounds can be modified by installing a "Sound Theme", I also found "Sound Themes" over at gnome-look.org, but it appears that each sound change is done manually.

If the option of modifying the sound preferences through the command line is not available, can someone identify which file(s) are modified?

In my searching around, it sure seems that the Sound Themes could use some attention: I would be willing to give it that attention since I need it, but please someone give me a starting point?

---

### Post by Yellow Pasque on 2009-05-27
> GNOME Library
  --disable-sound                   Disable sound server usage
  --enable-sound                    Enable sound server usage

Try these options and see if the corresponding "alerts and effect sounds" checkbox has changed in the GUI dialog.

---

### Post by Pipps on 2009-05-27
> **Saibot Sivad said:**
> Is there a way to modify the "System > Preferences > Sound" properties completely from the terminal? For example, and specifically, I want to toggle the check-mark "Play alerts and sound effects" without having to open the graphical interface.

This is also exactly what I would really like to be able to do.

If anyone knows of a 'coded' way of changing all the usual fiddly system settings, rather than using the GUI, then I would be very grateful to hear it!

---

### Post by Saibot Sivad on 2009-05-28
Surprisingly, it responds like this:
```
Unknown option --disable-sound
```
So I checked to see what --help-all gives:
```
Usage:
  gnome-sound-properties [OPTION...] - GNOME Sound Preferences

Help Options:
  -?, --help                        Show help options
  --help-all                        Show all help options
  --help-gst                        Show GStreamer Options
  --help-gtk                        Show GTK+ Options

GStreamer Options
  --gst-version                     Print the GStreamer version
  --gst-fatal-warnings              Make all warnings fatal
  --gst-debug-help                  Print available debug categories and exit
  --gst-debug-level=LEVEL           Default debug level from 1 (only error) to 5 (anything) or 0 for no output
  --gst-debug=LIST                  Comma-separated list of category_name:level pairs to set specific levels for the individual categories. Example: GST_AUTOPLUG:5,GST_ELEMENT_*:3
  --gst-debug-no-color              Disable colored debugging output
  --gst-debug-disable               Disable debugging
  --gst-plugin-spew                 Enable verbose plugin loading diagnostics
  --gst-plugin-path=PATHS           Colon-separated paths containing plugins
  --gst-plugin-load=PLUGINS         Comma-separated list of plugins to preload in addition to the list stored in environment variable GST_PLUGIN_PATH
  --gst-disable-segtrap             Disable trapping of segmentation faults during plugin loading
  --gst-disable-registry-update     Disable updating the registry
  --gst-disable-registry-fork       Disable the use of fork() while scanning the registry

GTK+ Options
  --class=CLASS                     Program class as used by the window manager
  --name=NAME                       Program name as used by the window manager
  --screen=SCREEN                   X screen to use
  --sync                            Make X calls synchronous
  --gtk-module=MODULES              Load additional GTK+ modules
  --g-fatal-warnings                Make all warnings fatal

Application Options:
  --apply                           Just apply settings and quit (compatibility only; now handled by daemon)
  --init-session-settings           Just apply settings and quit (compatibility only; now handled by daemon)
  --display=DISPLAY                 X display to use
```
So its obviously not there. Should it be there in the default install, or did that change with the 9.04 release?

---

### Post by Saibot Sivad on 2009-05-29
#bump

Any way to interact with the gnome-sound-properties through the command line?

---

### Post by mcduck on 2009-05-29
Enable "Play alerts and sound effects":
```
gconftool-2 --type boolean --set "/desktop/gnome/sound/event_sounds" "true"
```

...and disable the same setting:
```
gconftool-2 --type boolean --set "/desktop/gnome/sound/event_sounds" "false"
```

---

### Post by kaibob on 2009-05-29
> **Saibot Sivad said:**
> ...Is there a way to modify the "System > Preferences > Sound" properties completely from the terminal? For example, and specifically, I want to toggle the check-mark "Play alerts and sound effects" without having to open the graphical interface....

Building on mcduck's suggestion, you can use the following shell script, which acts as a toggle. It can be run from a terminal window or assigned to a custom launcher. 

```
#!/bin/bash

STATE=$(gconftool-2 --get /desktop/gnome/sound/event_sounds)

if [ $STATE = true ] ; then
   gconftool-2 --type bool --set /desktop/gnome/sound/event_sounds false
else
   gconftool-2 --type bool --set /desktop/gnome/sound/event_sounds true
fi
```

BTW, in Hardy this script toggles the "Play System Sounds" option. I assume that this option was renamed in Jaunty.

---

### Post by Saibot Sivad on 2009-05-29
Many many thanks go to mcduck for this invaluable code!

I noticed there is a missing quotation mark at the beginning of the directory list, noting that it becomes:
```
gconftool-2 --type boolean --set "/desktop/gnome/sound/event_sounds" "true"
```

Kaibob, thank you for that script as well! I am writing in perl, but that was a good thing to know as well!

Looks like I will be fiddling with the gconftool-2 for a while!

I think it is safe to call this post Solved, since a clear answer was given to the original question. I am not the original poster, so...

---

### Post by Pipps on 2009-05-29
Gentleman, thank you for your astounding efforts. Saibot, please keep me updated with your further work in this area. It is of great interest to me. Thank you again, one and all.

---

