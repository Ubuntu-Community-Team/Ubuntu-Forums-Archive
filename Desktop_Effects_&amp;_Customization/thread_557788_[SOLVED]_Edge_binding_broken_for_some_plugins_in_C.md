---
title: "[SOLVED] Edge binding broken for some plugins in Compiz Fusion after upgrading to Gut"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by circle on 2007-09-23
Hello all,

I was using Feisty + Compiz Fusion from the unofficial eyecandy repository ([http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy) and everything was ok.

Last night I had a dist-upgrade to Gusty and met some problems on the screen edge binding. I bind to the ButtomLeft corner to the display the desktop (in the general settings) but it have no effect. However, using the shortcut key Ctrl+Alt+D works great. I have also tried binding the Left and Right edit together with edge button 1 to Rotate cube left and right, and they don't work either. Like the case for BottomLeft edge, using the hot key Ctrl+Alt+Left/Right works fine.

I also noticed that I failed to drag & drop the windows to other desktop like what I did in Feisty. I tried to reset all settings to defaults but this doesn't help.

I have tried to bind those edge/corners to other plugins (e.g. Expo, Scale Windows) and they just work, so I guess it may not be the problem in the edge handler.

FYI, here are the version of Compiz-Fusion I have installed.
```
$ dpkg -l compiz compiz-* compizconfig-settings-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                               Description
+++-=====================================-=====================================-==========================================================================================
ii  compiz                                1:0.5.2+git20070918-0ubuntu5          OpenGL window and compositing manager
un  compiz-compcomm-plugins-main          <none>                                (no description available)
ii  compiz-core                           1:0.5.2+git20070918-0ubuntu5          OpenGL window and compositing manager
un  compiz-extra                          <none>                                (no description available)
ii  compiz-fusion-plugins-extra           0.5.2+git20070917-0ubuntu1            Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-main            0.5.2+git20070917-0ubuntu3            Collection of plugins from OpenCompositing for Compiz
pn  compiz-fusion-plugins-unofficial      <none>                                (no description available)
pn  compiz-fusion-plugins-unsupported     <none>                                (no description available)
ii  compiz-gnome                          1:0.5.2+git20070918-0ubuntu5          OpenGL window and compositing manager - GNOME window decorator
rc  compiz-gtk                            1:0.3.6-1ubuntu13                     OpenGL window and compositing manager - Gtk window decorator
ii  compiz-plugins                        1:0.5.2+git20070918-0ubuntu5          OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager         0.5.2+git20070912-0ubuntu1            Compiz configuration settings manager
```Any idea? Thanks!

---

### Post by hyperair on 2007-09-23
There are problems with the dist-upgrade method. I'm going for a full reinstall later today or maybe tomorrow. Try making CCSM use a flat file backend adn see how it goes.

---

### Post by Forlong on 2007-09-23
You can't upgrade with Trevino's packages, because they are not compatible with Gutsy.
Just remove them, disable the repository and install **compiz** as well as **compizconfig-settings-manager** again.

---

### Post by Forlong on 2007-09-23
> **hyperair said:**
> There are problems with the dist-upgrade method.
Not really. You just have to make sure to remove any third-party packages (and their repositories) and install the (k/x)**ubuntu-desktop** metapackage.

---

### Post by circle on 2007-09-23
Thanks. Actually when I upgrade to Gutsy, apt complains that those compiz packages have some dependency problem, so I disabled the repository, removed those packages and installed again.

Just try to remove all those packages and install again, not working either.

Here is what I have done:
```
metacity --replace &
apt-get remove compiz compiz-* compizconfig-* emerald
apt-get install compiz compiz-fusion-* compizconfig-* emerald
compiz --replace -c emerald &
```

I notice that after the re-installation, my compiz configs are still here. Do I need to remove them and try again? How?

BTW, I have removed the ubuntu-desktop metapackage. I installed tpb for setting the special keys of my Thinkpad and removed the hotkey-setup package (which will further removed the ubuntu-desktop package too)

---

### Post by circle on 2007-09-23
Just noticed one interesting observation: whenever I close and restart the compizconfig-settings-manager (ccsm), the mentioned edge binding are lost. I set those edge bindings again (with no effect, as expected) and restart ccsm, they are lost again.

I tried to open gconf-editor and navigate to apps > compiz, the edge settings are still there:
```
general/allscreens/options/show_desktop_edge = BottomLeft
plugins/rotate/allscreens/options/rotate_left_button = <LeftEdge>Button1
plugins/rotate/allscreens/options/rotate_right_button = <RightEdge>Button1
```strange enough :(

---

### Post by Forlong on 2007-09-23
Remove Compiz like this (switch to Metacity first via *System &#8594; Preferences &#8594; Appearance &#8594; Desktop Effects &#8594; No Effects*):
```
sudo apt-get remove --purge compiz* emerald* && sudo apt-get autoremove && sudo apt-get clean
```

If you want to remove your configs as well, do this:
```
rm -r ~/.config/compiz
```
And you can delete the gconf-keys too:
```
rm -r ~/.gconf/apps/compiz
```
You should reboot then. The folder will get created again, when you run Compiz for the first time.

Then install Compiz:
```
sudo apt.get install compiz compizconfig-settings-manager
```
And before you run Compiz for the first time, run
```
ccsm
```
and switch to the Flat-file Backend in Preferences.


If you have any problems then, post the output of:
```
dpkg -l | grep compiz
```

---

### Post by hyperair on 2007-09-23
No Forlong, there are bugs. Check out the hamachi forums, the Linux section, a thread to do with Ubuntu Gutsy. Someone installed Tribe 5 and Hamachi worked. The rest who upgraded via apt didn't manage to get hamachi running. I, too have that problem.

---

### Post by Forlong on 2007-09-23
Sorry, I thought you were talking about upgrading in general.
I can't speak for hamachi, of course - but Compiz worked for me after upgrading.

---

### Post by circle on 2007-09-23
Thanks! It works now!

I guess there is some conflicts in the old configuration. Removing all the configuration works great now!

I have also switch to flat-file backend, sounds more straight forward :)

Thanks!

---

### Post by circle on 2007-09-24
Just FYI, I found that if you want to drag and drop windows to other desktop, besides enabling the "Flip Edge Move" (or "Flip Edge DnD" if you want to enable the drag and drop object over different viewport) settings in the RotateCube plugin, you also need to set the screen edge of the "Rotate Flip Left" and "Rotate Flip Right" edge action. However ccsm may warn you for conflicts with the "Rotate Left" and "Rotate Right" edge (only if you want to do something similar to what i describe in my first post), I just ignore the warnings and choose "Set it anyway", now it works fine for me. I may not present the idea well so here's part of the config:
```
"Rotate Left": Left Edge + Button 1
"Rotate Right": Right Edge + Button 1
"Rotate Flip Left": Left Edge
"Rotate Flip Right": Right Edge
```

Just wanna raise the idea that it is possible to do something like this :)

---

