---
title: "Icons in panel rearrange themselves"
date: 2010-04-19
forum: Desktop Environments
---

### Post by Weepleman on 2010-04-19
Hi, when the screen resolution on my computer, and sometimes when I just turn on my computer the launchers or icons, or whatever they are called, are all moved around in the panel.  Is there any program that will restore the icons with a click or something.  I have already tried locking the panel, but that does not work.

---

### Post by TitanusEramius on 2010-04-20
>  I have already tried locking the panelHave you tried locking the icons themself? 
You can do this by right-clicking on them and press the bottom choice, lock to panel.

---

### Post by drs305 on 2010-04-20
I wrote a script to save my panel icons & positions. The script saves the current panel setup to a file, *panel.saver.sh*, on the user's Desktop. Change the filename and locations as desired.

The script uses *zenity* to provide a GUI interface and offers selections to save or restore the panel settings. If the settings are restored, the panel is then refreshed using the command "killall gnome-panel".

If *zenity* is not currently installed (from the *main* repository) you can install it with this command:
```
sudo apt-get install zenity
```

To run the script, download and make it executable. This can be done by selecting the file's "Properties" in a file browser or running the following command (with the correct location):
```
chmod +x /path-to-file/panel.saver.sh
```

You can place a shortcut on the panel and restore the saved settings/positions with a few clicks.

> 
#!/bin/bash
# This script by drs305 saves or restores a user's panel icons/positions in Ubuntu.

ans=$(zenity  --list  --text "Save or Restore Panel Settings?" --radiolist  --column "Pick" --column "options" TRUE "Save_Panel"  FALSE "Restore_Panel"  FALSE "Exit"  --separator=":"); echo $ans

if [ $ans = "Save_Panel" ]; then
	gconftool-2 --dump /apps/panel > $HOME/Desktop/panel_saved
	exit 
fi 	
if [ $ans = "Restore_Panel" ]; then
	gconftool-2 --load $HOME/Desktop/panel_saved
	killall gnome-panel
	exit 
fi
if [ $ans = "Exit" ]; then
	exit 
fi
exit


---

### Post by Weepleman on 2010-04-20
Thanks, that worked really well.  I did change it to save to my home folder though, but that is not a big deal.  Thanks a lot for that.

---

### Post by BrokeMahPC on 2010-04-22
An update in Linux Mint last year caused me some wondering / duplicating panel icon trouble.
If you just want to restore the default panels and put them back to how they looked at install, use this:
```
gconftool-2 --recursive-unset /apps/panel
```
```
killall gnome-panel
```

---

### Post by ram130 on 2010-10-16
Can't believe this bug was never fixed! It's annoying as hell. I've installed Ubuntu on at least 5 client machines since 9.04 and this keeps happening...5/10 boot ups the panel icons would rearrange to somewhere different or some will not appear...This is VERY annoying! I can't believe it's not fixed after so long!

---

### Post by phredbull on 2010-10-16
> **ram130 said:**
> I can't believe it's not fixed after so long!
Right! Who cares about a lightning fast startup time, when you have to spend another minute restoring your desktop settings by hand!

---

### Post by rafe.kettler on 2010-10-17
My problem seems to stem from changing monitors. The icons seem to rearrange themselves only when I use my laptop screen instead of an external monitor or vice versa. It's rather annoying.

Thanks for the solutions, BrokeMahPC and drs305. I'll have to try those out next time I have this problem.

---

