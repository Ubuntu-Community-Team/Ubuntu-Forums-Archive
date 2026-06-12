---
title: "Can see the nautilus menu in Desktop when using Gnome Shell"
date: 2012-03-01
forum: Desktop Environments
---

### Post by THPubs on 2012-03-01
Hi, when I update my system several weeks ago, I started to see the nautilus menu in my desktop! I saw this because I had a transparent Gnome Shell panel.

Today I re installed Ubuntu and things seems to be ok. Then I installed a shell extension which will hide the top menu... When its hidden, I can again see the menu! Anyone know how to get rid of it?

Check the attached image... Its a gnome shell environment in Ubuntu. The top panel is hidden!

[IMG]http://dl.dropbox.com/u/51654769/menu-in-desktop.png

---

### Post by Krytarik on 2012-03-01
Run this command; then relogin:
```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && [ "$DESKTOP_SESSION" != "ubuntu-2d" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```Regards.

---

### Post by markbl on 2012-03-01
Krytarik, I recognise your snippet above as a slightly modified version of something I have posted about here and elsewhere. Apart from ubuntu (Unity), your version fixes it for ubuntu-2d which I must admit I forgot about. Given that, a slightly neater solution is:

```

echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

---

### Post by Krytarik on 2012-03-01
> **markbl said:**
> Krytarik, I recognise your snippet above as a slightly modified version of something I have posted about here and elsewhere. Apart from ubuntu (Unity), your version fixes it for ubuntu-2d which I must admit I forgot about. Given that, a slightly neater solution is:

```

echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```
Yeah, exactly, I've modified your command to exclude Unity 2D as well. :P And I'll test your new, more streamlined version later. Thanks!

---

### Post by THPubs on 2012-03-01
> **markbl said:**
> Krytarik, I recognise your snippet above as a slightly modified version of something I have posted about here and elsewhere. Apart from ubuntu (Unity), your version fixes it for ubuntu-2d which I must admit I forgot about. Given that, a slightly neater solution is:

```

echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

Thanks mate it worked :D Is it ok if i write about it on my blog mentioning about you?

---

### Post by markbl on 2012-03-02
> **THPubs said:**
> Thanks mate it worked :D Is it ok if i write about it on my blog mentioning about you?
Go for your life buddy :D

It is depressing that this trivial bug has not been fixed officially though.

---

### Post by THPubs on 2012-03-03
> **markbl said:**
> Go for your life buddy :D

It is depressing that this trivial bug has not been fixed officially though.

:D Is it only appearing when using Gnome Shell or does Unity get that menu? (I didn't checked :))

If its only in Gnome Shell, then Ubuntu really hates it :P

---

### Post by kazztan0325 on 2012-03-03
Actually it appears when using 'Cinnamon Desktop' also.

However we can make it disappear temporarily if we TURN OFF "Have file manager handle desktop" with "Advanced Settings (gnome-tweak-tool)"..., but this is not an essential solution.

---

### Post by THPubs on 2012-03-03
> **kazztan0325 said:**
> Actually it appears when using 'Cinnamon Desktop' also.

However we can make it disappear temporarily if we TURN OFF "Have file manager handle desktop" with "Advanced Settings (gnome-tweak-tool)"..., but this is not an essential solution.

This will disable the desktop icons :) Can you please try markbl's solution and tell us the results?

---

### Post by kazztan0325 on 2012-03-03
Okay, I'll try it tomorrow and tell you the results, because it is the time to go to bed in Japan...
See you later!

---

### Post by yo_bhan on 2012-03-03
> **kazztan0325 said:**
> Okay, I'll try it tomorrow and tell you the results, because it is the time to go to bed in Japan...
See you later!

if you prefer using gnome shell not using unity global menu, just remove unity global menu.

```
sudo apt-get --purge remove appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
```

---

### Post by kazztan0325 on 2012-03-03
> **yo_bhan said:**
> if you prefer using gnome shell not using unity global menu, just remove unity global menu.

```
sudo apt-get --purge remove appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
```

Hi yo_bhan,

Thanks for your advice, but sorry, actually I hate gnome shell, and do not like unity.
However I like 'Window Buttons' and 'Global Menu' are on top panel, so I put 'gnome-window-applets' and 'xfce4-appmenu-plugin' on top panel in Xubuntu Session.

---

### Post by kazztan0325 on 2012-03-03
> **THPubs said:**
> This will disable the desktop icons :) Can you please try markbl's solution and tell us the results?

Hi THPubs,

I tried markbl's solution on 'Cinnamon Desktop', and it worked!
Wow, How amazing!!
Krytarik and markbl seem to me to be wizards.

---

### Post by Devi 710 on 2012-03-27
> **Krytarik said:**
> Run this command; then relogin:
```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && [ "$DESKTOP_SESSION" != "ubuntu-2d" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```Regards.

I just ran this and now I can't login to any desktop environment!

How can I reverse this command? I can login into via CTRL+ATL+F3, but I don't know what command to run.

-Ubuntu 11.10, 64 bit, ATI drivers installed

---

### Post by markbl on 2012-03-27
> **Devi 710 said:**
> I just ran this and now I can't login to any desktop environment!
You must have typed the command incorrectly. DONT TYPE IT - Copy and paste it with your mouse (highlight select and then middle click in terminal). Make sure you copy the whole line. Here is a slightly shorter version:
```

echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

---

### Post by Devi 710 on 2012-03-27
Many thanks for the quick reply. I realy needed at file.

I ran the command (had to type it as I was in a terminal session) and I can login into my desktop environments now :)

Unfortunately, it didn't fix gnome shell. I have two ugly panels:

[http://dl.dropbox.com/u/1483214/gnome-shell-panels-1.png]("http://dl.dropbox.com/u/1483214/gnome-shell-panels-1.png")

It's almost like it mixed Cinnamen with Gnome Shell... weird

---

### Post by Devi 710 on 2012-03-27
I just fixed the panels in gnome shell issue by uninstalling the proprietary ATI drivers for my HD5450 video card. Gnome Shell works again! But now how do I play Doom 3 :(

Thanks for all the help.

---

