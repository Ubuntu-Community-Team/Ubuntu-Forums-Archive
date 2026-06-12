---
title: "Resolution error loading gnome-desktop"
date: 2010-02-11
forum: Desktop Environments
---

### Post by TheProphetJonah on 2010-02-11
I had reported this as a bug in gnome, now I've recreated the error, AND I know where and why it's hanging on loading the desktop.

I had put a new monitor to my system, one with much higher resolution, 1900x1400 or something similar, my older monitor did 1280x1024.

So smart fellow that I am, I didn't just reconfigure that resoultion by making the fonts, icons and windows larger to compensate for the higher resolution, and just stepped down the resolution to the 1280x1024 @85Hz. It works when I reboot the system or restart X...

[SIZE=4]_***IF***_[/SIZE] 

I remember to reset it to the default before rebooting.
Otherwise, it gives me a not-infinite-yet-still-annoying loop of attempting to restart the desktop, immediately after the login screen. it shows the Ubuntu logo in the center, flickers to show the Ubuntu logo off center to the right, then back to the login screen, I put in my password again, same thing...

My last attempt was 15 minutes ago and after 11 times watching it do this mess I gave up and booted my Knoppix partition to post this.

Since I know where it's doing it, now I need to know which Gnome configuration file to make it stop.

The monitor is a Samsung SyncMaster 900NF and graphix card is Matrox Millennium, 
The hardware manager recognizes the card but says "Unknown Monitor" in the screen settings from the gnome panel. and I haven't found any GUI app in Gnome to change that value.

I don't even know if it makes a difference.

Summary, when I set the resolution to the lower value, the startup bug happens, if when I complete the session I re-reset the value back to the higher resolution no problem, it travels through the login screen to the Desktop smoothly.

---

### Post by flippo on 2010-02-11
Do you get any different errors in /var/log/Xorg.0.log when you get the bug? If so, can you post them?

---

### Post by TheProphetJonah on 2010-02-11
Apparently, it's stopping at IM, samba-share (because I've got three NTFS partitions on the system)  and the first part is the gnome-settings-daemon with "assertion 'src != NULL' failed. then it queries Xgl, not present.

Mentions that the error is logged to /var/log/Xorg.0.log 

which gives me 

> (==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default mga Device 0"
        Driver    "mga"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default mga Screen 0"
        Device    "Builtin Default mga Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default mga Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration --- as the defaults.
the ./xsession-errors log file:
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-9ZoUKe/socket
SSH_AUTH_SOCK=/tmp/keyring-9ZoUKe/socket.ssh

(gnome-settings-daemon:1745): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/jonah/.config/metacity/sessions/1056025ee6c4506a9d126590544734909600000016790022.ms: Failed to open file '/home/jonah/.config/metacity/sessions/1056025ee6c4506a9d126590544734909600000016790022.ms': No such file or directory
Unable to find a synaptics device.

(nautilus:1801): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1797): DEBUG: Adding applet 0.
** (gnome-panel:1797): DEBUG: Initialized Panel Applet Signaler.
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** (gnome-panel:1797): DEBUG: Adding applet 1.

(polkit-gnome-authentication-agent-1:1820): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1820): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: killswitches state 3
** (gnome-panel:1797): DEBUG: Adding applet 2.
** (gnome-panel:1797): DEBUG: Adding applet 3.
** (gnome-panel:1797): DEBUG: Adding applet 4.
** (gnome-panel:1797): DEBUG: Adding applet 5.
** (gnome-panel:1797): DEBUG: Adding applet 6.
Initializing nautilus-gdu extension

** (nautilus:1801): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1801): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1801): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:1797): DEBUG: Adding applet 7.
** (gnome-panel:1797): DEBUG: Adding applet 8.
** (gnome-panel:1797): DEBUG: Adding applet 9.
** (gnome-panel:1797): DEBUG: Adding applet 10.
evolution-alarm-notify-Message: Setting timeout for 27314 1265932800 1265905486
evolution-alarm-notify-Message:  Thu Feb 11 17:00:00 2010

evolution-alarm-notify-Message:  Thu Feb 11 09:24:46 2010


(firefox:1964): GLib-WARNING **: g_set_prgname() called multiple times

(nautilus:2021): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
Then from the Xorg.0.log file, not an error exactly. but I have an older bios without ACPI support, which I made sure to check that when I installed Ubuntu, at the bootup from CD screen. But grub didn't put it into the Non-editable grub.conf file so Xorg.0.log gives me:
> (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)

Xorg recognizes the monitor, somehow this doesn't get to Gnome's Hardware sections, gnome reports it as "unknown monitor"
> (II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:E-EDID segment register" registered at address 0x60.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C monitor info
(II) MGA(0): Manufacturer: SAM  Model: 2f  Serial#: 1095840057
(II) MGA(0): Year: 2003  Week: 3
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MGA(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
 
And nothing actually starting with an (EE) error notice in Xorg.0.log

Which putis it right back to gnome.

X loaded before the login screen anyway. So X was successful.

From what I can see in the xsession-errors log it's calling 5 gnome apps and failing.

On the session (this one) that's recorded there, it only cycled through the login screen three times.

Is there an heuristic auto-correction for gnome, where the gnome-desktop init will correct such errors, and eventually the problem (from the point of view of the user) simply go away with enough tries?

---

### Post by flippo on 2010-02-11
Hmm, this one seems to be beyond me.  Hopefully someone else can help you out on it.  Sorry.

---

### Post by TheProphetJonah on 2010-02-11
Right now it doesn't destroy the system, it's an annoyance. If it's just my hardware configuration that does it, then it'll remain a curiosity piece. If it's happening more often then I'm certain somebody else is also working on it. Or will be. 

That's what community development is for, it's working fairly well so far.

It's why We have an OS that works on real world hardware and They don't.

I suspect that the Microsoft test kitchen laboratory whatever only has the latest two generations of PCs.

---

