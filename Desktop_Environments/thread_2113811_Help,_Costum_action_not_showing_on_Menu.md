---
title: "Help, Costum action not showing on Menu"
date: 2013-02-08
forum: Desktop Environments
---

### Post by X_Splinter on 2013-02-08
I am trying in last hour to get this to work.

So I want to add script on the "right mouse click" action menu to verify .iso files on abgx360

So kde4-config --path services givesme this

```
/home/x_splinter/.kde/share/kde4/services/:/usr/share/kde4/services/

```

I created abgx.desktop and inside I wrote this

```
[Desktop Entry]
Encoding=UTF-8
ServiceTypes=application/x-cd-image,application/x-iso
Actions=Verify
Type=Service

[Desktop Action Verify]
Name=Verify Xbox360 Iso
Name[pt]=Verificar Iso Xbox360
Exec=abgx360 -vw -af3 %f
Icon=k3b 

```

Then I place it in

/usr/share/kde4/services/ServiceMenus/

and

/home/x_splinter/.kde/share/kde4/services/

and

/home/x_splinter/.kde/share/kde4/services/ServiceMenus/

and

/usr/share/kde4/services

Did work on any of them... it just dont show on the menu.

it also does not show on the Dolphin settings - services.

What I am missing?

---

