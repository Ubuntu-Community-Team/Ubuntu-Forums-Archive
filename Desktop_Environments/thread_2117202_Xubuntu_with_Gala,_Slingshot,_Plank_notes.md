---
title: "Xubuntu with Gala, Slingshot, Plank: notes"
date: 2013-02-17
forum: Desktop Environments
---

### Post by Bruce McL on 2013-02-17
**Why:** Speed and ease of use. I have an old HP Pavilion DV600 computer, with 1GB RAM and 100 MB HD. It's not my primary computer, just something to mess around with. In the past I found Xubuntu to be a good compromise of speed, ease of use and availability of apps. When Elementary OS Luna Beta came out, I tried that and liked the look. However, it wasn't particularly fast and I couldn't get my networked printer to work. Xubuntu with Gala feels faster than Xubuntu alone or Elementary Luna alone. With Slingshot and Plank it looks like Elementary.

**How:**
add Elementary repos from terminal
```
sudo add-apt-repository ppa:elementary-os/daily
sudo apt-get update
```
install Synaptic Package Manager from Software Center

install Gala from Synaptic Package Manager
to start Gala automatically, copy the config file
```
cp /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
```
Open the copied file in a text editor and replace "xfwm4" with "gala" in one place.

Install slingshot-launcher from Synaptic.
Add an app launcher to the top panel, choose "run program," specify slingshot-launcher as the command.
To speed up opening Slingshot the first time, add an item to Settings Manager> Session and Startup> Application Autostart> startup services. specify "slingshot-launcher -s" as the command.

Install plank from Synaptic.
Add an item to Settings manager> Session and Startup> Application Autostart> startup services. Specify plank as the command.

**Tuning and Tweaking:**
Settings Manager> Appearance still works for changing the window appearance theme in Gala. Note that Settings Manager does not show up in Slingshot, you can right click on the desktop to run Settings Manager. Once it's open you can keep it in the dock.
For changing the window manager theme in Gala, install gnome-tweak-tool from Synaptic. Gnome-tweak-tool> theme> current theme will change the window manager theme. Again, gnome-tweak-tool does not show up in Slingshot. You can use "Run Program," then you can keep it in the dock.

I like Open Sans as a system font. It is available in Synaptic as fonts-open-sans.

Use dconf-editor to change the position of the open, minimize, and close buttons. This setting is in dconf Editor> org> pantheon> gala> appearance.
For Windows style buttons
```
:minimize,maximize,close
```
For Mac style buttons
```
close,minimize,maximize:
```
You can use dconf-editor to make other changes in Gala.

In the top panel, I named my Slingshot launcher "Applications" and checked "show label instead of icon" and "disable tooltips" in the advanced section of the launcher.
You can use dconf Editor> org> pantheon> slingshot for changing the number of rows and columns, size of icons, and a few other things.

