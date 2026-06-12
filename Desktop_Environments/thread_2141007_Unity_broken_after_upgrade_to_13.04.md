---
title: "Unity broken after upgrade to 13.04"
date: 2013-05-01
forum: Desktop Environments
---

### Post by sigdrifa on 2013-05-01
Hi all,

the upgrade to raring broke Unity on my default user account. When I log into an Ubuntu session, it won't load the wallpaper, and nothing happens on right-clicking the desktop. This problem only occurs with my regular user account; when I log into a guest session, everything works fine.

I've had problems with Unity on 12.10, too; it would start alright, but after less than a minute it would crash; there wouldn't be any window decorations anymore, no panels and no dash. unity --replace would fix that, though, but now that doesn't make a difference. I tried resetting unity with both methods listed here: [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html) . That didn't solve the problem either.

Here's the output I get after starting Unity from the command line, don't know if this is of any help:

```
[tanja@desktop:~]$ unity --replace
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
WARN  2013-05-01 08:12:33 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-05-01 08:12:33 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
WARN  2013-05-01 08:12:33 unity.libindicator <unknown>:0 Desktop file '/usr/local/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-05-01 08:12:33 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2013-05-01 08:12:33 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2013-05-01 08:12:33 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
WARN  2013-05-01 08:12:33 unity.glib.dbus.proxy GLibDBusProxy.cpp:418 Calling method "CanHibernate" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-05-01 08:12:33 unity.session.gnome GnomeSessionManager.cpp:334 logind CanHibernate call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-05-01 08:12:33 unity.glib.dbus.proxy GLibDBusProxy.cpp:418 Calling method "CanSuspend" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-05-01 08:12:33 unity.session.gnome GnomeSessionManager.cpp:334 logind CanSuspend call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files

```

Help would be very much appreciated.

---

### Post by dino99 on 2013-05-01
compiz --replace ccp &
setsid unity

---

### Post by sigdrifa on 2013-05-01
> **dino99 said:**
> compiz --replace ccp &
setsid unity

Nope... That didn't change anything either. Is there some configuration file or directory in my home folder that I can try moving?

---

### Post by Frogs Hair on 2013-05-01
What grapics card  ? ```
lspci
``` Unity Support Test: ```
/usr/lib/nux/unity_support_test -p
```

---

### Post by sigdrifa on 2013-05-01
> **Frogs Hair said:**
> What grapics card

It's an NVidia GeForce 8600 GT, but I doubt that this is a graphics card issue; as I said, the problem occurs only with my default user account - guest account works fine.

---

### Post by sinaen on 2013-05-01
i have geforce 540m and no glx present

havent found any solution to get NVIDIA or compiz/unity to work :-/

---

