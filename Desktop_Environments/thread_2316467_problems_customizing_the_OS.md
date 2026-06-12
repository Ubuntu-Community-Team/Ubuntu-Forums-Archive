---
title: "problems customizing the OS"
date: 2016-03-08
forum: Desktop Environments
---

### Post by noam4 on 2016-03-08
Hi

Installed kubunu 15.10 on Dell XPS 13 2015 9343 a few days ago. I am having problems with setting up desktop effects. I am trying to set up wobbly windows but this option doesn't appear in desktop effect's settings. Tried to install compiz config with it's extras, but no matter what settings I set on it, it appears that requested effect (or any other effect) doesn't take place.

Another problem I encountered is that I am unable to change the login screen's background via system settings. I have seen [this instructions]("http://askubuntu.com/questions/154430/kubuntu-12-04-change-login-screen-background") but it didn't help.

Thanks in advance
Noam

---

### Post by deadflowr on 2016-03-08
Kubuntu 15.10 uses a completely re-designed desktop than that used previously.
So functions such as wobbly windows are probably gone, for now at least.
(I only tried the new desktop during a beta period[some time around 14.10 or 15.04], but noticed a few things not around; didn't look for wobbly windows, though, as that on Kubuntu was some what glitchy for me. Things change, so maybe it is somewhere now...)

Also, installing compiz will have no affect as Kubuntu uses the kwin desktop manager.

If you want to run compiz you will need to run the compiz --replace command.
in a terminal run:
```
 compiz --replace
```
I have no idea what how it will work with the new desktop.
It used to work great, but like I said, have not used Kubuntu enough with the new desktop.

---

### Post by Frogs Hair on 2016-03-08
Kwin in 15.10 is now kwin-decoration-oxyegen . Not sure what effects are included though.

---

### Post by noam4 on 2016-03-08
When I tried this version (15.10) via live cd there was an option of wobbly windows option, but after installation there isn't. Tried this "compiz --replace" command but didn't help. What is the opposite command?
Also, what about the login background?[COLOR=#000000][/COLOR]

---

### Post by Frogs Hair on 2016-03-08
Try the following. ```
kwin --replace
```[COLOR=#222426][FONT=Helvetica Neue] or [/FONT][/COLOR]```
DISPLAY=:0 kwin --replace
```

---

### Post by montag dp on 2016-03-11
I am on plasmashell 5.5.5 and the Wobbly Windows effect is available (not that I normally use it).  I tried enabling it and the following appeared in ~/.config/kwinrc under [Plugins]:

```
wobblywindowsEnabled=true
```

So you might try putting that in kwinrc and see if it has an effect.  You might have to log out and do it from a console login for it to work (though it might not anyway, but it's worth a try).

---

### Post by Rog131 on 2016-03-12
> **noam4 said:**
> Hi

Installed kubunu 15.10 on Dell XPS 13 2015 9343 a few days ago. I am having problems with setting up desktop effects. I am trying to set up wobbly windows but this option doesn't appear in desktop effect's settings. Tried to install compiz config with it's extras, but no matter what settings I set on it, it appears that requested effect (or any other effect) doesn't take place.

Another problem I encountered is that I am unable to change the login screen's background via system settings. I have seen [this instructions]("http://askubuntu.com/questions/154430/kubuntu-12-04-change-login-screen-background") but it didn't help.

Thanks in advance
Noam

**KDE desktop effects**

Some of the KDE desktop effects need the OpenGL compositing: KDE System Settings > Display and Monitor > Compositor > Rendering backend. 

At here - with the XRender - no wobbly windows. With the OpenGL, wobblies are available.

The KWin support information command will show the compositing/effects/etc information - terminal:
```
qdbus org.kde.KWin /KWin supportInformation
```


**Login screen background**

What display manager are you using ?
The default KDE dm is the SDDM: [https://en.wikipedia.org/wiki/Simple_Desktop_Display_Manager](https://en.wikipedia.org/wiki/Simple_Desktop_Display_Manager)
From the Kubuntu forums: [https://www.kubuntuforums.net/showthread.php?67599-Plasma-5-background-images](https://www.kubuntuforums.net/showthread.php?67599-Plasma-5-background-images)

---

