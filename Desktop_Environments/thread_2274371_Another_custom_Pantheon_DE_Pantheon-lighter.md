---
title: "Another custom Pantheon DE: Pantheon-lighter"
date: 2015-04-19
forum: Desktop Environments
---

### Post by quequotion on 2015-04-19
> **quequotion said:**
> [ElementaryOS's  Pantheon DE (cerbere, slingshot-launcher, wingpanel, plank) can be  installed independently of elementaryOS.]("http://ubuntuforums.org/showthread.php?t=2124220")
It's 2015, the  old how-to was updated, time for a new thread!
-Do check the old one  for background and updated, detailed how-tos on Pantheon 3d and Pantheon Lite.

Ubuntu Kylin (Vivid)
[[IMG]http://s1.postimg.org/xz2k9v7cr/Screenshot_from_2015_04_20_11_45_14.jpg[/IMG]]("http://postimg.org/image/xz2k9v7cr/")
My ancient IBM clone became a loaner to my zh_cn girlfriend.
Ubuntu  Kylin offers an all-in-one chinese-language and localization solution  with familiar corporate backing (recognizing a brand is important;  recognizing multiple brands at once is better).

While she's out of town, I'm using it for kicks.
It's weak, but it can run a Pantheon-like DE :D

Pantheon-lighter
[[IMG]http://s27.postimg.org/oe2t4m43j/pantheon_lighter.jpg[/IMG]]("http://postimg.org/image/oe2t4m43j/")
Another openbox variant; using the default session provided by openbox
#gnome-system-monitor:
Displaying resources while DVD-quality MPEG4:AC3,5.1:MKV plays in SMPlayer...

See the old thread for how-to the elementary PPAs!

::TODO:: LXDE PPA (optional)

Install the desktop components (compton is optional):
```
apt-get install lxpanel plank compton
```

Start all the needed components:
**/etc/xdg/openbox/autostart**:```
#
# These things are run when an Openbox X Session is started.
# You may place a similar script in $HOME/.config/openbox/autostart
# to run user-specific things.
#

# If you want to use GNOME config tools...
#
#if test -x /usr/lib/i386-linux-gnu/gnome-settings-daemon >/dev/null; then
#  /usr/lib/i386-linux-gnu/gnome-settings-daemon &
#elif which gnome-settings-daemon >/dev/null 2>&1; then
#  gnome-settings-daemon &
#fi

# If you want to use XFCE config tools...
#
#xfce-mcs-manager &

# Background Services - Watch OnlyShowIn=Gnome;Unity; autostarts...
gnome-keyring-daemon --start --components=gpg &
gnome-keyring-daemon --start --components=pkcs11 &
gnome-keyring-daemon --start --components=secrets &
gnome-keyring-daemon --start --components=ssh &
/usr/lib/gnome-user-share/gnome-user-share &
gsettings-data-convert &
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
/usr/lib/unity-settings-daemon/unity-settings-daemon-localeexec &
xdg-user-dirs-gtk-update &
#/usr/lib/gnome-fallback-media-keys-helper/gnome-fallback-media-keys-helper &

# "Pantheon" - Slingshot launcher broken: gala schema dependency; lxpanel lighter than wingpanel.
lxpanel &
plank &

# Indicators - Need GTK2 indicators for LXPanel?
sleep 2
#/usr/lib/i386-linux-gnu/indicator-application/indicator-application-service &
#/usr/lib/i386-linux-gnu/indicator-datetime/indicator-datetime-service &
#/usr/lib/i386-linux-gnu/indicator-messages/indicator-messages-service &
#/usr/lib/i386-linux-gnu/indicator-printers/indicator-printers-service &
#/usr/lib/i386-linux-gnu/indicator-sound/indicator-sound-service &
#/usr/lib/i386-linux-gnu/indicator-power/indicator-power-service &
#/usr/lib/i386-linux-gnu/indicator-session/indicator-session-service &

# Optional: Compositor - transparency, prettiness.
sleep 3
compton --dbus &
```

Logout!

Before the next login, select the openbox session in lightdm:
-Find an ubuntu icon near your name
-Click on the icon for the list of available sessions

---

### Post by quequotion on 2015-04-20
Her desktop is this snappy Ubuntu Kylin Custom Unity gig:
[[img]http://s4.postimg.org/7sf0prlm1/2015_04_20_12_51_04.jpg[/img]](http://postimg.org/image/7sf0prlm1/)

Ubuntu Kylin's compiz is reduced! Only 2D features included :(
It's highly stable! Even the Unity interface isn't that bad (she picked it up fast; it doesn't give me nightmares anymore).

It's like a fashionable mall coffee shop version of Ubuntu, if the mall were in Beijing.

Under the hood, Trusty was not bad but then I did a [distribution-upgrade](http://ubuntuforums.org/showthread.php?t=1485604) to Vivid and it was *even better*.

Note, that distribution-upgrade method is outdated (maybe); aptitude is better now and does a better job; and I discovered sed for fixing things in many text files at once.

---

