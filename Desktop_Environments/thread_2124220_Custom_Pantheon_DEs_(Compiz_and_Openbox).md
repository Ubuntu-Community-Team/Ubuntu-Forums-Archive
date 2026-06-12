---
title: "Custom Pantheon DEs (Compiz and Openbox)"
date: 2013-03-10
forum: Desktop Environments
---

### Post by quequotion on 2013-03-10
ElementaryOS's Pantheon DE (cerbere, slingshot-launcher, wingpanel, plank) can be installed independently of elementaryOS.

Add the PPA:
```
apt-add-repository ppa:elementary-os/stable
```
and if you're feeling adventurous:
```
apt-add-repository ppa:elementary-os/testing
```
and if you're crazy:
```
apt-add-repository ppa:elementary-os/daily
```

Update
```
apt-get update
```

Install the desktop components:
```
apt-get install pantheon-shell cerbere plank
```
Install these to satisfy some configuration dependencies:
```
apt-get install gala elementary-default-settings
```

Time to set up some pantheon-derivative desktops!

---

### Post by quequotion on 2013-03-11
Pantheon 3D:
[[IMG]http://i.imgur.com/HlJXb22l.jpg[/IMG]]("http://imgur.com/HlJXb22")

Replaces gala with compiz for a 3D, light and fast alternative to Unity.

Create a compiz profile with Unity disabled either [from Unity](http://ubuntuforums.org/showthread.php?t=2124239), or [another DE](http://ubuntuforums.org/showthread.php?t=2265978).

Install the window manager and configuration app:
```
apt-get install compiz compizconfig-settings-manager
```
Create the session files:
/usr/share/xsessions/pantheon-compiz.desktop```
[Desktop Entry]
Name=Pantheon 3D
Comment=This session provides elementary-3d experience
Exec=gnome-session --session=pantheon-compiz
TryExec=compiz
Icon=
Type=Application
```/usr/share/gnome-session/sessions/pantheon-compiz.session```
[GNOME Session]
Name=Pantheon
RequiredComponents=compiz;
FallbackSession=ubuntu
DesktopNames=Pantheon
```

---

### Post by Dry Lips on 2013-03-11
Interesting! I'm definitively going to bookmark this thread! :)

---

### Post by quequotion on 2013-03-16
Pantheon Lite:
[[IMG]http://i.imgur.com/xMB7MEKl.png[/IMG]]("http://imgur.com/xMB7MEK")

Replaces gala with openbox for a very light 2D alternative to Pantheon.

Install the window manager and configuration app:
```
apt-get install openbox obconf
```
Create the session files:
/usr/share/xsessions/openbox-pantheon.desktop```
[Desktop Entry]
Name=Pantheon Lite
Comment=This session provides elementary-lite experience
Exec=gnome-session --session=pantheon-openbox
TryExec=openbox
Icon=
Type=Application
```/usr/share/gnome-session/sessions/pantheon-openbox.session```
[GNOME Session]
Name=Pantheon
RequiredComponents=openbox;
FallbackSession=ubuntu
DesktopNames=Pantheon
```

Openbox is [*still* not getting packaged correctly]("https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1220257"), and the .desktop file has been removed as a result of the confusion.

This desktop file is needed to start openbox (eg, pantheon-lite) with gnome-session:
/usr/share/applications/openbox.desktop```
[Desktop Entry]
Type=Application
Name=Openbox
Exec=openbox
Icon=openbox
NoDisplay=true
# name we put on the WM spec check window
X-GNOME-WMName=Openbox
# gnome-session autostart
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
# Ubuntu stuff
X-Ubuntu-Gettext-Domain=openbox
# back compat
X-GNOME-Autostart-Notify=true
```

Please chime in on my bug report and insist that this be fixed (by packaging the correct .desktop file in "data/openbox.desktop").

---

### Post by quequotion on 2013-03-17
> **Dry Lips said:**
> Interesting! I'm definitively going to bookmark this thread! [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
Thanks!

I've got some updates already!

For a better looking Pantheon-lite (transparency, etc), add compton as a  compositor:```
sudo add-apt-repository ppa:richardgv/compton
sudo apt-get update && sudo apt-get install compton
```

/usr/share/gnome-session/sessions/pantheon-openbox.session```
[GNOME Session]
Name=Pantheon
RequiredComponents=openbox;compton;
FallbackSession=openbox
DesktopNames=Pantheon
```

Compton features a dbus interface which can do amazing things!

To start pantheon-lite with dbus-enabled compton, create an additional .desktop file:
/usr/share/applications/compton-dbus.desktop```
[Desktop Entry]
Version=1.0
Type=Application
Name=compton (dbus enabled)
GenericName=X compositor
Comment=A X compositor
Categories=Utility;
TryExec=compton
Exec=compton --dbus
```

Then specify compton-dbus in the session file:
/usr/share/gnome-session/sessions/pantheon-openbox.session```
[GNOME Session]
Name=Pantheon
RequiredComponents=openbox;compton-dbus;
FallbackSession=openbox
DesktopNames=Pantheon
```

Adding a compositor will improve the look of the desktop, but it also  consumes more resources (though certainly less than compiz and probably  less than gala).

As an example of what to do with the dbus interface, assign [this script]("https://github.com/chjj/compton/blob/master/dbus-examples/inverter.sh") to a hotkey to invert the color of the currently focused window.

---

### Post by quequotion on 2013-03-18
Optional stuff

Elementary Themes
For compiz apply the elementary theme with [GNOME Tweak Tool]("https://wiki.gnome.org/action/show/Apps/GnomeTweakTool?action=show&redirect=GnomeTweakTool"), [Ubuntu Tweak]("http://ubuntu-tweak.com/"), or dconf-editor
For openbox, there are several options. I reccomend to apply the [eGTK theme for openbox]("http://grvrulz.deviantart.com/art/elementary-for-openbox-253002995") with obconf.

Super-wingpanel
Super-wingpanel re-implements the original "super-sexy, space saving" design of wingpanel.```
apt-add-repository ppa:heathbar/super-wingpanel
``` or ```
apt-add-repository ppa:heathbar/super-wingpanel-daily
``` Super-wingpanel has not been updated upstream since Precise, but I have patched in support for new indicators and build fixes for newer versions of Ubuntu in the [archlinux packaging]("https://github.com/quequotion/pantheon-bzr-qq/tree/master/super-wingpanel-unstable-bzr").
If anyone who understands debian packaging wants to turn my version into a PPA, please do. I find debian packaging to be more difficult than writing programs.

---

### Post by quequotion on 2013-04-03
I gathered some statistics on each desktop's resource consumption.
The process statistics come from top running in gnome-terminal while no other windows are open.
The VRAM statisic comes from nvidia-settings GUI, while no other windows are open.
CPU usage was not enough to make note, although compiz consumes more than gala, openbox, or compton.

Pantheon Lite (with compositor)```
CMD       VIRT      RES  SHR
openbox   151m      10m  6336
compton   94812     20m  11m
VRAM: 49m
```Pantheon```

CMD       VIRT      RES  SHR
gala      613m      48m  31m
VRAM: 82m
```Pantheon 3D```

CMD       VIRT     RES  SHR
compiz    681m      186m 39m
VRAM: 201m
```Ayatana (Unity)```

CMD       VIRT      RES  SHR
compiz    1491m     301m 51m
VRAM: 291m
```

To enable vsync and improve performance (with the nvidia binary driver), I added some options to compton in Pantheon Lite. The increased resource consumption is still lower than the standard Pantheon desktop:
~/.config/compton.conf```
# Other
backend = "glx";
vsync = "opengl-swc";
paint-on-overlay = true;
unredir-if-possible = true;
```Pantheon Lite (with configuration)```

CMD       VIRT      RES  SHR
openbox   151m      10m  6356
compton   112m      28m  17m
VRAM: 73m
```

---

### Post by oldfred on 2014-06-16
reopened

---

### Post by flaymond on 2015-04-21
What is the difference between XFCE customized dock panel?

---

### Post by quequotion on 2015-07-13
> **InterProg said:**
> What is the difference between XFCE customized dock panel?
...and (super-)wingpanel?

You can customize XFCE panel to look and do the same as wingpanel, but not super-wingpanel.
Wingpanel is gtk3(+granite?) and a little shinier than xfce-panel, with several eye-candy features (but no hiding).

Super-wingpanel is another thing. The application launcher and status icon area can be split into two, independently auto-hiding panels. There's no better screenspace saving panel available (except perhaps the earliest versions of wingpanel).

Both have support for Unity 7 indicators (super-wingpanel does, with patches from me, in the Arch User Repository), but wingpanel is undergoing an identity crisis, hopefully becoming a little less dependent on Canonical-patched code.

Super-wingpanel is abandoned by it's creator. I'm considering making an official fork, but bzr gives me headaches.

Also, this thread is ancient: Ask the Elementary people about their panel! There's lots of stuff I don't know. I'm sure they visit these forums; they also have a handy irc channel on freenode.

---

### Post by Melodie on 2015-07-27
> **quequotion said:**
> Openbox is [*still* not getting packaged correctly]("https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1220257"), and the .desktop file has been removed as a result of the confusion.

This desktop file is needed to start openbox (eg, pantheon-lite) with gnome-session:
/usr/share/applications/openbox.desktop```
[Desktop Entry]
Type=Application
Name=Openbox
Exec=openbox
Icon=openbox
NoDisplay=true
# name we put on the WM spec check window
X-GNOME-WMName=Openbox
# gnome-session autostart
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
# Ubuntu stuff
X-Ubuntu-Gettext-Domain=openbox
# back compat
X-GNOME-Autostart-Notify=true
```

Please chime in on my bug report and insist that this be fixed (by packaging the correct .desktop file in "data/openbox.desktop").


Hello,

Lately I have tried to use Openbox in a Gnome3 session. I have also tried by using packages supposedly meant for this use. (Don't ask me what now, I would have to check my notes, just, even with the help and advice of darkxst, the leader of the Ubuntu Gnome project, I could not get it to work).

I stumbled upon this post of  yours and started to wonder about it and did a research to know more.

My actual situation : I use Ubuntu with Openbox, this is the Bento Openbox project I have been leading since 3 years. The version it relies on is Vivid, and I am using the Openbox version 3.6.0 provided by Mati75 on the Lubuntu testing ppa. 

- I don't have a /usr/share/applications/openbox.desktop file
- I have a /usr/share/xsessions/openbox.desktop file : which does not contain the same things as yours in the above code tags
- I have browsed inside the deb source files of the version Openbox 3.6.1 from sid, the version Openbox 3.5.2 from Debian Jessie and Ubuntu Trusty : they all have the openbox.desktop file exactly as you show above, in the data/ directory, in each of the source packages.

But in my install it does not show anywhere. Instead, in /usr/share/xsessions/ I have:
```

[Desktop Entry]
Name=Openbox
Comment=Log in using the Openbox window manager (without a session manager)
Exec=/usr/bin/openbox-session
TryExec=/usr/bin/openbox-session
Icon=openbox
Type=Application

```

I am particularly interested about the topic, as having Openbox for a possible window management replacement in different desktops can come very handy to make them lighter on machines having averagely low resources.

What do you think? Would you browse through your former bug reports again and see if there is one specifically dedicated to that topic?
[https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1220257](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1220257)
[https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1185502](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1185502)
[https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1255783](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1255783)

 If using the desktop file you advice, directly in /usr/share/applications, in a Ubuntu Gnome distribution for instance, would there be the need for additional packages to be installed for the Openbox session to work? (If you send me back to testing it, it's not a problem, just that I have an install of a recent Ubuntu Gnome on a hard drive which is for now out of it's computer, and I will need to put it all back in place one of these days, among other things).

Anyway it would be nice to have this one sorted out.

---