You can remove the Plank icon from the dock. To do so, delete or rename plank.dockitem, located in ~/.config/plank/dock1/launchers.
More info on Plank is located here: [https://answers.launchpad.net/plank]("https://answers.launchpad.net/plank")

I am not an expert on Linux. I am writing this post because I had a hard time finding information about how to tune and tweak this setup. Corrections or alternate suggestions are welcome.

Here is one source of general info on this modification I found helpful: [http://www.reddit.com/r/linux/comments/14heuu/xfce_gala_plank_awesome/]("http://www.reddit.com/r/linux/comments/14heuu/xfce_gala_plank_awesome/")

---

### Post by Bruce McL on 2013-03-01
As with the post above, I'm still trying to get the most out of an old laptop, but my strategy has changed. Since I don't see much information about modifying Xubuntu in this way on the web, I am posting followup info.

I switched from gala window manager to mutter. Mutter performs about as well as gala, and it's more mainstream. Installation is similar to gala, only you don't need the elementary software repositories. Install mutter via Synaptic Package Manager or with the following command:

```
sudo apt-get install mutter
```

Make mutter the default window manager with the following:

```
cp /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

leafpad ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
```

In leafpad, change one instance of xfwm (or gala) to mutter. Save, and restart.

To change the window manager theme use gnome-tweak-tool, theme tab, current theme. To change other window manager settings use dconf-editor. Preferences are in org:gnome:desktop:wm and in org:gnome:desktop:wm:preferences

...

I find PCManFM to be much more responsive than Thunar. It can be installed with Synaptic Package Manager. To make it the default, go to Settings Manager, Preferred Applications, Utilities tab.

I like to access PCManFM using the Places plugin in the top panel. If the plugin is not installed already, it's called xfce4-places-plugin in Synaptic.

To stop Thunar from running in the background, open the file you created above:

```
leafpad ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
```

Note the following lines:

```
<property name="Client3_Command" type="array">
        <value type="string" value="Thunar"/>
        <value type="string" value="--daemon"/>
      </property>
      <property name="Client3_PerScreen" type="bool" value="false"/>
```

Change them to look like this and save:

```
<property name="Client3_Command" type="array">
        <value type="string" value=""/>
      </property>
      <property name="Client3_PerScreen" type="bool" value="false"/>
```

Restart and check your work in Settings Manager: Session and Startup: Session tab. Thunar should no longer be in the list.

---

### Post by Bruce McL on 2013-05-05
Openbox is one other window manager option that is worth a try. I think the performance is better than xfwm, mutter, or gala. It's also easy to install and doesn't add a lot of dependencies.

On the negative side, the top and sides of the windows don't look quite as nice. Also, transparency, shadows, and other effects require an extra app which is not easy to configure.

install openbox with synaptic or sudo apt-get install. Open up the ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml file that you created in the first post and replace xfwm, gala, or mutter with openbox. Logout and log in and the change is complete.

Open Settings Manager and you should see Openbox Configuration Manager. Use that instead of Window Manager and Window Manager tweaks.

For transparency, install excompmgr. To enable it, run excompmgr -c in terminal. To enable it permanently, go to Settings Manager: Session and Startup: Application Autostart: Startup Services. Add excompmgr to the list of applications to start up. Use the command excompgr -c

To set up excompmgr, you add more options to the -c. Look around on the internet and you will see a lot of posts with specific recommendations for excompmgr options. I haven't added any more options yet, so I don't have any recommendations.

Once you do this you may be tempted to move to Lubuntu or even crunchbang to see if they perform better than Xubuntu. But that's another story, which doesn't fit in this thread.

---

### Post by themind24 on 2013-05-25
Hi,
I successful installed Gala on Xubuntu 13.04, but I have a question about workspace management:
in Elementary OS the workspace are shown and managed at bottom with the possibility of move windows from a workspace to another; how can I obtain it in xubuntu too?
I tried setting this operation is command in an active corner but nothing happened.
Thanks!

---

### Post by Bruce McL on 2013-05-25
In xfce, workspace management is handled by xfdesktop. This is still running when you install Gala. If you disable xfdesktop you might get the gala desktop management. Or you might have to install more pieces from elementary os.

---

### Post by themind24 on 2013-05-25
Thanks.
I disabled xfdesktop but gala doesn't manage workspace yet :S
I don't know if is necessary install other elementary's component :S

---

### Post by Bruce McL on 2013-05-26
I don't know what else to suggest. I am not using gala with xfce anymore.

---

### Post by ManualSparrow on 2013-05-26
> **themind24 said:**
> Thanks.
I disabled xfdesktop but gala doesn't manage workspace yet :S
I don't know if is necessary install other elementary's component :S
You probably need to install pantheon-desktop to get the workspace switcher to work. But you probably want to check out elementaryos.org, or the #elementary IRC channels for more information about elementary-specific components.
However: Why bother running xfce at all, if you're doing to replace the file, desktop, and window managers? On an older system, those are the light, fast components that distinguish xfce from kde, gnome, etc. Also, consider upgrading to the latest xfce version (4.12) via ppa: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12). There are a lot of nice updates, like tabs in Thunar, dropdown options in xfterminal, and better support for window snapping.

---

### Post by Bruce McL on 2013-05-26
> **ManualSparrow said:**
> However: Why bother running xfce at all, if you're doing to replace the file, desktop, and window managers? 

The latest beta (Luna beta 2) of Elementary OS runs much smoother on my machine than the last one. So I agree it may be worth a try. In my testing it does take more memory than xfce. If you are at 1Gb of RAM or less then Elementary may not work well.

---

### Post by WRAYC on 2013-06-15
I love Luna like crazy but not enough resources on my dv5000 with only 1gb ram although I still have it on my hard drive with manjaro, hybryde and LXLE. Yea, I'm bit of a linux junky. I'm hoping eventually they might offer a "Luna Light" but somehow I doubt it.

---

### Post by Bruce McL on 2013-06-15
I agree with you; I don't think a light version of Elementary is coming any time soon. They are focused on getting their first and only OS out of beta and into release right now.

It's fun to try different releases. On my hard drive I also have WattOS, which is based on Ubuntu and Lxde. I like WattOS, it seems to run a little bit better than Lubuntu and other Lxde distros I have tried.

---

### Post by screaminj3sus on 2013-06-26
I'm still running XFCE with gala here (was using compton for a while, but missed gala's nice animations and expose feature). I've also been a little curious as to exactly what packages would be needed to get gala's workspace management working in XFCE, but its no big deal.

I would use luna, its turning out very nice and for the most part is already usable; but unfortunately it being based on 12.04 is a deal-breaker for me. Ubuntu 12.04 has a very annoying and still unfixed bug where I randomly start getting graphical artifacts on the indicators that don't go away until I *completely reboot*, its bizarre and drives my OCD crazy. Happens on the two totally different laptops I have too (ony system76 lemur ultra, less than a year old with intel ivybridge, the other an asus u52f from 2010). Maybe elementary +1 will be usable for me :( I don't see the problem in 13.04.

Its pretty sad how the bug has zero activity aside from being pushed back over and over :/ [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/998704](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/998704)

/rant

For now Xubuntu 13.04 + plank and gala is a very nice solution for me, very fast and no annoying bugs.

---

### Post by grigio2 on 2013-11-08
Hi guys,
I love Elementary (specially Gala WM) and Ubuntu Community and Support, can you confirm if Xubuntu + Gala setup still work on Ubuntu 13.10?

---

