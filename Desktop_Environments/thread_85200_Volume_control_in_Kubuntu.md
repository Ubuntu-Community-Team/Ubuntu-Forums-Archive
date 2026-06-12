---
title: "Volume control in Kubuntu?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by the__collector on 2005-11-02
Hey there,

I've used linux for some time now. At the moment I'm a proud Kubuntu user. I've made the switch from Ubuntu to Kubuntu two weeks ago because somehow KDE is more appealing to me.

However I miss one function in Kubuntu that I loved in Ubuntu. The ability to change the volume level with the following key-combinations : Fn+LEFT and FN+RIGHT.

Is there a package I should install to enable this is this even possible in Kubuntu? I'd like to point out that the other 'function'-key-combinations ( backlight control of my laptop, en-/disabling touchpad, battery status etc. ) work perfectly.

I'm using Breezy on my Samsung M40 laptop.

Kind regards,

Luc

---

### Post by daller on 2005-11-08
Try to find "mmkeys"

Originally I found it on [www.printf.dk](www.printf.dk), but I can't seem to find it now...

Please post if you find IT, or a better alternative...

---

### Post by the__collector on 2005-11-09
[QUOTE=daller]Try to find "mmkeys"

Originally I found it on [www.printf.dk](www.printf.dk), but I can't seem to find it now...

Please post if you find IT, or a better alternative...[/QUOTE]


I found the better alternative:

I used hotkeys and this scheme:

```
<?xml version="1.0"?>
<definition>
        <config model="Samsung M40">
                <Play         keycode="124"/>
                
                <VolUp        keycode="176" adj="2"/>
                <VolDown      keycode="174" adj="2"/>
                <Mute         keycode="160"/>
                
                <WebBrowser   keycode="125"/>
                <Email        keycode="128"/>
        </config>
        <contributor>
                <name>to be added</name>
                <email>to be added</email>
        </contributor>
</definition>
```

---

### Post by BOBuntu on 2005-11-09
I had the same problem...I solve it  using hotkeys too.
But the problem is if Gnome recognises the volume Fn keys, why KDE doesn't?
Anyone solved it?

---

### Post by asimon on 2005-11-09
You can configure the keys for Kmix, but it's very good hidden:

1. Start Kmix, there should appear a loudspeaker icon in the system tray
2. Right-click on the icon and choose "Show Mixer Window"
3. In the Kmix window right-click on the "Master" Volume slider and chooe "Configure Shortcuts"
4. Assign keys as you want

---

### Post by daller on 2005-11-11
[QUOTE=asimon]You can configure the keys for Kmix, but it's very good hidden:

1. Start Kmix, there should appear a loudspeaker icon in the system tray
2. Right-click on the icon and choose "Show Mixer Window"
3. In the Kmix window right-click on the "Master" Volume slider and chooe "Configure Shortcuts"
4. Assign keys as you want[/QUOTE]

The only thing that happens, when I click on the hotkey, is that the dashed rectangle disapears (inside the button)

---

