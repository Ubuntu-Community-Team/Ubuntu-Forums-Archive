---
title: "Animated Unity Starter"
date: 2013-02-02
forum: Desktop Environments
---

### Post by gnuser12 on 2013-02-02
Hello Users,
I've created a bookmark for  unity as *.desktop file
... added that file to the Unity Sidebar.
Is it possible to animate the icon ? (Color or Text)
I would change the background color of the bookmark icon.
One Host in the LAN is sometimes available and then it should have a special background color or maybe a text in the foreground.

Gnuser12
Hand (Have a nice day)

---

### Post by greg finnegan on 2013-02-02
Do you mean like change the icon??

---

### Post by Frogs Hair on 2013-02-02
The back-lighting is a chameleon effect that follows the icon color and can be turned on or off in the CCSM, UBuntu Tweak, or like applications. Creating a custom icon is possible also. I don't know about an animated .gif though

---

### Post by gnuser12 on 2013-02-04
Hi,
I explain it a bit more.
I have created a own Icon for unity with a quicklist 
What is a quicklist?
here more Details -> [http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07](http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07)

Here is the code of my quicklist

```

[Desktop Entry]
Encoding=UTF-8
Name=TVon
Comment=switch tv on
Exec=wakeonlan tv
Icon=/usr/share/app-install/icons/minitube.png
Categories=Application
Version=1.0
Type=Application
Terminal=0

Name[en_DK]=minitube.desktop

X-Ayatana-Desktop-Shortcuts=Remote;TVGuide

[Remote Shortcut Group]
Name=Remote
Exec=xdg-open http://vdr.let:6001/remote.html
TargetEnvironment=Unity

[TVGuide Shortcut Group]
Name=TVGuide
Exec=xdg-open http://vdr.let:6001
TargetEnvironment=Unity

...


```it works fine for me 
If I click on the icon the tv starts , 
with the right mouse button 
I can read quickly the tvguide, or use the remote 
But ... one wish is in my head ;) the Icon should display whether the tv is on or off 
some guesses
tv is on
- icon background is green
or maybe a text "on"
tv is off
- icon background is red
or maybe a text "off"

It should be possible to show something on the icon
for example thunderbird shows a number on the icon if a new mail has been arrived 

So I hope it helped 
Gunuser12

---

### Post by Frogs Hair on 2013-02-04
I know that to make an animation like you described can require two or more images but I don't know how make the animation work like a battery or mail notify icon works.

---

