---
title: "I can't change the size of the Launch bar"
date: 2014-01-13
forum: Desktop Environments
---

### Post by viriatovigo on 2014-01-13
I did come back to Ubuntu 12.04 after awhile and I did install it in a new machine (Shuttle X50V3).
 

 It is installed from the CD that I've bought from Canonical few weeks ago. Have been installed all the updates.
 

 I can't change the size of the Launch bar because in "Appearance" doesn't show up the sliding rule to change the size as used to be before, so I have not a clue how to do it now.  
 

 Please, advice. Thank you.

---

### Post by ajgreeny on 2014-01-13
There is a long discussion of this in the thread at [http://ubuntuforums.org/showthread.php?t=1973684](http://ubuntuforums.org/showthread.php?t=1973684)

Good Luck!

---

### Post by viriatovigo on 2014-01-13
Ta [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")

I could see in all the answers that no one works.

What I don't understand is why Ubuntu took away the Laucher Icon Size slide facility... It seems to me that Linux is starting to  do the same than Microsoft: Every time they take away more goodies in the new versions.

I'll keep trying in the spare time.

---

### Post by howefield on 2014-01-13
If you are running Unity 2D and aren't afraid of editing a few files, there is a workaround.

[http://ubuntuforums.org/showthread.php?t=1943423](http://ubuntuforums.org/showthread.php?t=1943423)

---

### Post by viriatovigo on 2014-01-13
Ta [ 						 					]("http://ubuntuforums.org/member.php?u=186490") 				 				 					 						 	[**[COLOR=#C61919][B]howefield**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490")

I don't know what is Unity 2D.

According to your link I need to do a hell or scripts. Again: "What I don't understand is why Ubuntu took away the Laucher Icon Size slide facility..." 

What is trying to do Linux? Promoting masochism? There is a kind of "terminal" drug addiction?

---

### Post by howefield on 2014-01-13
If you open a terminal and type the following..

```
echo $DESKTOP_SESSION
```

If the output of that is ubuntu-2d, then you are using Unity 2D. You cannot change the icon size other than by editing those files, as far as I know.

As for "What I don't understand is why Ubuntu took away the Laucher Icon Size slide facility..." well, they never took it away because it was never an option in Unity 2D, you couldn't change the icon size by using the slider.

Let us know the output of the above command.

---

### Post by viriatovigo on 2014-01-13
Ta howefield

   	 	 	 	   **[COLOR=#000000]"well, they never took it away because it was never” - Yes it was:[/COLOR]**
 

 **[COLOR=#000000]May 5th, 2012[/COLOR]**
 

 **[[COLOR=#000000]BigSilly[/COLOR]]("http://ubuntuforums.org/member.php?u=297219")**

 [INDENT]System Settings/Apperance/Launcher Icon Size. At the bottom.  :wink:


[/INDENT] 

 And it was because I have it in my previous Ubuntu 12.04 one year ago.
 

 Well, OK, it is, now what? How to open that thing and how to use it?
 

 constante@constante-X50V3:~$ echo $DESKTOP_SESSION 
 ubuntu-2d

---

### Post by viriatovigo on 2014-01-13
Hi howefield

You can see in this thread how it was the Launch Size Icon and where it was:

  	 	 	 	   [http://askubuntu.com/questions/29553/how-can-i-configure-unity/101415#101415](http://askubuntu.com/questions/29553/how-can-i-configure-unity/101415#101415)

---

### Post by howefield on 2014-01-13
> **viriatovigo said:**
> "well, they never took it away because it was never” - Yes it was:

At the risk of sounding like the panto villain.. oh no it wasn't. :)

Unity (3D) had and has the slider control to change the iocon size, but Unity 2D which you have kindly shown to be running, doesn't. Period. 

> And it was because I have it in my previous Ubuntu 12.04 one year ago.

Then you were running Unity a year ago, and not Unity 2D.

Is this the same machine as you were running a year ago, if so, try clicking on the cog wheel at the login screen and select Ubuntu ?

---

### Post by viriatovigo on 2014-01-13
Ta howefield

Nop! It is a new machine that I've bought 6 months ago, Before was a LenovoThinkcentre and now is a Shuttle X50V3. I took rid of the Lenovo.

In this one, clicking o the cog wheel, there is not such a thing as "Ubuntu", only "System Settings", "Displays", "Startup applications", "Software Update", "Attached Devices", "Printers", "Lock Screen", "Log out", "Suspend" and "Shut down".

---

### Post by deadflowr on 2014-01-13
> **viriatovigo said:**
> Ta howefield

Nop! It is a new machine that I've bought 6 months ago, Before was a LenovoThinkcentre and now is a Shuttle X50V3. I took rid of the Lenovo.

In this one, clicking o the cog wheel, there is not such a thing as "Ubuntu", only "System Settings", "Displays", "Startup applications", "Software Update", "Attached Devices", "Printers", "Lock Screen", "Log out", "Suspend" and "Shut down".

howefield means click the cog in the login screen.
It's the icon the box where you enter your username and password when you login.

but, to help try to resolve the issue of trying to get Unity to work rather than Unity-2d, post the outputs for
```
lspci | grep VGA
```
and possibly
```
/usr/lib/nux/unity_support_test -p
```

The first should give us the graphics card
the second whether the current graphics card is currently supported for the advanced 3d environment of unity.

It's quite possible that a better driver can be used.

---

### Post by viriatovigo on 2014-01-13
Hi deadflower

Sorry, but I don't need to put my name and password to login... I just click in "Loging with SSO", or someting like that, and do click in "Yes, Log me in".

I suppose that you mean when  login in the Forum because when I do star Ubuntu opens automtically, I don't need to login and the screen is set not to go off and no password required.

By the way, I have open all my PCs 24 hours for business reasons and to perform remote control with my laptop, so I am working with the desktops werever I go.

So I don't know which cog do you mean... The solo one that I see all the time is the one in the top right corner, next to my name.

---

### Post by ajgreeny on 2014-01-13
You are using autologin so to change your session type you will have to logout, then login again from the login screen which will appear automatically.

That login screen will have a box for your password, and just above and to right of that box is a small settings icon, looking a bit like a flower.  Click on that and you should see a variety of login sessions available to you.  It is there that you need to choose "Ubuntu".

---

### Post by deadflowr on 2014-01-13
^^^^Exactly, as ajgreeny stated.

I wasn't referencing the forums login, and what would make you think I was.;)
What I stated makes no sense as far the forums login goes...

Simply logging out of the  desktop session and then see if changing the desktop with the earlier mentioned method works, or changes the desktop from unity-2d to normal unity.
Logout is in the cog on the top panel.

---

### Post by viriatovigo on 2014-01-13
Ta ajgreeny and deadflower

I am waiting for a Skype call to do an interpretation on the MacBook Pro for my Interpreters Agency and,when I do finish, I'll do what you said.

I'll be back to you with the results.

---

### Post by viriatovigo on 2014-01-14
Hi ajgreeny and deadflower.

Sorry, was a very long night and I was sleeping most of the day today.

Right...

After Log out I did Log in again and In the cog did show &#8220;Ubuntu&#8221; and &#8220;Ubuntu d&#8221;. I did click on Ubuntu and nothing did happen (Was supposed to happen something?). Still it doesn't show the slide bar in &#8220;Appearance&#8221;. Then I did log in and still it doesn't show the slide bar in &#8220;Appearance&#8221;, so I went to input in the terminal the 2 scripts that you gave me. The results were...:
 

 constante@constante-X50V3:~$ lspci | grep VGA  
 00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 0b)  
 constante@constante-X50V3:~$  
 

 
 constante@constante-X50V3:~$ /usr/lib/nux/unity_support_test -p  
 OpenGL vendor string:   VMware, Inc.  
 OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)  
 OpenGL version string:  2.1 Mesa 8.0.4  
 Not software rendered:    no  
 Not blacklisted:          yes  
 GLX fbconfig:             yes  
 GLX texture from pixmap:  yes  
 GL npot or rect textures: yes  
 GL vertex program:        yes  
 GL fragment program:      yes  
 GL vertex buffer object:  yes  
 GL framebuffer object:    yes  
 GL version is 1.4+:       yes  
 Unity 3D supported:       no  
 constante@constante-X50V3:~$  


What nexr?

---

### Post by deadflowr on 2014-01-14
> [COLOR=#000000]OpenGL vendor string: VMware, Inc. [/COLOR]

I wonder how much this has to do with the issue.
Normally the vendor should be simply Intel.
Maybe vmware has an additional component to add the needed hardware rendering support.

---

### Post by viriatovigo on 2014-01-14
Ta deadflowr.

And that means...?

---

### Post by howefield on 2014-01-14
> **viriatovigo said:**
> And that means...?

That you are back to post number [4]("http://ubuntuforums.org/showthread.php?t=2199290&p=12899102&viewfull=1#post12899102").

---

### Post by viriatovigo on 2014-01-14
Ta homwfield.

I understand that is your post with the link to the post of bonzini.

OK, I'll do it. I have not a clue about what says bonzini but I'll copy and paste the scripts in the terminal and see what's happens.

Thank you.

---

### Post by viriatovigo on 2014-01-14
Hi homefield

                        I did manage to understand what bonzini said and I went to the file called "Shell.qml&#8221;.
 

 I did click to open it and...:
 

 

 Could not display "/usr/share/unity-2d/shell/Shell.qml".
 

 There is no application installed for Qt Markup Language file files. 
 Do you want to search for an application to open this file?
 

 

 Great... Will I manage to change the size of the icons in the Launch bar before next Xmas? Everything in Mac is just a click away and is faster, easier and more accurate 100% than Windows, that's why I am doing business with Mac Maverick. In Linux all seems to take ages and be a geek about Linux, not for "John People".
 

 What next?

---

### Post by ajgreeny on 2014-01-14
You can open **Shell.qml** or other **.qml** files in a text editor, eg gedit.

If you need to edit the file, (and I do not use unity so, do not need to know about launchbars, use command gksudo gedit /usr/share/unity-2d/shell/Shell.qml and you can change it as needed.

---

### Post by viriatovigo on 2014-01-14
Thank you ajgreeny

I've got the followinf result. I am not skilled at all in Linux, so it is difficult for me to identify the html scripts.

Where is supposed to change the size within the script?

I do apologize for being so thick.

---

### Post by viriatovigo on 2014-01-14
Sorry ajgreeny, I've forgotten to enclose the sript. Here it is:

```
/*
 * This file is part of unity-2d
 *
 * Copyright 2012 Canonical Ltd.
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; version 3.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

import QtQuick 1.1
import Unity2d 1.0
import "launcher"
import "common/utils.js" as Utils

Item {
    id: shell

    property variant declarativeView
    property variant dashLoader
    property variant hudLoader
    property bool launcherAlwaysVisible: launcherLoader.loadLauncher && !launcherLoader.launcherInHideMode

    Binding {
        target: declarativeView
        property: "accessibleName"
        value: {
            if (shellManager.hudActive) {
                return "Hud";
            }
            if (shellManager.dashActive) {
                return "Dash";
            }
            return "Launcher";
        }
    }

    /* Space reserved by strutManager is taken off screen.availableGeometry but
       we want the shell to take all the available space, including the one we
       reserved ourselves via strutManager. */
    height: declarativeView.screen.availableGeometry.height
    // We need the min because X is async thus it can happen that even if strutManager.enabled is true
    // declarativeView.screen.availableGeometry.width still has not been updated and thus the sum might be bigger than declarativeView.screen.geometry.width.
    // The real nice and proper solution would be strutManager having a hasTheChangeBeenApplied property
    width: Math.min(declarativeView.screen.geometry.width, declarativeView.screen.availableGeometry.width + (strutManager.enabled ? strutManager.width : 0))

    Accessible.name: "shell"

    WallpaperColor {
    }

    GestureHandler {
        id: gestureHandler
        dashManager: shellManager
    }

    onDashLoaderChanged: {
        if (shellManager.dashActive) {
            if (dashLoader == undefined)
            {
                launcherLoader.visibilityController.endForceVisible("dash")
            } else {
                launcherLoader.visibilityController.beginForceVisible("dash")
            }
        }
    }

    onHudLoaderChanged: {
        if (shellManager.hudActive && launcher2dConfiguration.hideMode != 0) {
            if (hudLoader == undefined)
            {
                launcherLoader.visibilityController.endForceHidden("hud")
            } else {
                launcherLoader.visibilityController.beginForceHidden("hud")
            }
        }
    }

    LauncherLoader {
        id: launcherLoader
        anchors.top: parent.top
        anchors.bottom: parent.bottom
        width: 65

        /* Launcher visibility handling and 4 fingers dragging reveal */
        property int hiddenX: Utils.isLeftToRight() ? -width : shell.width
        property int shownX: Utils.isLeftToRight() ? 0 : shell.width - width
        x: {
            var value
            var delta = Utils.isLeftToRight() ? gestureHandler.dragDelta : -gestureHandler.dragDelta

            if (visibilityController.shown) {
                value = shownX
            } else {
                /* FIXME: it would be better to have gestureHandler disabled
                   for dragging when hideMode is set to 0 */
                if (launcher2dConfiguration.hideMode != 0 && gestureHandler.isDragging) {
                    value = hiddenX + delta
                } else {
                    value = hiddenX
                }
            }

            if (hiddenX <= shownX) {
                return Utils.clamp(value, hiddenX, shownX)
            } else {
                return Utils.clamp(value, shownX, hiddenX)
            }
        }

        Binding {
            target: launcherLoader.item
            property: "showMenus"
            value: (dashLoader == undefined || !dashLoader.item.active) && (hudLoader == undefined || !hudLoader.item.active)
        }

        Behavior on x { NumberAnimation { id: launcherLoaderXAnimation; duration: 125 } }

        SpreadMonitor {
            id: spread
            onShownChanged: if (shown) {
                                /* The the spread grabs input and Qt can't properly
                                   detect we've lost input, so explicitly hide the menus */
                                launcherLoader.item.hideMenu()
                                launcherLoader.visibilityController.beginForceVisible("spread")
                            }
                            else launcherLoader.visibilityController.endForceVisible("spread")
        }
    }

    Connections {
        target: shellManager

        onDashActiveChanged: {
            if (shellManager.dashActive) {
                if (hudLoader != undefined && hudLoader.item.active) {
                    hudLoader.item.active = false
                }
                if (dashLoader != undefined) {
                    launcherLoader.visibilityController.beginForceVisible("dash")
                }
            } else {
                if (dashLoader != undefined) {
                    launcherLoader.visibilityController.endForceVisible("dash")
                    if (dashLoader.status == Loader.Ready) dashLoader.item.deactivateAllLenses()
                }
            }
        }

        onHudActiveChanged: {
            if (shellManager.hudActive) {
                if (dashLoader != undefined && dashLoader.item.active) {
                    dashLoader.item.active = false
                }
                if (hudLoader != undefined && launcher2dConfiguration.hideMode != 0) {
                    launcherLoader.visibilityController.beginForceHidden("hud")
                }
            } else {
                if (hudLoader != undefined && launcher2dConfiguration.hideMode != 0) {
                    launcherLoader.visibilityController.endForceHidden("hud")
                }
            }
        }
    }

    Connections {
        target: declarativeView
        onLauncherFocusRequested: {
            launcherLoader.focus = true
            launcherLoader.item.focusBFB()
        }
        onFocusChanged: {
            if (!declarativeView.focus && hudLoader!= undefined && hudLoader.item.active) hudLoader.item.active = false

            /* FIXME: The launcher is forceVisible while it has activeFocus. However even though
               the documentation says that setting focus=false will make an item lose activeFocus
               if it has it, this doesn't happen with FocusScopes (and Launcher is a FocusScope).
               Therefore I'm working around this by giving focus to the shell, which is safe since
               the shell doesn't react to activeFocus at all.
               See: [https://bugreports.qt.nokia.com/browse/QTBUG-19688](https://bugreports.qt.nokia.com/browse/QTBUG-19688) */
            if (!declarativeView.focus && launcherLoader.activeFocus) shell.focus = true
        }
    }

    Component.onCompleted: {
        if (declarativeView.screen.screen == 0) {
            var loaderComponent = Qt.createComponent("DashLoader.qml");
            dashLoader = loaderComponent.createObject(shell, {});

            var loaderComponent = Qt.createComponent("HudLoader.qml");
            hudLoader = loaderComponent.createObject(shell, {});
        }
        declarativeView.show()
    }

    Keys.onPressed: {
        if (event.key == Qt.Key_Escape || (event.key == Qt.Key_F4 && event.modifiers == Qt.AltModifier )) {
            declarativeView.forceDeactivateWindow()
        }
    }

    InputShapeManager {
        target: declarativeView

        InputShapeRectangle {
            id: launcherInputShape
            enabled: launcherLoader.status == Loader.Ready
        }

        InputShapeRectangle {
            rectangle: {
                if (dashLoader != undefined) {
                    if (desktop.isCompositingManagerRunning) {
                        return Qt.rect(dashLoader.x, dashLoader.y, dashLoader.width, dashLoader.height)
                    } else {
                        return Qt.rect(dashLoader.x, dashLoader.y, dashLoader.width - 7, dashLoader.height - 9)
                    }
                } else {
                    return Qt.rect(0, 0, 0, 0)
                }
            }
            enabled: dashLoader != undefined && dashLoader.status == Loader.Ready && dashLoader.item.active
            mirrorHorizontally: Utils.isRightToLeft()

            InputShapeMask {
                id: shape1
                source: "shell/common/artwork/desktop_dash_background_no_transparency.png"
                color: "red"
                position: dashLoader != undefined ? Qt.point(dashLoader.width - 50, dashLoader.height - 49) : Qt.point(0, 0)
                enabled: shellManager.dashMode == ShellManager.DesktopMode
            }
        }

        InputShapeRectangle {
            id: hudInputShape
            enabled: hudLoader != undefined && hudLoader.status == Loader.Ready && hudLoader.item.active

            InputShapeMask {
                source: "shell/common/artwork/desktop_dash_background_no_transparency.png"
                color: "red"
                position: hudLoader != undefined ? Qt.point(hudLoader.width - 50, hudLoader.height - 49) : Qt.point(0, 0)
            }
        }
    }

    Binding {
        target: launcherInputShape
        property: "rectangle"
        value: Qt.rect(launcherLoader.x,
                       launcherLoader.y,
                       launcherLoader.width,
                       launcherLoader.height)
        when: !launcherLoaderXAnimation.running
    }

    Binding {
        target: hudInputShape
        property: "rectangle"
        value: {
            if (hudLoader != undefined) {
                if (desktop.isCompositingManagerRunning) {
                    return Qt.rect(hudLoader.x, hudLoader.y, hudLoader.width, hudLoader.height)
                } else {
                    return Qt.rect(hudLoader.x, hudLoader.y, hudLoader.width - 7, hudLoader.height - 9)
                }
            } else {
                return Qt.rect(0, 0, 0, 0)
            }
        }
        when: hudLoader != undefined && !hudLoader.animating
    }

    StrutManager {
        id: strutManager
        edge: Unity2dPanel.LeftEdge
        widget: declarativeView
        height: launcherLoader.height
        width: launcherLoader.width
        enabled: launcherAlwaysVisible
    }

    PointerBarrier {
        property int x: declarativeView.globalPosition.x + (Utils.isLeftToRight() ? 0 : shell.width)
        property bool enableTrigger: launcherLoader.launcherInHideMode && launcherLoader.loadLauncher
        // This enableSticky logic has a 'bug' int RTL where the right most screen will still have enableSticky
        // set to true, but it won't cause any issue other than consuming a few bytes of mememory and calculating the 
        // rightmost x is probably more expensive and error prone than just enabling the extra barrier
        property bool enableSticky: unity2dConfiguration.stickyEdges && (declarativeView.screen.geometry.x > 0 || Utils.isRightToLeft())

        id: leftBarrier
        triggerDirection: Utils.isLeftToRight() ? PointerBarrier.TriggerFromRight : PointerBarrier.TriggerFromLeft
        triggerZoneEnabled: enableTrigger && !launcherLoader.visibilityController.shown
        triggerOnly: enableTrigger && !enableSticky
        p1: Qt.point(x, declarativeView.screen.geometry.y)
        p2: Qt.point(x, declarativeView.screen.geometry.y + declarativeView.screen.geometry.height)
        triggerZoneP1: Qt.point(x, launcher2dConfiguration.revealMode == 1 ? declarativeView.screen.geometry.y : declarativeView.globalPosition.y)
        triggerZoneP2: Qt.point(x, launcher2dConfiguration.revealMode == 1 ? declarativeView.screen.geometry.y + 1 : declarativeView.globalPosition.y + launcherLoader.height)
        threshold: (enableSticky || enableTrigger) ? launcher2dConfiguration.edgeStopVelocity : -1
        maxVelocityMultiplier: launcher2dConfiguration.edgeResponsiveness
        decayRate: launcher2dConfiguration.edgeDecayrate
        triggerPressure: launcher2dConfiguration.edgeRevealPressure
        breakPressure: launcher2dConfiguration.edgeOvercomePressure

        onTriggered: launcherLoader.item.barrierTriggered()
    }

    PointerBarrier {
        property bool enableSticky: unity2dConfiguration.stickyEdges && declarativeView.screen.geometry.y > 0

        id: topBarrier
        p1: Qt.point(declarativeView.screen.geometry.x, declarativeView.screen.geometry.y)
        p2: Qt.point(declarativeView.screen.geometry.x + declarativeView.screen.geometry.width, declarativeView.screen.geometry.y)
        threshold: enableSticky ? launcher2dConfiguration.edgeStopVelocity : -1
        maxVelocityMultiplier: launcher2dConfiguration.edgeResponsiveness
        decayRate: launcher2dConfiguration.edgeDecayrate
        breakPressure: launcher2dConfiguration.edgeOvercomePressure
    }
```

---

### Post by ajgreeny on 2014-01-15
CHANGING ICON SIZE IN UNITY 2D UBUNTU 12.04

First, all of the .qml files live in /usr/share/unity-2d/shell. You need to edit three files, as follows, though I believe some of the line numbers may have changed with updates to these files so you may need to search for the text strings I show.
Also this info is now pretty old, so just in case everything goes wrong, make sure you have backups of the files before you edit them and save new versions.

In that directory you will see a file called "Shell.qml". In it you will adjust the width of the launcher, by changing line 91(?), which looks like

Width: 65
to look like    
Width: 50

Then in the subdirectory "common", you will see a file called "IconTile.qml". In it you adjust the width and height of the main icon of the tile, by changing lines 71 and 72 (?), which look like

sourceSize.width: 48
sourceSize.height: 48

to look like

sourceSize.width: 32
sourceSize.height: 32

Finally, in the subdirectory "launcher", you will see a file called "LauncherList.qml". In it you will adjust the tile size by changing line 30 (?), which looks like

property int tileSize: 54    to look like    property int tileSize: 38

and also the selection outline size by changing line 34, which says

property int selectionOutlineSize: 65    to say    property int selectionOutlineSize: 50

Now you need to check, and possibly change, one last thing. In the same "launcher" directory, examine line 250 (?) in the file "LauncherItem.qml". If it looks like

width: 32

you are good to go. On the other hand, it may show a width of some other (larger?) number. If so, change it to 32, the same as the change shown above in IconTile.qml.

---

### Post by deadflowr on 2014-01-15
If you want something easy, I forgot about this little script
Try this
```
cd
wget http://webupd8.googlecode.com/files/script.py
chmod +x script.py
sudo ./script.py SIZE

```

From here
[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)

I had used this in the past and it works, and the settings stay set.

---

### Post by viriatovigo on 2014-01-16
Ta deadflowr

Sorry for the delay but it seems that the whole planet want translations with a pretty short deadline. It is the typical new year rush in companies with branches abroad.

After pasting the scripts in the template this was the result. Now what next?

constante@constante-X50V3:~$ cd
constante@constante-X50V3:~$ 
constante@constante-X50V3:~$ wget [http://webupd8.googlecode.com/files/script.py](http://webupd8.googlecode.com/files/script.py)
--2014-01-16 12:34:50--  [http://webupd8.googlecode.com/files/script.py](http://webupd8.googlecode.com/files/script.py)
Resolving webupd8.googlecode.com (webupd8.googlecode.com)... 74.125.132.82, 2a00:1450:400c:c06::52
Connecting to webupd8.googlecode.com (webupd8.googlecode.com)|74.125.132.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2143 (2.1K) [text/x-java]
Saving to: `script.py'

100%[======================================>] 2,143       --.-K/s   in 0.03s   

2014-01-16 12:34:51 (67.1 KB/s) - `script.py' saved [2143/2143]

constante@constante-X50V3:~$ chmod +x script.py
constante@constante-X50V3:~$ sudo ./script.py SIZE
[sudo] password for constante: 
Traceback (most recent call last):
  File "./script.py", line 43, in <module>
    icon_size = int(sys.argv[1])
ValueError: invalid literal for int() with base 10: 'SIZE'
constante@constante-X50V3:~$

---

### Post by viriatovigo on 2014-01-16
Hi ajgreeny

Yeap! The Launch bar did disappear and, thanks to your advice, I had to put back the backed up old script and the Launcher bar is on again but still I can't change the size.

---

### Post by howefield on 2014-01-16
> **viriatovigo said:**
> constante@constante-X50V3:~$ sudo ./script.py SIZE

Try running the script again, but this time replace the word SIZE with the icon size that you want, for example...

```
sudo ./script.py 32
```

---

### Post by mc4man on 2014-01-16
> The Unity 3D launcher icon size can easily be changed through System Settings (under Appearance), but that's not available for Unity 2D. But there is a way to change the Unity 2D launcher icon size: through a script.

To change the Unity 2D icon size, run the following commands in a terminal:

```
cd
wget http://webupd8.googlecode.com/files/script.py
chmod +x script.py
sudo ./script.py SIZE
```


In the last command above, **replace "SIZE" with the desired size for the launcher icons, for example "32" (don't use any quotes)**. Then log out and log back in to Unity 2D.

Maybe you've done too much reading lately so you didn't bother on the above, in that case possibly something stands out now?

---

### Post by viriatovigo on 2014-01-16
Hey!!!! Bingo!!!! Thank you very much mc4man, it did work!

What I can see is that I am too thick and I couldn't understand what were tellig me homefield, ajgreeny and deadflowr. Sorry, I really do apologize to everyone for wasting your time. And I take this opportunity to thank all of you for your patience with me and all your help.

All gthe best to every one.

Have a nice day.

Tino

---

