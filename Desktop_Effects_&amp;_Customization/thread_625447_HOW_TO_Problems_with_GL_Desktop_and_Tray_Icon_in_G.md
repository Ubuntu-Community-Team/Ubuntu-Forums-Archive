---
title: "HOW TO: Problems with GL Desktop and Tray Icon in Gutsy 7.10"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by willie_wang on 2007-11-28
In response to [this thread]("http://ubuntuforums.org/showthread.php?t=585177") about problems with GL Desktop and the tray icon. If you have problems with the GL Desktop tray icon appearing intermittently, or not appearing at all, disappearing or not loading on startup or boot, the instructions below may help.

This may also help if you have the GL Desktop utility installed, but you have to wait a while for it to launch or have to click on the GL Desktop menu item twice to even get it to load.

This may not work for everyone, but it worked for me. So please let me know if you have these problems, whether they work for you.


**Uninstall the GL Desktop Menu Item and Install Advanced Desktop Effects Setting**

Uninstall the GL Desktop menu option by going to Synaptic Package Manager and uninstalling "gnome-compiz-manager". You need to be using the "compizconfig-settings-manager" instead, along with "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-main". it's up to you if you want to install the extra compiz-plugins. This will create a new menu item under System > Preferences > Advanced Desktop Effects Settings.

In the Advanced Desktop Effects Settings you'll be able to do everything you were able to in the buggy GL Desktop AND MORE... just takes a little playing about (which is actually soooo much fun) to learn what all the options do.

(You may have to go to System > Preferences > Appearance , then choose Custom from the Visual Effects tab to enable these extra effects.)

**Tray Icon Alternative - fusion-icon**

The GL Desktop tray icon can be very buggy on some machines. It was on mine too. There's a much better alternative that is just as good! It's called the fusion-icon. [Original Blog post about this is here]("http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/"), although to save you some time, I've copied the instructions to install the icon here.

The icon allows you to switch between metacity and compiz by simply right clicking the tray icon and choosing your window manager, effectively enabling or disabling your Desktop Effects very very quickly.

You can easily obtain it by:

1) Install git-core.

```
sudo apt-get install git-core
```

2) After installing, you need to grab the code. Run this command:

```
git-clone git://anongit.compiz-fusion.org/users/crdlb/fusion-icon
```

3) It should download stuff into a directory. Cd into that directory.

```
cd fusion-icon
```

4) Let&#8217;s make and install.

```
sudo make && sudo make install
```

Once you've done this, you can press Alt-F2 for the application launcher and type in "fusion-icon" to launch the tray icon. If you want your system to load this on boot, just go to System > Preferences > Sessions > Additional Startup Programmes and then add fusion-icon to the program list.

Hope this helps someone. It took me a good hour to figure this one out myself!

:KS

Anyway, thanks again to everyone who contributes to these forums. You've all encouraged me to do the same. And thanks again to all the Ubuntu Developers and testers! This post'll probably be missed by everyone, hehe :), but here's trying anyhow!!

This worked on my 64-bit version of Gutsy Gibbon, but may work for 32-bit versions too.

---

### Post by thinkgeek on 2008-02-19
Thanks, this worked great. Before I attempted this I did install the following first though

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool
```

I'm not sure that all of those are necessary, but I I know that some of them will be for the make command. Also, I intend to install the extra fusion plug-ins which do require all of the packages listed above.

---

### Post by stealthl on 2008-03-03
Thank you for the info. Worked perfectly for me
sv

---

### Post by swet on 2008-03-28
I am having this problem - I have uninstalled the GL desktop as Willie suggested above but I just can't get any of the effects to work...

I think this is relevent : I can't get any of the visual effects to select in the Appearance/Preference dialogue....I select a radio button but as soon as I do the radio button reverts to None with the message 'desktop effects could not be enabled'

I miss my wobbly windows, can anybody help

Regards

Ed

---

### Post by willie_wang on 2008-03-29
Hey Ed!

Were your desktop effects working with the GL Desktop settings?

It sounds as though you've got a problem with your driver settings/xorg.conf file. What graphics card do you have? I might be able to help if its an ATI card as I've spent hours fiddling with compiz and my own.

Willie

---

### Post by swet on 2008-04-03
Hi Willie

I have an old nvidea gforce2 mx100/200. The graphics worked fine in 7.04 but just stopped when I upgraded to 7.10. Sound has laso been a problem since the upgrade.

Any suggestions would be appreciated.

Regards

Ed

---