### Post by Frogs Hair on 2013-05-02
> [COLOR=#000000]It's an NVidia GeForce 8600 GT, but I doubt that this is a graphics card issue[/COLOR] I agree because I have a similar card . I have read about this  before were the guest account works but not the user account . Try searching in that context because resetting unity again nay not work.

---

### Post by father_ted on 2013-05-04
Im having this problem with fglrx driver. So its not exclusively an nvidia problem. my guest account works perfectly - just my main account is gimped.

For a giggle i ran the unity support test and everything is ok.

ive tried all the variations of unity and compiz reset.

---

### Post by Highland23 on 2013-05-04
I am having the same problem, i tried to toggle filemanager managing desktop, changed variables in dconf...nothing helped. Even a reinstall of unity didn helped.
Where can i look else? Where is the location of the Desktop Wallpaper stored so i would manually remove or change it.

---

### Post by bogan on 2013-05-05
**Originally Posted by bogan in Ubuntu +1**: [http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435) There is a long list of alternative reset commands in that Thread.
Hi!,** All,**> My Blank Desktop problem with 13.04 has been cured by using a terminal in Fallback  mode to enter the reset unity command included in Unity-Tweak-Tool: ```
sudo apt-get install unity-tweak-tool 
echo $DESKTOP_SESSION  
fallback-compiz   
gksudo unity-tweak-tool --reset-unity 
Warning: You are about to reset unity to its default configuration.
   It is normal for your desktop to flicker during the process.   
Type yes to continue, anything else to exit.      Do You wish to continue? _ 
```On rebooting all the log-in options' displays were correct and with intact Launchers and Panels.

 Running the same commands when logged into the faulty Ubuntu/Unity Blank  Desktop gave a 'Can not open display' message and did nothing.

It is probable - though I have not tried it - that the other compix/unity reset commands would also work if run in the same way.

Chao!, **bogan**.

---

### Post by echo6 on 2013-05-06
Having the same issues after upgrade.
The last post didn't fix it for me.

Which package provides fallback-compiz and gksudo?

This is on laptop with an Intel graphics card.

---

### Post by bogan on 2013-05-06
> **echo6 said:**
> Having the same issues after upgrade.
The last post didn't fix it for me.

Which package provides fallback-compiz and gksudo?

This is on laptop with an Intel graphics card.Install with apt-get:
```
sudo apt-get install gnome-session-fallback # reboot and login to 'Fallback'
sudo apt-get install gksu
```Please Post:```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```If still not solved.

Chao!, **bogan.**

---

### Post by theoden9017 on 2013-05-07
same problem here, all start when i tried to install nvidia driver.

that is my output, using those commands

```
theoden@theoden-Aspire-5830TG:~$ uname -r
3.8.0-19-generic
theoden@theoden-Aspire-5830TG:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:055b]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 540M] [10de:0df4] (rev ff)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:055b]
    Kernel driver in use: atl1c
theoden@theoden-Aspire-5830TG:~$ /usr.lib/nux/unity_support_test -p
bash: /usr.lib/nux/unity_support_test: File o directory non esistente


```
pls help me

---

### Post by bogan on 2013-05-07
Hi!, **Theoden9017.**

Sorry, I put in a typo:> /usr.lib/nux/unity_support_test -p 
bash: /usr.lib/nux/unity_support_test: File o directory non esistenteIt should be:```
/usr/lib/nux/unity_support_test -p
```IE a forward stroke after '/usr'.


Either the support_test or: ```
glxinfo | grep -i opengl # or:
sudo lshw -C display
```Should show if the GT 540M is being used and what driver it has; as lspci, recognised it but did not show a driver .

Though it could be turned off in Bios.Uefi

Are you using Bumblbee? As this is a Laptop with Hybrid Graphics you probably need it.

Chao!,** bogan.**

---

### Post by theoden9017 on 2013-05-08
i solved my problem using this command


```
dconf reset -f /org/compiz/
```

anyway yes i using bumblebee cause my video card have nvidia optimus

funfact: i have do all this for playing dota 2 on linux using my dedicated video card, but with the intel integrated video card have better FPS :/ i'll try nouveau

---

### Post by echo6 on 2013-05-26
If I run sudo su first then run unity-tweak-tool it works, but after that my desktop session is root.  If I run as suggested in the earlier post I get an error
```
[~]$ gksudo unity-teak-tool --reset-unity
gksudo: unrecognised option '--reset-unity'
GKsu version 2.0.2
```

---

### Post by echo6 on 2013-05-26
> **bogan said:**
> If still not solved.

```
3.8.0-19-generic
```

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
        Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
        Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
```

```
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile
OpenGL version string:  3.0 Mesa 9.1.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

AND of course unity --reset is deprecated.....Deprecated for what? What has replaced it??

Running "unity-tweak-tool --reset-unity" with as normal user then doing a reboot appears to have fixed the issue!

---

### Post by bogan on 2013-05-26
Hi!,** Echo**6,

You Posted:> AND of course unity --reset is deprecated.....Deprecated for what? What has replaced it??'unity --reset' is replaced by 'setsid unity' but you probably also need to run: 'unity --reset-icons'.

In practice the 'reset-unity' option with unity-tweak-tool is, in my experience, more effective and less productive of confusing error messages. As with 'setsid', you need to reboot afterwards for the changes in the config files to be effective.


Glad you got it working OK.

Chao!,** bogan.**

---

### Post by echo6 on 2013-05-27
> **bogan said:**
> In practice the 'reset-unity' option with unity-tweak-tool is, in my experience, more effective and less productive of confusing error messages. As with 'setsid', you need to reboot afterwards for the changes in the config files to be effective.

Thanks Bogan that is good to know.

Kinda annoying when you get messages about options being deprecated without any indication as to what has replaced it.  Even the man page for unity specifies --reset option as still being available.

---

### Post by [Knuckles] on 2013-10-27
Just wanted to add that I broke unity by trying to start it with a broken amd driver install, and after fixing the driver install unity was still not loading, but using "unity-tweak-tool --reset-unity" fixed it for me. Thanks!

---

### Post by ralfs2 on 2014-10-08
Ctrl + Alt + F1 to open system shell
 goto the home directory of your user account and check the permissions of .Xauthority with *ls -l .Xauthority* (to make visible hidden files type ls -a ..)
**if it is owned by root**
 type *sudo chown -c yourusername:yourusername .Xauthority*

i had the same problem after sudo apt-get dist-upgrade and this was the error


[FONT=Arial][/FONT][FONT=Arial][CENTER]Enter Cookie as format:
(ex: name=val;) separate with ';'

[/CENTER]
OKCancel[/FONT]

---

