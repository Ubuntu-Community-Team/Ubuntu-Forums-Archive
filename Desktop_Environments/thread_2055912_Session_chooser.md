---
title: "Session chooser"
date: 2012-09-10
forum: Desktop Environments
---

### Post by JKyleOKC on 2012-09-10
Using Xubuntu 12.04.1 with the standard LightDM login screen, I'm offered the choice between two sessions at login. One is "Xubuntu session" and the other is "Xfce session" (I do not save sessions automatically at exit).

However I see almost no difference in operation or appearance between the two. The only difference I've found is that "Xubuntu session" seems to stutter when starting the desktop. That is, I get the splash screen for about a second, then the monitor goes dark for a couple of seconds, then the splash screen comes back while the desktop initializes.

If I select "Xfce session" the stutter isn't there. The splash screen comes up almost instantly, progresses through its sequence, and the desktop appears fully initialized.

So my question is: what is the expected difference between the two sessions? Or is there supposed to be a difference at all?

---

### Post by raja.genupula on 2012-09-10
I think this will help you a bit

[http://askubuntu.com/questions/91380/what-is-the-difference-between-ubuntuxfce-and-xubuntu](http://askubuntu.com/questions/91380/what-is-the-difference-between-ubuntuxfce-and-xubuntu)

---

### Post by JKyleOKC on 2012-09-10
Unfortunately that doesn't help at all. I'm quite familiar with xubuntu, having used it since version 7.04. What I'm looking for is the difference -- if there is any -- between the two sessions offered at login. Listing the current session from the tab in the "startup and session settings" dialog fails to show any difference, and the only thing I see different is absence of the "stutter" when starting the Xfce session.

---

### Post by LewisTM on 2012-09-10
This [thread]("http://ubuntuforums.org/showthread.php?t=1895108") has a discussion on the subject.
Bottom line is : Xfce Session has different, less styled defaults.

---

### Post by Toz on 2012-09-10
Here is my understanding of the difference (unverified). Xfce session is the default Xfce while Xubuntu is Xfce with a few "tweaks".

However, it gets complicated because the two share the same configuration files, so once you log in as one session, the other one will look similar because of the configurations that you've made. To really see the difference, you need to create separate accounts and login as each session.

The next logical question then is "what are these tweaks"? I believe these tweaks come from the xubuntu-default-settings package. Here are the contents:
```
$ dpkg -L xubuntu-default-settings 
/.
/etc
/etc/xdg
/etc/xdg/xdg-xubuntu
/etc/xdg/xdg-xubuntu/xfce4
/etc/xdg/xdg-xubuntu/xfce4/panel
/etc/xdg/xdg-xubuntu/xfce4/panel/indicator-5.rc
/etc/xdg/xdg-xubuntu/xfce4/panel/default.xml
/etc/xdg/xdg-xubuntu/xfce4/panel/datetime-7.rc
/etc/xdg/xdg-xubuntu/xfce4/xfconf
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfprint.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/thunar-volman.xml
/etc/xdg/xdg-xubuntu/xfce4/helpers.rc
/etc/xdg/xdg-xubuntu/Terminal
/etc/xdg/xdg-xubuntu/Terminal/terminalrc
/etc/xdg/xdg-xubuntu/autostart
/etc/xdg/xdg-xubuntu/autostart/xfce4-tips-autostart.desktop
/etc/xdg/xdg-xubuntu/menus
/etc/xdg/xdg-xubuntu/menus/xfce-applications.menu
/etc/xdg/xdg-xubuntu/Thunar
/etc/xdg/xdg-xubuntu/Thunar/thunarrc
/etc/xdg/xdg-xubuntu/Thunar/uca.xml
/etc/xdg/xdg-xubuntu/lightdm
/etc/xdg/xdg-xubuntu/lightdm/lightdm-gtk-greeter.conf
/etc/xdg/xdg-xubuntu/orage
/etc/xdg/xdg-xubuntu/orage/oragerc
/etc/skel
/etc/skel/.xscreensaver
/etc/skel/.Xdefaults
/usr
/usr/share
/usr/share/xsessions
/usr/share/xsessions/xubuntu.desktop
/usr/share/xubuntu
/usr/share/xubuntu/applications
/usr/share/xubuntu/applications/Thunar-bulk-rename.desktop
/usr/share/xubuntu/applications/xfhelp4.desktop
/usr/share/xubuntu/applications/debian-xterm.desktop
/usr/share/xubuntu/applications/debian-uxterm.desktop
/usr/share/xubuntu/applications/Thunar.desktop
/usr/share/xubuntu/applications/defaults.list
/usr/share/xubuntu/applications/xfce4-terminal.desktop
/usr/share/doc
/usr/share/doc/xubuntu-default-settings
/usr/share/doc/xubuntu-default-settings/copyright
/usr/share/doc/xubuntu-default-settings/changelog.gz
/usr/share/glib-2.0
/usr/share/glib-2.0/schemas
/usr/share/glib-2.0/schemas/20_xubuntu-default-settings.gschema.override
/usr/share/gconf
/usr/share/gconf/defaults
/usr/share/gconf/defaults/20_xubuntu-default-settings
```

Those files should hold the information about what these tweaks are. For example:
```
$ more /usr/share/glib-2.0/schemas/20_xubuntu-default-settings.gschema.override
[com.canonical.indicator.sound]
interested-media-players=[ 'gmusicbrowser' ]
show-notify-osd-on-scroll=false

[com.ubuntu.update-notifier]
auto-launch=false

```
.../usr/share/glib-2.0/schemas/20_xubuntu-default-settings.gschema.override seems to:
[LIST=1]
[*]set gmusicbrowser as the sound indicator music player
[*]turn off notify-osd on scroll
[*]disable the update-notifier
[/LIST]

I believe this might get even a little more complicated because the tweaks are applied when you log in the first time (ie. ~/.config/xfce4 is created). If your first login is as Xfce-session, then you won't get the tweaks applied even if subsequent logins are via Xubuntu-session. In addition, I believe that Xfce-session uses the template files in /etc/xdg/xfce4 to create the initial profile and Xubuntu-session uses the template files in /etc/xdg/xdg-xubuntu but I can't seem to find in the code where and how this distinction happens. The desktop files in /usr/share/xsessions seem to run the same executable.

---

### Post by JKyleOKC on 2012-09-10
Thanks to both of you; that was what I wanted to know!

The explanation from Toz tends to shed some light on the "stutter" I experience in the xubuntu session; apparently this session tries to refer to something that's not there, and has to start itself over. Which is fine. Now that I know there's no significant difference to the two, after the first-time login, I'll simply leave it set for the non-stuttering xfce session on my account...

---

### Post by jeremija on 2013-07-31
I realize it's been almost a year since the last post, but this has been bothering me for the past few hours and I think I came to a conclusion about how this works.

As the **/etc/xdg** folder is actually a system-wide equivalent of **~/.config**. It can be seen in the **/usr/bin/startxfce4** file that the path **/etc/xdg** is exported to the enviroment variable **$XDG_CONFIG_DIRS**.

The problem which I had was I didn't know which xfce4-session.xml file should I change to use compiz instead of xfwm4. I had two xfce4-session.xml files:
```
/etc/xdg/xdg-xubuntu/**xfce4**/xfconf/xfce-perchannel-xml/xfce4-session.xml
/etc/xdg/**xfce4**/xfconf/xfce-perchannel-xml/xfce4-session.xml
```

As I used the **xfce.desktop** session instead of the **xubuntu.desktop** (located in **/usr/share/xsessions**), my **$XDG_CONFIG_DIR** variable was:
```
XDG_CONFIG_DIRS="/etc/xdg/xdg-xfce:/etc/xdg:/etc/xdg"
```
Which means it will first look in the **/etc/xdg/xdg-xfce** folder to look for configuration and then will use the **/etc/xdg** as a fallback. As I do not have the **xdg-xfce** folder, the xfce4 configuration from **/etc/xdg/xfce4** is used.

What bothered me was that I wanted to know where did that **/etc/xdg/xdg-xfce** value come from. A quick grep resulted in this:
```
$ grep -rIsnE XDG_CONFIG_DIRS=.*?xdg- /etc/*
/etc/X11/Xsession.d/60x11-common_xdg_path:11:  **XDG_CONFIG_DIRS="$DEFAULT_XDG_CONFIG_DIRS"/xdg-**"$DESKTOP_SESSION":"$XDG_CONFIG_DIRS"
```
The **$DEFAULT_XDG_CONFIG_DIRS** is set to **/etc/xdg** in the same file on line 4.

This helped me to realize that the **$DESKTOP_SESSION** variable was to blame, so I did an another grep:
```
$ grep -rIsnE DESKTOP_SESSION= /etc/*
/etc/xdg/xfce4/xinitrc:21:  **DESKTOP_SESSION**="xfce"
```

These are the lines around that very line:
```
# set DESKTOP_SESSION so that one can detect easily if an Xfce session is running
if test "x$DESKTOP_SESSION" = "x"; then
  **DESKTOP_SESSION="xfce"**
  export DESKTOP_SESSION
fi
```

The **/etc/xdg/xfce4/xinitrc** file is actually called from both **xfce.desktop** and **xubuntu.desktop** as they both call startxfce4 and startxfce4 calls xinitrc.

My guess was that the display manager such as lightdm sets both the **$GDMSESSION** and the **$DESKTOP_SESSION** enviroment variables (as they were both set to xfce) from the name of the xsession *.desktop file used for login. Then I downloaded the source code of lightdm to check for sure and an another grep showed that my guess was right:
```
$ apt-get source ligthtdm
$ cd lightdm-1.6.0
$ grep -rIsnE GDMSESSION\|DESKTOP_SESSION *
NEWS:598:    * Set PATH, **DESKTOP_SESSION**, **GDMSESSION** and USERNAME environment variables
src/display.c:732:    session_set_env (display->priv->session, "**DESKTOP_SESSION**", display->priv->user_session); // FIXME: Apparently deprecated?
src/display.c:733:    session_set_env (display->priv->session, "**GDMSESSION**", display->priv->user_session); // FIXME: Not cross-desktop

```

Luckily I did not have to look futher into the code as the NEWS file had this documented.

I hope this post helps somebody in the future!

---

### Post by normadize on 2013-11-30
@[**[COLOR=#000000]jeremija[/COLOR]**]("http://ubuntuforums.org/member.php?u=314357")

I know it's a further year later but many thanks for your investigation! I was surprised that this is not documented properly.

I'm on a headless virtual machine which had a bare Ubuntu 12.04. I manually installed xubuntu-desktop (*apt-get install xubuntu-desktop*). This makes LightDM start automatically.

I need VNC access to it and the usual way is to install and configure *x11vnc*. That works fine, and it offers vnc access to the LightDM login screen from which I can start a Xubuntu session, with all its XFCE customizations.

**The problem:**

x11vnc is utterly slow in comparison to Xvnc from vnc4server or tightvncserver. I wasted half a day already trying to understand why and fix it (I also posted on [stackoverflow]("http://stackoverflow.com/questions/20297931/x11vnc-much-slower-than-xvnc-both-vnc4server-and-tightvncserver") about it). As I care about my sanity, I decided to use vnc4server/tightvncserver started manually. These cannot connect to the root display :0 so they create a new X session on :1 or above, independent of LightDM which becomes redundant; so I can stop LightDM altogether.

So, I want to start a Xubuntu session (i.e. XFCE with the Xubuntu customizations) manually on a display :1 or above via Xvnc. If I do just "*startxfce4*" then it starts the plain xfce session, not the xubuntu session. vnc4server/tightvncserver basically execute *~/.vnc/xstartup* which is a script where you can put any command to start your X session.

I'm glad I stumbled upon your guide. I'll report back once I try to make "startxfce4" use the Xubuntu customizations when started manually.

Thanks once again.

---

### Post by normadize on 2013-11-30
And I'm happy to report that it seems to have been a success. If I edit ~/.vnc/xstartup to contain only

    ```
#!/bin/sh
export XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/etc/xdg:/etc/xdg
export XDG_DATA_DIRS=/usr/share/xubuntu:/usr/local/share/:/usr/share/:/usr/share
. lightdm-session
```

You can replace *". lighdm-session"* with *"startxfce4 &"* if you wish; the former is really what lightdm calls. Then do:

```
vncserver :1 -depth 16 -geometry 1280x800
```

Then XFCE seems to apply the Xubuntu customizations. I can certainly see the gray background terminal with smaller fonts (Xubuntu), instead of the black background terminal with ridiculously large fonts (default XFCE).

Many thanks once again for the valuable pointers!

p.s. XFCE thinks there is already a server on :2 when starting vncserver above. The vncserver log says:
30/11/13 10:45:08 Listening for VNC connections on TCP port 5902
/usr/bin/startxfce4: X server already running on display :2

But then it works so I'll probably give it a rest for now...

---

