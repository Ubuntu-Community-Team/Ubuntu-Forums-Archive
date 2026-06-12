---
title: "Force Quit in 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by teluma on 2011-10-15
Hello.

I miss the Force Quit applet.... so I found a script fore a similar app here: [http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/](http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/).  My problem is that it will not drop into the Unity launcher, it drags but then gets evicted, whereas other shortcut icons are accepted!  

Can anyone tell me another way of adding it so that it is accessible?

Also, I really miss a straight forward panel displaying icons for all open programs, like the Gnome Panel. Has anyone created something like this for Unity?

Thanks

---

### Post by Hreinsi on 2011-10-15
gedit ~/.local/share/applications/quit.desktop

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg

save 

Drag it from dash

---

### Post by Spr0k3t on 2011-10-15
Awesome tip Hreinsi.  Tagged for later use.

---

### Post by Krytarik on 2011-10-15
I'd change this:
> **Hreinsi said:**
> Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
... to this:
```
Icon=process-stop
```
So that it adapts to any other themes than "Humanity".

Regards.

---

### Post by teluma on 2011-10-16
Many thanks Hreinsi, that's great!

One other thing, is there something I can add to cancel the force quit process, by pressing Esc?

---

### Post by mcduck on 2011-10-16
> **teluma said:**
> Many thanks Hreinsi, that's great!

One other thing, is there something I can add to cancel the force quit process, by pressing Esc?

Just right-click instead of left-click.

---

### Post by teluma on 2011-10-16
> **mcduck said:**
> Just right-click instead of left-click.

:redface: As simple as that! Big thanks.

---

### Post by Hreinsi on 2011-10-16
This is nice to just found it looks good just tryed it :)

---

### Post by Hreinsi on 2011-10-16
This is nice to just found it looks good just tryed it :)

[http://www.omgubuntu.co.uk/2011/10/freezeunfreeze-unity-app-killer/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29&utm_content=FaceBook](http://www.omgubuntu.co.uk/2011/10/freezeunfreeze-unity-app-killer/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29&utm_content=FaceBook)

---

### Post by linuxuser12345 on 2011-11-05
Please vote!
[[IMG]http://brainstorm.ubuntu.com/idea/28840/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/28840/)

---

### Post by shantiq on 2011-12-04
> **Hreinsi said:**
> gedit ~/.local/share/applications/quit.desktop

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg

save 

Drag it from dash


thank you very much for this :D   two icons added here:KS

---

