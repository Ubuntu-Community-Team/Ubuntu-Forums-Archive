---
title: "Diggin' more and more Gnome questions!"
date: 2005-07-15
forum: Desktop Environments
---

### Post by fresco on 2005-07-15
Hello brothers!

Here's my set of freshly-popped-up questions.  :grin: 

1. Does the Gnome use .desktop files to keep user settings? For example, there's a tool called Smeg for customizing personal menues.  But is it possible to manage these settings manually, without using it? (Don't want to feel myself like windows user and   :^o ) In HOME/.gconf, .gconfd. .gnome2 etc. I have found only xml files.
 
2. Trere's a path in .gnome2 (or some other, it doesn't matter) called panel2(?)/launchers where all user launchers on the panel are kept. So, I tried adding there .desktop files from /usr/share/applications/ but it was useless - launchers didn't show up on the panel. Otherwise, when i add launcher to the panel using drag'n'drop, everything is fine - it appears on the panel and in /launchers dir.
So, what's the difference between those files? I refreshed panel using killall gnome-panel but nothing.  O:) 

3. When I installed xine-ui, I associated xine-ui to play multimedia files using command from ubuntu-guide,
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list

Ok,  I did myself stupid. How can I rooll back these changes? Don't want do open multimedia using xine, i like rhytmbox and xine-totem. Can someone describe me what to do with these settings?

---

### Post by Caboto on 2005-07-15
I can only answer one question...
1. Yeah. There are .desktop files. They are kept in /usr/share/applications/. A possible entry for NVU would be:
```
[Desktop Entry]
Name=Nvu
Comment=Web Development Editor
Exec=nvu
Icon=nvu.xpm
Terminal=false
Type=Application
Categories=Application;Network;
```
you can simply create new .desktop files and fill it with what you want. don't really know what's needed, but you should be fine with the above variables. Smeg doesn't do anything else. (I don't ask, why you don't want to use Smeg. It's a nice program which save you some time...)
btw. the above code is just taken from [ubuntuguide.org](http://ubuntuguide.org/#nvu).

I hope, I did understand you question right and could help you.

---

