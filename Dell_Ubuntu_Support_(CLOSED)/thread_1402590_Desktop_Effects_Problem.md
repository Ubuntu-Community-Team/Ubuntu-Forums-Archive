---
title: "Desktop Effects Problem"
date: 2010-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sparser on 2010-02-09
Hi,

I am using a Dell Dimension 2400 with an nVidia 8400GS PCI graphics card.

I am using ubuntu 9.10

The system is running fine - the only problem is that when I attempt to enable desktop effects I get an error message telling me that Desktop Effects Could Not Be Enabled.

I have installed the proprietary drivers for my card specifically - NVIDIA accelerated graphics driver (version 185).

However I cannot enable desktop effects even though the driver reports as activated and currently in use.

I have tried the 175 version also - however the result is the same - the desktop effects cannot be enabled.

I would appreciate any help you can give.

Thanks.

---

### Post by bonevg on 2010-02-09
Try with glxgears or glxheads
If it runs fine - then u have compiz problems.. probably as Andrea points in the following thread.
If you have old drivers that are NOT in use - remove them and that just may solve your problem as it solved mine and few more guyz's.

More help here.
[http://ubuntuforums.org/showthread.php?t=1328828&highlight=rendering+method](http://ubuntuforums.org/showthread.php?t=1328828&highlight=rendering+method)

---

### Post by lidex on 2010-02-09
Can you post the contents of:
```
gedit /etc/X11/xorg.conf
```
and
```
gedit ~/.xsession-errors
```

Welcome to the forums, BTW. Enter the above commands in a terminal. You can find one in your Applications menu under "Accessories"

---

### Post by Sparser on 2010-02-09
Hi, Thanks for the replies.

When I type glxgears they show Ok and spin around fine - no lag or juddering.

The only problem is that I can't enable desktop effects eventhough I have the drivers installed.

Here is the contents of xorg.conf :-

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```
Here is the contents of xsession-errors :-

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-zJHbaM/socket
SSH_AUTH_SOCK=/tmp/keyring-zJHbaM/socket.ssh

(gnome-settings-daemon:1539): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1539): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Unable to find a synaptics device.
Window manager warning: Failed to read saved session file /home/kris/.config/metacity/sessions/1018649d6acef474d3126573260937103100000014730022.ms: Failed to open file '/home/kris/.config/metacity/sessions/1018649d6acef474d3126573260937103100000014730022.ms': No such file or directory
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(nautilus:1571): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(polkit-gnome-authentication-agent-1:1595): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1595): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (gnome-panel:1570): DEBUG: Adding applet 0.
** (gnome-panel:1570): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1570): DEBUG: Adding applet 1.
** (gnome-panel:1570): DEBUG: Adding applet 2.

** (nautilus:1571): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1571): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1571): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:1570): DEBUG: Adding applet 3.
Initializing nautilus-gdu extension
** (gnome-panel:1570): DEBUG: Adding applet 4.
** (gnome-panel:1570): DEBUG: Adding applet 5.
** (gnome-panel:1570): DEBUG: Adding applet 6.
** (gnome-panel:1570): DEBUG: Adding applet 7.
** (gnome-panel:1570): DEBUG: Adding applet 8.
** (gnome-panel:1570): DEBUG: Adding applet 9.
** (gnome-panel:1570): DEBUG: Adding applet 10.
evolution-alarm-notify-Message: Setting timeout for 27358 1265760000 1265732642
evolution-alarm-notify-Message:  Wed Feb 10 00:00:00 2010

evolution-alarm-notify-Message:  Tue Feb  9 16:24:02 2010


(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
There is not a graphics driver available for your system which supports the composite extension, or the current driver already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1705): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(firefox:1744): GLib-WARNING **: g_set_prgname() called multiple times

(nautilus:1805): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(gnome-appearance-properties:1843): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a00003 (Archive Ma)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

---

### Post by lidex on 2010-02-09
Try this command and then reboot:
```
sudo nvidia-xconfig
```

---

### Post by Sparser on 2010-02-09
I ran the command and the terminal told me that the xorg.conf file was incomplete so it wrote a new one. I then rebooted but the problem is still the same.

---

### Post by lidex on 2010-02-09
What is jockey (hardware drivers) telling you?

---

### Post by Sparser on 2010-02-09
Here is a a screnshot of my system > preferences > Hardware Drivers

[http://i46.tinypic.com/5frr13.png](http://i46.tinypic.com/5frr13.png)

It is the 185 driver that I have active

---

### Post by lidex on 2010-02-09
Uninstall v 173 drivers

Next:
```
sudo nvidia-settings
```

Reboot

---

### Post by Sparser on 2010-02-09
Should  I uninstall the 185 driver and install the 173 driver then run the command and reboot?

---

### Post by lidex on 2010-02-09
No. You want to uninstall all drivers except 185

Edit:Use synaptic and search "nvidia" and uninstall any drivers not v.185.(or 180 - may show as both/either depending on where you look)

---

### Post by Sparser on 2010-02-09
OK, the only driver installed now is the 185 driver.

When I run sudo nvidia-settings the nvidia x server box is displayed, here is a screenshot of it :-

[http://i46.tinypic.com/nfjzaw.png](http://i46.tinypic.com/nfjzaw.png)

---

### Post by Sparser on 2010-02-09
Ok, I think I have only got the 185 drivers in synaptic.

Here is a print screen of my synaptic when I search for nvidia

[http://i46.tinypic.com/nzhc42.png](http://i46.tinypic.com/nzhc42.png)

---

### Post by lidex on 2010-02-09
Looks good.

---

### Post by Sparser on 2010-02-09
Still no luck. In the hardware drivers it reports that the 185 drivers are working but the desktop effects wont activate.

Do you know anything else I could try to get he desktop effects to work?

Thanks very much for trying.

---

### Post by lidex on 2010-02-09
Where did you install those drivers from?

---

### Post by Sparser on 2010-02-09
When I first tried to enable the desktop effects a pop up box appeared telling me that I needed to install proprietary drivers so I followed it's instructions and the 185 drivers were installed. I rebooted but when I tried to enable desktop effects it would not work.

---

### Post by lidex on 2010-02-09
You could try uninstalling the driver, rebooting, then re-installing and rebooting one more time.

I've never tried it but a lot of users report good results using envy. Info here:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by lidex on 2010-02-09
This may be helpful:
[http://ubuntuforums.org/showthread.php?t=1116026]("http://ubuntuforums.org/showthread.php?t=1116026")

---

### Post by Sparser on 2010-02-09
Ok, I uninstalled all the nvidia drivers and rebooted.

When I tried to enable desktop effects I got this box :-

[http://i48.tinypic.com/153bfb7.png](http://i48.tinypic.com/153bfb7.png)

So I enabled the driver and it downlaoded and installed it, and then presented me with this box :-

[http://i50.tinypic.com/2a9znkh.png](http://i50.tinypic.com/2a9znkh.png)

So I rebooted but when I try to enble desktop effects it simply tells me that they could not be enabled.

---

### Post by lidex on 2010-02-09
Can you post your xorg.conf again?

Try this in a terminal and post output:
```
compiz --replace
```

Go here and run the compiz-check script:
[http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by bonevg on 2010-02-11
If glxgears worked on 1st place as you said using any of those nvidia drivers, then you have operational VGA driver.
Looking further deep into this won't be much of use is what i suspect.

However I have a direction for you.
If you still run glxgears and if you have operational nvidia driver in use, then download **compiz-check** from let's say here: 

```
http://forlong.blogage.de/entries/pages/Compiz-Check
```

It is all explained At the page I gave u as link.

and/or check if your compiz blacklisted your vga driver
For that use your favorite text editor and open /usr/bin/compiz
more info at the link I gave you in the 1st answer of your thread.

---

