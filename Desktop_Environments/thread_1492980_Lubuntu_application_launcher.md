---
title: "Lubuntu application launcher"
date: 2010-05-25
forum: Desktop Environments
---

### Post by viralmeme on 2010-05-25
How do I edit a panel item to add a parameter string to launching Chrome. I can't seem to locate it ?

From: /usr/lib/chromium-browser/chromium-browser

To: /usr/lib/chromium-browser/chromium-browser --enable-plugins %U

---

### Post by tom4everitt on 2010-05-25
I haven't tried Lubuntu, but are you sure it is not as easy as right-clicking on the applet and choose Properties, or similar? I see no reason why it shouldn't be that simple :)

---

### Post by kerry_s on 2010-05-25
plugins are already enabled.

but to answer your question it's /etc/chromium-browser/default
just in case you need to ad proxy or something.

---

### Post by SlidingHorn on 2010-05-25
> **kerry_s said:**
> plugins are already enabled.

but to answer your question it's /etc/chromium-browser/default
just in case you need to ad proxy or something.

I'm not sure if it's the same in lubuntu as the rest, but couldn't they also just use the command 'chromium-browser' just as well?

---

### Post by viralmeme on 2010-05-26
> **SlidingHorn said:**
> I'm not sure if it's the same in lubuntu as the rest, but couldn't they also just use the command 'chromium-browser' just as well?
Thanks for all the responces ..

---

### Post by MooPi on 2010-05-26
The applet may be located in ```
/usr/share/applications
```These are .desktop files that can be edited simply with gedit/leafpad/nano/    etc.....
Not certain on this location but I have used this in conjunction with lxpanel.

---

### Post by viralmeme on 2010-05-26
> **tom4everitt said:**
> I haven't tried Lubuntu, but are you sure it is not as easy as right-clicking on the applet and choose Properties, or similar? I see no reason why it shouldn't be that simple :)
Right-click don't seem to be working. For instance right click on the clock doesn't bring up an adjust option.

---

### Post by kerry_s on 2010-05-26
> 
I'm not sure if it's the same in lubuntu as the rest, but couldn't they also just use the command 'chromium-browser' just as well?


it's the same i started with lubuntu.

> Right-click don't seem to be working. For instance right click on the clock doesn't bring up an adjust option.

some applets on lxpanel you have to edit from the main gui, i think you can right click anywhere on the panel to bring that up. don't remember the wording as i only used lxpanel a short time, it was to limited for me, so i switched to xfce4-panel.

---

### Post by wirah on 2010-11-18
Firstly thank you for your help and suggestions.

I too am a lubuntu user (on my netbook, at least) and have the same difficulty.

For all its merits, adding a panel launcher is **ridiculously** difficult. Such that I too have not yet figured out how to do it.

The interface is called LXDE, and I will be focussing my endless google searches on this as a keyword. When I determine how to add a launcher (I realise in Gnome that it is as easy as right clicking and adding a panel item/custom application launcher) - I will document the method here.

I suppose that what I want to highlight is that it is unnecessarily unintuitive in Lubuntu, and I will raise this with the authors of LXDE.

Lastly, loose ends aside, I am extremely impressed with the speed of lubuntu, and would like to commend the authors for their success in achieving, even exceeding their primary objective.

---

### Post by cavalier911 on 2010-11-19
Edit the existing chromium launcher on the application launch bar and menu/Internet/Chromium Web Browser 

```
sudo nano /usr/share/applications/chromium-browser.desktop 
```

Change:
```
Exec=chromium-browser %U
```
To:
```
Exec=chromium-browser --enable-plugins %U
```

---

### Post by wirah on 2010-11-19
Hi There,

That is one way to do it, but editing existing launchers is not ideal.

Here is how I added a new 'custom' launcher to the panel:

Firstly, create a desktop item with lxshortcut, you can put it wherever you like, but /usr/share/applications is a good place.

```

lxshortcut -o myshortcutname.desktop

```

Next, right click your new .desktop file and edit its properties to your liking.

Then, you can add it to your panel. Open up
```

~/.config/lxpanel/Lubuntu/panels/panel

```

in Leafpad. Find the stanza which begins:

```


Plugin {
    type = launchbar
    Config {
       ....

```

and edit it so that you are adding a new 'Button' element. The 'id' parameter should contain either the full path to your application's .desktop file, or if it is in /usr/share/applications/, it should contain only the filename (i.e. no path).

My finished panel looks something like this:

```

Plugin {
    type = launchbar
    Config {
        Button {
            id=pcmanfm.desktop
        }
        Button {
            id=chromium-browser.desktop
        }
        Button {
            id=/home/ant/Launcher/idea.desktop
        }
    }
    ...
}

```

Now save and close the file, and log in/out of Lubuntu.

I read somewhere that you could drag and drop .desktop files straight to a panel's launchbar. I haven't experienced this, but you are welcome to try.

---

