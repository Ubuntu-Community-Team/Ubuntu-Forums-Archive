---
title: "xearth in unity?"
date: 2014-10-09
forum: Desktop Environments
---

### Post by MikeCyber on 2014-10-09
Hi
I remember long time ago I had xearth on FreeBSD. Now I wonder if that would still work in Unity? There's no repo for xearth anymore?
Thanks

---

### Post by grahammechanical on 2014-10-09
> [COLOR=#000000]There's no repo for xearth anymore?[/COLOR]

It that a question or a statement? If we have the Universe and the Multiverse repositories enabled and we have searched for xearth in the software centre and it replies with a "not found" message then the answer is No.

What information do you have to confirm that the software is still maintained and packaged for Ubuntu?

---

### Post by ibjsb4 on 2014-10-09
Xearth is now xplanet.

[http://xplanet.sourceforge.net/](http://xplanet.sourceforge.net/)

[http://packages.ubuntu.com/trusty/xplanet](http://packages.ubuntu.com/trusty/xplanet)

---

### Post by tgalati4 on 2014-10-09
Open a terminal:

```
sudo apt-get install xplanet
xplanet
```

---

### Post by MikeCyber on 2014-10-10
Thanks, but does that work in Unity without losing icons etc.?

---

### Post by ibjsb4 on 2014-10-10
> Thanks, but does that work in Unity without losing icons etc.?
If it will not fly in Unity (compiz) you could try adding a different desktop/wm to your system.  Flashback (metacity).
```
sudo apt-get install gnome-session-flashback
```
And choose your desktop at login.

---

### Post by mcduck on 2014-10-11
no, it won't work on any desktop environment where the file manager handles both the desktop icons and wallpaper. (or, actually, it works just fine, you'll just either never see it since it's drawing behind the desktop window, or can't see the icons since it's drawing on top of the desktop window...)

You can work around that by telling the file manager to not handle the desktop, and then using some additional program to get just the desktop icons back. If you choose to for that, then look for instructions made for barebones window managers (like Openbox) as they are where people most commonly use additional software for desktop icons only.

(and no, using gnome-session-flashback doesn't help. It uses exactly the same file manager to manage it's desktop as Unity does.)

---

### Post by CantankRus on 2014-10-11
It works here in ubuntu 14.04 using the script found @ [http://xplanet.sourceforge.net/FAQ.php#gnome](http://xplanet.sourceforge.net/FAQ.php#gnome)
I installed xplanet through synaptic then added the script to startup applications making just the one change in the script.
May need to change the **geometry=1680x1050** also.
```
# location of the xplanet binary
xplanetBin=**${HOME}/local/xplanet-1.3.0/bin/xplanet**
```
to
```
# location of the xplanet binary
xplanetBin=**/usr/bin/xplanet**
```
I have never used xplanet before so don't know if this script gives full funtionality but it is drawing images to the desktop
by replacing the background  image using **gsettings set org.gnome.desktop.background picture-uri** 
so nautilus is still drawing the desktop and icons.

---

### Post by MikeCyber on 2014-10-12
Thanks, that works in Unity. How do you change the default to only show earth? (and if possible current clouds)

---

### Post by CantankRus on 2014-10-12
Like I said I haven't used before and am just seeing what I can do.
I just found a deb file for **xplanetfx** which includes a gui to enhance the use of xplanet.
Uses imagemagick to manipulate images
Find the deb [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://repository.mein-neues-blog.de:9000/")
Blog page----> [http://mein-neues-blog.de/xplanetFX/](http://mein-neues-blog.de/xplanetFX/)
This works and allows you to position the earth in an existing wallpaper among other options.
In the third pic notice "GNOME" is selected.

(PS remove the xplanet startup script you may have added previously to startup applications)

---

### Post by MikeCyber on 2014-10-17
Great works fine but doesn't update. How do you get it to update every 15min. The setting only works after 
manually pushing refresh but not auto.
Thanks

---

### Post by CantankRus on 2014-10-17
Works ok here.
Enabling autostart in the xplanetfx tools tab adds xplanetfx to startup applications and
if you log out/in you should see it running in the system monitor.

---

### Post by MikeCyber on 2014-10-18
Thanks

---

