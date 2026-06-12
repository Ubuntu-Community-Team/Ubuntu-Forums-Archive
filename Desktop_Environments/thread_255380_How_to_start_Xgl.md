---
title: "How to start Xgl?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Vinze on 2006-09-11
Hey, I followed [this post](http://ubuntuforums.org/showthread.php?t=203877#postmenu_1324503) but apparently it did not work. Thanks to ```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```
I now have drop shadows but I think those are Xfce's. When I select the "Xgl session" from the gdm it takes a few seconds, then brings me back to the gdm. How can I fix this?

Maybe this'll help:

> $ startxgl-xfce 1 xfce nvidia/other
###### STARTXGL SCRIPT ######
Starting X Server with XGL
   Using Display 1
   Using WM: xfce
   Using Card: nvidia/other

Fatal server error:
no GLX visuals available

   Starting Compiz
   Starting Window Manager
/usr/bin/startxgl-xfce: line 45: gnome-window-decorator: command not found
/usr/bin/compiz: Couldn't open display :1

(xfce4-session:5947): Gtk-WARNING **: cannot open display:


Thanks in advance.

---

### Post by kwalo on 2006-09-11
Are you trying to set-up Xgl, or aiglx. If you have nvidia, or ati card you should install Xgl. For open source graphics, there is aiglx. Follow instructions from [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager). Everything should work fine.

---

### Post by Vinze on 2006-09-11
> **kwalo said:**
> Are you trying to set-up Xgl, or aiglx. If you have nvidia, or ati card you should install Xgl. For open source graphics, there is aiglx. Follow instructions from [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager). Everything should work fine.

I have nvidia and I tried Xgl, and it did not work ](*,)

---

### Post by kakulacis on 2006-09-11
> **Vinze said:**
> 
$ startxgl-xfce 1 xfce nvidia/other
###### STARTXGL SCRIPT ######
Starting X Server with XGL
Using Display 1
Using WM: xfce
Using Card: nvidia/other

Fatal server error:
no GLX visuals available

Starting Compiz
Starting Window Manager
/usr/bin/startxgl-xfce: line 45: [COLOR="Red"]gnome-window-decorator: command not found[/COLOR]
/usr/bin/compiz: Couldn't open display :1

(xfce4-session:5947): Gtk-WARNING **: cannot open display:


i'm not an expert but doesn't text marked with red give you an idea? :)
[COLOR="Red"]gnome-window-decorator: command not found[/COLOR] Do you have a gnome-window-decorator?

---

### Post by Vinze on 2006-09-11
> **kakulacis said:**
> i'm not an expert but doesn't text marked with red give you an idea? :)
[COLOR="Red"]gnome-window-decorator: command not found[/COLOR] Do you have a gnome-window-decorator?

Nope, I thought of that too but > $ sudo apt-get install gnome-window-decorator
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-window-decorator


---

### Post by kakulacis on 2006-09-12
$locate gnome-window-decorator
/usr/bin/gnome-window-decorator
/home/username/[COLOR="Red"]compiz/gnome[/COLOR]/window-decorator/gnome-window-decorator.c

It means that gnome-window-decorator is compiz component and particularly compiz-gnome component, so make your decisions :)

---

### Post by Vinze on 2006-09-12
> **kakulacis said:**
> $locate gnome-window-decorator
/usr/bin/gnome-window-decorator
/home/username/[COLOR="Red"]compiz/gnome[/COLOR]/window-decorator/gnome-window-decorator.c

It means that gnome-window-decorator is compiz component and particularly compiz-gnome component, so make your decisions :)

Weird.. That guy said the instructions were for Xubuntu... Well, guess I'll start looking for another guide then.

---

