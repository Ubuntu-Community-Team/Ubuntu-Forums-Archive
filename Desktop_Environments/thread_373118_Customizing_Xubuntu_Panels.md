---
title: "Customizing Xubuntu Panels?"
date: 2007-02-28
forum: Desktop Environments
---

### Post by lavinog on 2007-02-28
Is there a way to change the colors, change transparency, or use a background image on the panels in xfce like i could with gnome desktop?

Also can gnome panel items be used in xfce and vice versa?

---

### Post by john.nicholls on 2007-03-01
I think the answer to all three questions is no, but you'll find the definitive answers if you search the archives at the xfce.org discussion list, where these questions have frequently come up.

---

### Post by kerry_s on 2007-03-01
Yes

```
 there a way to change the colors,
```

You can tweak the gtk2.0 theme

```
change transparency,
```

Are you running the latest xfce4.4.0? You can turn compiz on, for 4.4.0.->
Press> alt+F2
type

gksu mousepad /etc/apt/sources.list

add this to the bottom->

deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0

close and save

press> alt+F2
type

gksu synaptic

click on> reload
then> mark all upgrades
then> apply

press> alt+F2
type

gksu mousepad /etc/X11/xorg.conf

add this to the bottom->

```
Section "Extensions"
    Option         "Composite" "true"
#    Option         "AllowGLXWithComposite" "true"
EndSection
```

You need to be running a accelerated driver(3d), uncomment the second line for nvidia.

```
use a background image on the panels in xfce
```

Got to tweak the gtk2.0

```
can gnome panel items be used in xfce
```

install "xfce4-xfapplet-plugin" , don't think you can use xfce4 applets in gnome.

---

### Post by kerry_s on 2007-03-01
> **john.nicholls said:**
> I think the answer to all three questions is no, but you'll find the definitive answers if you search the archives at the xfce.org discussion list, where these questions have frequently come up.

Jhon, see here for dapper upgrade-> [http://www.ubuntuforums.org/showthread.php?t=370341](http://www.ubuntuforums.org/showthread.php?t=370341)

---

### Post by Ptero-4 on 2007-04-01
[QUOTE=kerry_s]Got to tweak the gtk2.0[/QUOTE]

By "tweak gtk2" do you mean modding the gtk2 source code or modding a specifical gtk2 theme/theme engine? And what mods are these?

---

### Post by john.nicholls on 2007-04-02
> Jhon, see here for dapper upgrade-> [http://www.ubuntuforums.org/showthread.php?t=370341](http://www.ubuntuforums.org/showthread.php?t=370341)


Thanks for the info.
John

---

