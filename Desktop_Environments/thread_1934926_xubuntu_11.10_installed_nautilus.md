---
title: "xubuntu 11.10 installed nautilus"
date: 2012-03-03
forum: Desktop Environments
---

### Post by cookiepowa on 2012-03-03
hiya,

so i just installed xubunrtu 11.10, only to discover it uses thunar which dont have network support. so i went to terminal and apt-get install nautilus


also set in preffered applications file manager to nautilus

now when i rebooted none of my desktop icons works, when i double click on the icons it give me this message:

Failed to execute program /usr/bin/Thunar: Success

odd thing is using the dock on the bottom to luanch a file browser uses nautilus and turns my desktop to a blank blue background.

so any one know how i can fix this?

---

### Post by kazztan0325 on 2012-03-03
Hi cookiepowa,

If you would like to avoid the odd things, I think you might want to install **"pcmanfm"** file manager and set it as preferred file manager.

In my case, I also installed "Nautilus" on Xubuntu Session, because I need to install "nautilus-dropbox" to use Dropbox.
But as for file manager, I like to use **"pcmanfm"** more than "Thunar" and "Nautilus", so I installed "pcmanfm" and set it as preferred file manager.

This way, the odd thing which you mentioned does not occur even if I open "Nautilus".
However, I don't know why but "Thunar" opens when I double click on the desktop Home icon...

---

### Post by Toz on 2012-03-03
> **cookiepowa said:**
> hiya,

so i just installed xubunrtu 11.10, only to discover it uses thunar which dont have network support. 
Thunar _does_ have network support. Make sure you install gvfs-backends. 
> so i went to terminal and apt-get install nautilus


also set in preffered applications file manager to nautilus

now when i rebooted none of my desktop icons works, when i double click on the icons it give me this message:

Failed to execute program /usr/bin/Thunar: Success
To make nautilus default, see this link: [http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu]("http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu")

> odd thing is using the dock on the bottom to luanch a file browser uses nautilus and turns my desktop to a blank blue background.

so any one know how i can fix this?
Nautilus is changing the background because it also, by default, manages the desktop. See this link: [http://ubuntuforums.org/showthread.php?t=1768245]("http://ubuntuforums.org/showthread.php?t=1768245").

And oh, btw, welcome to the forums.

---

### Post by rattskjelke on 2012-03-03
When you install another file manager besides Thunar how do you make it the default?

---

### Post by Toz on 2012-03-03
If its nautilus, first disable its ability to control the desktop. Open a terminal window and run the following commands:
```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false

```

Logout and back in again.

---

### Post by Krytarik on 2012-03-03
> **Toz said:**
> If its nautilus, first disable its ability to control the desktop. Open a terminal window and run the following commands:
```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false

```Logout and back in again.
Since *ubuntu 11.10, it's:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
gsettings set org.gnome.desktop.background draw-backround false
```And the changes should take effect immediately.

Regards.

---

### Post by cookiepowa on 2012-03-07
> **Krytarik said:**
> Since *ubuntu 11.10, it's:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
gsettings set org.gnome.desktop.background draw-backround false
```And the changes should take effect immediately.

Regards.

thanks this worked :D

last problem is fixing the desktop icons to use nautilus instead of thunar and giving me a error. any ideas?

---

### Post by Rytron on 2012-03-22
I installed nautilus in Xubuntu 11.10 but get this [[image]("http://ubuntuforums.org/attachment.php?attachmentid=206223&d=1320334634")] on my desktop when I launch nautilus.

Update:
This solves it. As Krytarik stated earlier:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
gsettings set org.gnome.desktop.background draw-backround false
```

---

