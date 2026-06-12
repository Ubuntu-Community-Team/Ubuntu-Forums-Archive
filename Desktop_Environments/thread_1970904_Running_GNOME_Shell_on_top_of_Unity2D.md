---
title: "Running GNOME Shell on top of Unity2D"
date: 2012-05-01
forum: Desktop Environments
---

### Post by vanlong441 on 2012-05-01
Youtube video [COLOR=Red](New)[/COLOR]

GNOME Shell + Unity2D [ http://www.youtube.com/watch?v=nW-PqT4fx0w]("http://www.youtube.com/watch?v=nW-PqT4fx0w")
Cinnamon + Unity2D [http://www.youtube.com/watch?v=65wVYifJk-I](http://www.youtube.com/watch?v=65wVYifJk-I)

[SIZE=3][COLOR=Red]*Important:[/COLOR][/SIZE]

+ There has been an issue of prolonged loading time of DE [COLOR=Red]because of[/COLOR] LightDM. The solution is to use GDM instead of LightDM. A how-to can be found here [http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

+ Restarting GNOME Shell causes HUD and Unity Dash to malfunction. Restarting only the Shell Theme (rt instead of r in Alt F2) is OK though.

+ When Logging out or Shutting down, try to use the menu of GNOME Shell. Otherwise, the *gnome-session* will likely hang (open System monitor and kill *gnome-session* in order to restart). This is because GNOME Shell in running on top of Unity, it is in control.

[SIZE=3][COLOR=DarkGreen]*My customization[/COLOR][/SIZE]
[COLOR=DarkGreen]
[SIZE=2]Unity-2D[/SIZE][/COLOR]

Dconf-tools must be installed first

```
sudo apt-get dconf-tools
```+ By default when you are going with GNOME Shell on top of Unity, tabbing the left <Super> key will bring up Overview. For people who don't like this, we can ship Overview to the right <Super> key.

```
dconf-editor
```Navigate to *Org.gnome.mutter* >> *overlay-key* >> change from *Super_L* to *Super_R*

Log out and log back.

+ Do you know that by clicking on the launchers that have more than one opening window, a small Overview will come up (like an app-switcher)? If you are experiencing SLOW performance with this function (I mean slow, not ugly, because mine is also ugly for we are running in mutter, not compiz), follow this:

```
dconf-editor
```Navigate to *com.canonical.unity-2d* >> check [I]use-opengl

[/I]Log out and log back.

+ To change color of the Unity Dash:

```
dconf-editor
```Navigate to *com.canonical.unity-2d* >> averrage-bg-color >> change the color code (codes can be got from [**here**]("http://www.color-hex.com/color-wheel/") by clicking on one of the color box and then clicking on the color wheel)

+ Stop showing apport (crash report dialogs). This will not disable crash reporting. We can still silently support Ubuntu.

```
dconf-editor
```Navigate to *com.ubuntu.update-notifier *>> uncheck *show-apport-crashes*

[SIZE=3]**How-to with GNOME Shell:**[/SIZE]

1/ Install Gnome-tweak-tool (this will install all other necessary packages)

```
sudo apt-get install gnome-tweak-tool
```2/ Make sure you are in Unity-2d session, then type *gnome-shell --replace* in the terminal

```
gnome-shell --replace
```*To make this permanent, add that command line to start-up applications.

3/ Open the link below and install the gnome-shell extension to auto-hide the top-panel of Gnome Shell, so we can see that of Unity-2D, which has Appmenu and other applets on it.

[https://extensions.gnome.org/extension/208/panel-settings/](https://extensions.gnome.org/extension/208/panel-settings/)

After 15s or less, there will be a new icon on the top-panel of GNOME Shell. Click on it >> Visibility >> Autohide. All done.

*Extras:

Now you can enjoy the GnoUnity experience: move your mouse to the top  edge to reveal the GNOME Shell panel, to the top-left corner to reveal  Hot Corner, to the bottom edge to reveal notification bar; press the  <super> key or Alt F1 to reveal GNOME Shell overview. There are some other tips if you really want to get into this weird type of desktop environment.

4/ To be able to use many other extensions of GNOME Shell as well as to change the theme of GNOME Shell:

```
sudo add-apt-repository ppa:ricotz/testing 
sudo apt-get install ppa-purge 
sudo apt-get update 
sudo apt-get install gnome-shell-extensions 
sudo ppa-purge ppa:ricotz/testing 
```*(type N and press enter at the end of the process)   *

Restart the shell (Alt F2 >> R >> Enter) or just log out and log back in.

Other GNOME Shell extensions can be found here [https://extensions.gnome.org](https://extensions.gnome.org)

GNOME Shell themes can be found here [http://gnome-shell.deviantart.com/gallery/28081982](http://gnome-shell.deviantart.com/gallery/28081982)

5/ Customize Unity2D: 

Very good tips about Unity2D can be found here [http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html) (keep in mind that Unity2D is NOT the same as Unity3D) or you may want to take a look at the Important and My customization at the beginning of this thread.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[SIZE=3]**How-to with Cinnamon:**[/SIZE]

1/ Install Cinnamon stable

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update 
sudo apt-get install cinnamon
```2/ Make sure you are in Unity-2d session, then type *cinnamon --replace* in the terminal

```
cinnamon --replace
```*To make this permanent, add that command line to start-up applications.

3/ To further tweak Cinnamon:

```
sudo add-apt-repository ppa:bimsebasse/cinnamonextras
sudo apt-get update
```And install the themes and applets that you like.

---

### Post by cecilpierce on 2012-05-02
Nice! How do you do that ?

---

### Post by forrestcupp on 2012-05-02
My favorite part of the video is where at the end it says "A how-to can be found in the description below of this video", and the description of the video says "No description available." :D

Why would you even want to do this, though? It just seems wrong. ;)

---

### Post by cecilpierce on 2012-05-02
> **forrestcupp said:**
> My favorite part of the video is where at the end it says "A how-to can be found in the description below of this video", and the description of the video says "No description available." :D

Why would you even want to do this, though? It just seems wrong. ;)

I agree but wonder how they did it, looks spooky 
  :P

---

### Post by vanlong441 on 2012-05-02
> **cecilpierce said:**
> Nice! How do you do that ?

> **forrestcupp said:**
> My favorite part of the video is where at the end it says "A how-to can be found in the description below of this video", and the description of the video says "No description available." :D

Why would you even want to do this, though? It just seems wrong. ;)

Just added the tutorial. I was in a hurry this morning. Sorry about that. Should any errors occur ( though I tested this carefully before writing the how-to), please post them here. Thank you for your interest :popcorn:

---

### Post by Version Dependency on 2012-05-02
> **cecilpierce said:**
> Nice! How do you do that ?


Just taking some guesses, but Unity2D panel (unity-2d-panel) and the Unity2D launcher (unity-2d-launcher) are separate programs and can be run in any DE you want.  Not sure but the HUD feature may be tied in to either the panel or the launcher.

---

### Post by vanlong441 on 2012-05-02
> **Version Dependency said:**
> Just taking some guesses, but Unity2D panel (unity-2d-panel) and the Unity2D launcher (unity-2d-launcher) are separate programs and can be run in any DE you want.  Not sure but the HUD feature may be tied in to either the panel or the launcher.

I can guarantee you HUD and Unity Dash will be working in this case. Without them, there is no point of making up all these things, right :popcorn:

---

### Post by vanlong441 on 2012-05-03
add how-to of Cinnamon

---

### Post by vanlong441 on 2012-05-03
updated new video and a screenshot

---

### Post by vanlong441 on 2012-05-04
added advice in *Important

---

### Post by zombifier25 on 2012-05-04
Nice tutorial, considering the fact that I like both Shell and Unity.
But I won't use it though, not until GNOME Shell is ported to Compiz :P

---

### Post by ojdon on 2012-05-04
> **zombifier25 said:**
> 
But I won't use it though, not until GNOME Shell is ported to Compiz :P

OH GOD **NO**! Imagine all the whining about how unstable Gnome-Shell is with their graphics card if that ever happened. Unity 3D is/was far more unstable compared to Unity 2D on a lot of people's machines because of Compiz's stability issues.

---

### Post by vanlong441 on 2012-05-04
added my Unity2D customization.

> **zombifier25 said:**
> Nice tutorial, considering the fact that I like both Shell and Unity.
But I won't use it though, not until GNOME Shell is ported to Compiz :razz:

Thank you. I believe some of the functions of Compiz will be seen in GNOME Shell in no time. However, Compiz even when ported to GNOME Shell may not be what I want for my low-end system.

> **ojdon said:**
> OH GOD **NO**! Imagine all the whining about  how unstable Gnome-Shell is with their graphics card if that ever  happened. Unity 3D is/was far more unstable compared to Unity 2D on a  lot of people's machines because of Compiz's stability issues.

Stability is always the first priority but desktop effects and makeups matter, too. I just hope that Compiz will get more stable and GNOME Shell will get wobbly windows some day.
:lolflag:

---

### Post by zombifier25 on 2012-05-04
> **ojdon said:**
> OH GOD **NO**! Imagine all the whining about how unstable Gnome-Shell is with their graphics card if that ever happened. Unity 3D is/was far more unstable compared to Unity 2D on a lot of people's machines because of Compiz's stability issues.

You must be referring to the Compiz in 11.10.

---

### Post by vanlong441 on 2012-05-06
added Cinnamon + Unity2D video

---

### Post by philinux on 2012-05-06
Moved to Desktop Environments.

---

### Post by pieterio on 2012-07-12
i can't get the dfconf thing to work, the editor doesn't work, actually, nothing seems to work (that is, it seems this thread is out of date...

but i LOVED the idea: i myself would want to have the cinnamon desktop whereas my wife would like the unity launcher...so why not have both?! :)

anyways...i hope anyone will actually react....


thx heaps...

Pieterio

edit: when trying in the cinnamon desktop environment to run command: unity-2d-shell i get the launcher to the left, it even works but the terminal seems to have trouble:
pieter@pieter-Aspire-7250:~$ unity-2d-shell
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/app-install/desktop/chromium-browser:chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/app-install/desktop/chromium-browser:chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.

so far nothing good i think...

---

### Post by icio85 on 2012-10-29
I've found this
[https://extensions.gnome.org/extension/393/distraction-free/](https://extensions.gnome.org/extension/393/distraction-free/)
that show panel and message tray only in overla mode. The problem is that disable also the hot corner! Is anybody out there who know how to edit it and enable the corners?

---

### Post by cmcanulty on 2012-10-30
Can you post a way to get the launcher and dash to show in classic 12.04?
Also I can't find your tutorial could you post a link? Thanks

---

### Post by vanlong441 on 2012-10-30
> **cmcanulty said:**
> Can you post a way to get the launcher and dash to show in classic 12.04?
Also I can't find your tutorial could you post a link? Thanks

In GNOME Classic session

```
unity-2d-shell --replace
```You may want to add the command to startup :)

> **icio85 said:**
> I've found this
[https://extensions.gnome.org/extension/393/distraction-free/](https://extensions.gnome.org/extension/393/distraction-free/)
that show panel and message tray only in overla mode. The problem is  that disable also the hot corner! Is anybody out there who know how to  edit it and enable the corners?

That extension is very interesting :) just one missing corner is a fair trade I think

---

### Post by cmcanulty on 2012-10-31
I get this error. I do have Unity installed and am running 12.04 classic 64 bit.

```
cmcanulty@HPTech:~$ unity-shell-2d --replace
unity-shell-2d: command not found
cmcanulty@HPTech:~$ 

```

---

### Post by vanlong441 on 2012-11-01
My sincere apology. I have corrected the command in the previous post :)

---

### Post by cmcanulty on 2012-11-01
Great I got it up and running , is there a way to autohide it as I tried right click and nothing happened. I really want dash and not launcher but I can live with both if it autohides thanks!

---

### Post by vanlong441 on 2012-11-01
> **cmcanulty said:**
> Great I got it up and running , is there a way to autohide it as I tried right click and nothing happened. I really want dash and not launcher but I can live with both if it autohides thanks!
 
you can follow this guide here :) [http://forum.pinguyos.com/Thread-Gnome-Shell-suggestions-and-solutions?pid=17416#pid17416](http://forum.pinguyos.com/Thread-Gnome-Shell-suggestions-and-solutions?pid=17416#pid17416)

---

### Post by cmcanulty on 2012-11-12
I now have another bug. I am running classic and the launcher sort of autohides but when it hides it becomes an empty blank launcher and covers the edge of firefox or anything else. See screenshot and please how do I fix? I also tried removing launcher in synaptic and a restart and the empty launcher is still there I see the correct launcher if I mouse over left edge but can't have the big empty space there all the time.

---

### Post by vanlong441 on 2012-11-12
> **cmcanulty said:**
> I now have another bug. I am running classic and the launcher sort of autohides but when it hides it becomes an empty blank launcher and covers the edge of firefox or anything else. See screenshot and please how do I fix? I also tried removing launcher in synaptic and a restart and the empty launcher is still there I see the correct launcher if I mouse over left edge but can't have the big empty space there all the time.

+ Create a text file with the below content and save it as unity2d.sh

> #!/bin/sh

sleep 3 && unity-2d-shell

+ Open a terminal right where you save the file and

```
chmod +x unity2d.sh
```

Or just right click on the file >> Properties and make it executable if you're using Nautilus.

+ Open startup manager, delete the old command (the one with *unity-2d-shell*) and put in the path to the text file you've just created in the command box. That will delay unity-2d-shell 3 seconds and give time for compiz manager to start first.

---

### Post by cmcanulty on 2012-11-13
OK I did that will update after work right now there is no launcher at all
 still very buggy I have no launcher or dash at all now.I logged out and in and restarted.

---

### Post by ercherramon on 2012-11-13
woww. excellent info and work. thanks. :-)

---

### Post by vanlong441 on 2012-11-13
> **cmcanulty said:**
> OK I did that will update after work right now there is no launcher at all
 still very buggy I have no launcher or dash at all now.I logged out and in and restarted.

If 3s doesn't work, try 5s :) The problem is unity-2d-shell must start after compiz. After a while using unity, it gets fatter (with recently used files, and app suggestions) therefore it may take for than 3s to load all those stuff. I suggest you remove some lens that you don't use (work around with unity-2d packages in synaptic). However, it will be simpler to just log out and log back (provided you have the script running to delay unity).

> **ercherramon said:**
> woww. excellent info and work. thanks. :-)

Thanks :)

---

### Post by cmcanulty on 2012-11-13
I cannot get the launcher at all now, anything else to try? I did increase the delay to 5 and logged out and restarted.

---

### Post by vanlong441 on 2012-11-13
> **cmcanulty said:**
> I cannot get the launcher at all now, anything else to try? I did increase the delay to 5 and logged out and restarted.

That's strange. Doing the following should give you the launcher immediately, isn't it?

```
killall unity-2d-shell
unity-2d-shell
```

You may want to reinstall unity-2d-shell if the above doesn't work :) Otherwise, wait for the new spin of mine which includes openbox session and unity-2d-shell of course.

---

### Post by cmcanulty on 2012-11-14
I get a huge list of errors and no launcher

```
cmcanulty@HPTech:~$ killall unity-2d-shell
cmcanulty@HPTech:~$ unity-2d-shell
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/launcher/Launcher.qml:224:39: Expected token `}'
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/launcher/LauncherLoader.qml:67: TypeError: Result of expression 'launcherLoader.item' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+E" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/Shell.qml:312: TypeError: Result of expression 'launcherLoader.item' [null] is not an object.
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/Shell.qml:312: TypeError: Result of expression 'launcherLoader.item' [null] is not an object.

```

---

### Post by vanlong441 on 2012-11-14
My best bet is to reinstall unity-2d-shell. I don't know if you're looking for a distro spin, but for you are having trouble with unity2d within gnome classic, you may want to take a look at what I've got so far (and maybe try it out when it is released :) ). Give me a way to contact you if you want to be notified when this comes out.

[http://www.youtube.com/watch?v=FPr7Z5B3V8c](http://www.youtube.com/watch?v=FPr7Z5B3V8c)

---

### Post by cmcanulty on 2012-11-14
thanks that reinstall got it back.

---

### Post by cmcanulty on 2012-11-18
I guess the white bar when launcher disappears is a bug. It ran fine for a few days now issue is back so I will reinstall again.I can't put that function on our 10 library machines until it is less buggy.i spent a ton of time trying to get rid of the workplace switcher and now I guess I have to go through that again. It is really irritating that they have decided to not make that a right cl remove item. I don't like being force fed using something I don't need.

---

