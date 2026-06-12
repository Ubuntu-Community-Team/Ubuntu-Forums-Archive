---
title: "I want the old Gnome look and feel"
date: 2012-10-27
forum: Desktop Environments
---

### Post by SunfireSSR on 2012-10-27
Upgraded from 10.04 to 12.04 today. Running Gnome Classic Mode now. Does anyone have the steps to get all the windows slide bar mods / Put firefox in the top Panel / Edit the Panels  to get me back to the Gnome look ?

---

### Post by Frogs Hair on 2012-10-27
Gnome 2 was revived as the Mate desktop environment and can be installed on 12.04 . There is also customize Gnome classic thread on the forum by Kansasnoob.

Mate is based on pure Gnome 2 and won't include the modifications added in Ubuntu .   
[http://www.faqforge.com/linux/install-mate-desktop-on-ubuntu-12-04-precise-pangolin/](http://www.faqforge.com/linux/install-mate-desktop-on-ubuntu-12-04-precise-pangolin/)

---

### Post by Popaul on 2012-10-27
You can select this on the log-in screen without installing or uninstalling anything.
On the log-in screen, on the left or your name there's an Ubuntu logo. Click on it.
A menu appears with all the possibilities: Classic gnome etc...
Select the one you want, try them etc... to see which one is best for you.
Ooops... need to edit that. I was to quick. You are using this already.
To put Firefox etc... on the panel, in the old days you could just drag the icon from the menu to the panel, or right click on the panel to edit it.
The windows slide bar mods... not sure what you mean.

---

### Post by oldfred on 2012-10-27
Link to kansasnoob's thread and some of the commands I used. He also has instructions on how to undo something if you decide you do not like it.

To put an icon in the top panel you now have to  use alt key in addition to right click in panel.

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) - kansasnoob
sudo apt-get install gnome-session-fallback
sudo apt-get install gnome-tweak-tool
# this is same as fallback
sudo apt-get install gnome-panel
sudo apt-get install indicator-applet indicator-applet-session
Before you log in, click the gear icon and select GNOME Classic.
gconftool-2 --set "/apps/metacity/global_keybindings/panel_run_dialog" --type string "<Alt>F2"
gsettings set org.gnome.desktop.screensaver lock-enabled false
gsettings set com.ubuntu.update-notifier auto-launch false
#gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
sudo apt-get install shiki-colors-metacity-theme
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
gsettings set org.gnome.desktop.interface menus-have-icons true

---

### Post by SunfireSSR on 2012-10-30
I found MATE over the weekend and am a happy camper. Will figure out how to get Compiz working with it hopefully.

---

### Post by MadmanRB on 2012-10-30
Eh compiz and MATE dont get along.
Give XFCE a shot, its a little better under compiz

---

### Post by wojox on 2012-10-30
CentOS has it. :P

---

### Post by BBQdave on 2012-10-30
> **MadmanRB said:**
> Eh compiz and MATE dont get along.
Give XFCE a shot, its a little better under compiz

[Mint Xfce]("http://blog.linuxmint.com/?p=2088") is rather nice too :)

---

### Post by hictio on 2012-10-30
[Scientific Linux](https://www.scientificlinux.org/) offers you a plain vanilla GNOME2 desktop (the classic beauty ;) ) with support until 2020 or so, if you choose the 6.x release, which what you want to do :)
A truly amazing distro.

---

### Post by mosaic2s on 2012-10-31
try cinnamon desktop over 12.04 LTS. it is nice and works.

---

### Post by Dreamer Fithp Apprentice on 2012-10-31
If you haven't done much tweaking or written many scripts that alter the settings in any way you may find any of the above attractive, but if you HAVE invested considerable time doing that sort of thing you'll find classic mode, cinnamon, etc. a HUGE time sink to restore the function of your scripts and a modest additional time sink to figure out the new methods of customizing the UI manually. I played around with all that long enough to realize that I had already spent much more time at it than it was worth and I probably wasn't even half way there.

Right now, I only have enough HD space for 2 bootable systems. I still keep 10.04, Lucid, which is after all, still supported for a little while longer, on one, and on the other I try different things. Mate was pretty good and if, I repeat - IF, I stick with a gnome2-ish ubuntu (as opposed to a non-ubuntu with or without a gnome2-ish DE, or, if a Ubuntu, LXDE, which is NOT gnome2-ish, under Precise) after 10.04 I'll problably go back to it. PClinuxOS is also pretty good and I think, don't hold me to it, there is a gnome 2 option in it, though I didn't try it. I used it with LXDE which I like quite a bit.

Currently I'm trying LXDE under a minimal installation of Precise, built from the mini iso, a sort of not-quite-Lubuntu. I like LXDE in that environment too. It worked a little better in PClinuxOS but that may have been because I was using the 32 bit version of PClinuxOS (the 64 is still alpha) and the 64 bit version (which perhaps still isn't quite as mature bugwise as the 32?) of Precise and/or because I made the PClinuxOS installation from the light version, which isn't as mini as the Precise mini. None of which is to say any LXDE option is what you asked for. But if you are willing to work at it a bit more to get its config files beat into submission it sure is FAST and LIGHT.

If you use the search function, you'll find there is a LOT of stuff already posted on this topic, including several how-to posts, as quite a few of us, including me, were appalled at the change to Gnome 3 and Unity. You will even find the discussions were a bit heated at times as some of the stick-with-what-comes-out-of-the-box G3/U fans got a little hostile to those of us who weren't enthused about it. It is a major reason I haven't been on this forum in a while. I've been off exploring other distros altogether, including some in the BSD family.

Thanks to wojox and hictio for the heads up on CentOS and Scientific. I may audition them.

If you have the drive space, the best thing to do is to keep a system that you like on one partition and do your experimenting on another. That way, when you can't get x to start in the experimental system you can resist the urge to use a large hammer on your computer (not a recommended technique) and just reboot and google.

---

