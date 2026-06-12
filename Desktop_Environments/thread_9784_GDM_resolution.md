---
title: "GDM resolution"
date: 2005-01-01
forum: Desktop Environments
---

### Post by Darrena on 2005-01-01
My GDM login screen resolution is 1600x1200 but my desktop resolution is 1024x768, is there a way to reduce the resolution on login to something a little lower?

Thanks!

---

### Post by HankB on 2005-01-01
I'm not sure if there's an Ubuntu way, but you can do this by modifying your X configuration file: /etc/X11/XF86Config-4

1- make a backup copy!!!
2 - find the section named "Screen"
```
Section "Screen"
   .
   .
   .
        DefaultDepth    24

```
This will tell you  which line to look for further in this section. In my case this is:
```
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection

```

The first resolution on this line is what my system uses for the default (GDM) resolution. Once you make the change, you will need to log out to or restart gdm for it to take effect. (I'm not sure which) To restart GDN, type ```
sudo /etc/init.d/gdm restart
``` You might be better off to do that outside of X by hitting <ctrl><alt><f1> and logging in.

Now... If there's a GDM configuration that does this or an Ubuntu configuratoin tool that does this, I hope someone speaks up!

HTH.

---

### Post by Darrena on 2005-01-02
[QUOTE=HankB]I'm not sure if there's an Ubuntu way, but you can do this by modifying your X configuration file: /etc/X11/XF86Config-4

1- make a backup copy!!!
2 - find the section named "Screen"
```
Section "Screen"
   .
   .
   .
        DefaultDepth    24

```
This will tell you  which line to look for further in this section. In my case this is:
```
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection

```

The first resolution on this line is what my system uses for the default (GDM) resolution. Once you make the change, you will need to log out to or restart gdm for it to take effect. (I'm not sure which) To restart GDN, type ```
sudo /etc/init.d/gdm restart
``` You might be better off to do that outside of X by hitting <ctrl><alt><f1> and logging in.

Now... If there's a GDM configuration that does this or an Ubuntu configuratoin tool that does this, I hope someone speaks up!

HTH.[/QUOTE]
 I had tried that earlier and while it reduces the viewable resolution the rest of the screen (Like the options on the bottom) are not visible.  :(

Any other thoughts?  It's almost like it is using a virtual desktop...

---

### Post by fng on 2005-01-04
Could you check your /etc/X11/XF86Config-4 config file again?

```
Section "Screen"
...

    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection
``` 

Be sure the Virtual-line is commented!

---

### Post by Darrena on 2005-01-05
*smacks head*

Doh!  I am a moron, I did not remove the resolution on the other color depths, I guess the login screen uses a different color depth than 24 since I only modified that one (Stupidly) assuming that it shared the same color depth as my desktop.

Sorry about that!

---

