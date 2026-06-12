---
title: "Nautilus refresh problem..."
date: 2011-01-21
forum: Desktop Environments
---

### Post by Eremis on 2011-01-21
Hi guys,

I am running ubuntu 10.04 LTS, and I got a little annoying nautilus problem... Not too long ago I installed a theme which required me to change the engine (in GNOME color chooser) to Murrine. This made my desktop look a whole lot nicer but now when I scroll down/up in nautilus everything "smudges" together (See the screenshots). I dont know if this makes a difference but when I put my mouse over "Where the icons should be" they appear there, but there are still smudges...

I dont know weather that change caused this, or maybe something totally different. 

I am running this on an old machine (2.66 Ghz Pentium 4, 1Gb RAM, NVIDIA 440MX with AGP8X) (running 96 nvidia driver)...

Never had any problems before, and I really dont want to reinstall... (Using nautilus and scrolling is nearly impossible)

Will someone please help? 
Thx

If you need more info, just post...

---

### Post by Krytarik on 2011-01-21
Hi Eremis,

I have a fairly similar hardware setup like you, also an old Nvidia video card with driver version 96 running. I experience the same behaviour when I use "Nautilus Elementary" instead of the default one, although I like its look and its options I cannot use it. A fairly large amount of people and theme creators recommend it, also the creator of the "Elegant Gnome" theme. If you have it installed (NE), downgrade it by forcing its version in Synaptic and remove/disable its PPA.

Greetings.

---

### Post by Eremis on 2011-01-22
Yes I did have nautilus elementary, but I uninsulated it using the PPA (ppa purge I believe) which was supposed to uninstall the elementary package and install the one from default repos...

What exactly did you do to fix this?

Thx

---

### Post by Eremis on 2011-01-22
Attached another picture with how my sources and synaptic look...
What would I have to do to get the "old" nautilus back?

---

### Post by Krytarik on 2011-01-22
Ok, I have just checked the current official version number of "nautilus" and "nautilus-data" in Lucid: it's "2.30.1-0ubuntu1.1".

Since you have a higher number listed, downgrade them by "forcing" its version, but you have to be really carefull, because it sometimes wants to uninstall "ubuntu-desktop" alltogether:
- first click at "nautilus-data"
- click in the menu at "Package", the "Force Version..."
- choose the mentioned lower one
- at this point, it should say that "nautilus" will also be downgraded
- then apply the changes

If that way around doesn't work, try the other way around.

One thing I don't understand: You have already disabled the PPA for NE (am-monkey), but it still shows the current available version number. When done with the downgrade, check if Synaptic wants to upgrade them again!

When it's finally finished, restart Nautilus by pressing Alt+F2 and entering "killall nautilus", make sure that there is no active browser window before.

---

### Post by Eremis on 2011-01-22
ok, thx I will try this and get back to this post tomorrow...

---

### Post by Eremis on 2011-01-22
I tried forcing the older version on those packages, but it did not fix the problem, and now my desktop background is simply white and I cant change it... When I restart my regular background "flashes' for a sec then it disappears.... any ideas?

---

### Post by Krytarik on 2011-01-22
What version are now listed for "nautilus" and "nautilus-data", those I mentioned?
Try re-installing those packages.

---

### Post by Eremis on 2011-01-22
yes the ones you mentioned before are installed... Heres what I did to fix the background...

I installed elementary nautilus again (thought maybe the bug was fixed). Now my background is working again, but the scrolling issue still remains...

What would you recommend I do next?

---

### Post by Eremis on 2011-01-22
Here is how my packages look now...

---

### Post by Krytarik on 2011-01-22
I also installed it again recently, but as you can see, no difference.

Then downgrade the packages again.

Did you install anything else with it, or did any modification to that respect?

Did you the "killall nautilus" thing after the downgrade?

You may also try to reset the settings of nautilus by renaming/removing the directory:
/home/USER/.gconf/apps/nautilus .

---

### Post by Eremis on 2011-01-22
I've noticed that this happens not only in nautilus, but in other applications that use a scroll panel, for example as you can see the problem exists even in compiz effects settings window...

---

### Post by Eremis on 2011-01-22
ok so downgrade package "nautilus" from 1:2.31.1-0ubuntu2~ppa92(lucid) to 1:2.30.1-0ubuntu1.1(lucid-updates or 1:2.30.0-0ubuntu4(lucid) ? also should I use ppa purge to install the regular nautilus first?

---

### Post by Eremis on 2011-01-22
Also what other packages other then nautilus should I downgrade?


I was thinking.... what if I use "ppa purge" to revert back to regular nautilus, then rename the settings folder? Last time I only did ppa purge which did not fix my scrolling, or should I downgrade manually?

---

### Post by Krytarik on 2011-01-22
I would downgrade manually, more control, didn't try the ppa-purge app.

Downgrade to "lucid-updates".

Just do that, then restart nautilus with
```
killall nautilus
```and if the previously described issue re-occurs, move the folder to another location, but logout before and do it from within the console.

---

### Post by Eremis on 2011-01-22
downgrade nautilus and nautilus-data packages only? Or are there more packages I need to downgrade?

---

### Post by Krytarik on 2011-01-22
> **Eremis said:**
> downgrade nautilus and nautilus-data packages only? Or are there more packages I need to downgrade?
No, only "nautilus" and "nautilus-data". Sorry, forgot to answer that.

---

### Post by Eremis on 2011-01-22
Ok thx for your help so far, I will try it and get back with the results

---

### Post by Eremis on 2011-01-22
When I try to downgrade I get an error:

An error occurred:
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

Any ideas?

---

### Post by Krytarik on 2011-01-22
> **Eremis said:**
> When I try to downgrade I get an error:

An error occurred:
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

Any ideas?
Is another package manager running at the same time?

Do this before trying it again:
```
sudo apt-get --fix-broken install
```

---

### Post by Eremis on 2011-01-22
Downgraded nautilus + nautilus-data, renamed the directory you told me, and I am back to "white background" which I cant change and the scrolling is still messed up...

Any more ideas? lol

PS I renamed /home/user/.nautilus folder too once (read on a forum that I should do so...) could that have messed something up?

---

### Post by Krytarik on 2011-01-23
> **Eremis said:**
> 
PS I renamed /home/user/.nautilus folder too once (read on a forum that I should do so...) could that have messed something up?
No, not really.

Did you "killall nautilus" after that?

Regarding the other display issue: Did you downgrade the murrine package after you removed the theme? Although I noticed no difference when upgraded it upon the trial of the "Elegant Gnome" theme. Check the version, and downgrade it to "lucid-updates" or "lucid", whatever is available.

---

### Post by Eremis on 2011-01-23
yes I did kill nautilus after that... I just downgraded the murrine package, which also required me to uninstall elegant gnome, but I still have both the scrolling issue + and the white wallpaper...

---

### Post by Krytarik on 2011-01-23
Take a look into ~/.xsession-errors for error messages.

You may also try to create a new user and login with those.

---

### Post by Eremis on 2011-01-23
Got an idea for an easy fix...

What if I install ubuntu with live cd without partitioning the partitions... I mean use the same partitions to install ubuntu again, to override everything, will that work? 

A while ago I installed linux mint, without checking the "format" box and it did not destroy any data, but overwrote most settings to mint... Just thinking if this will work in this case as well...

---

### Post by Eremis on 2011-01-23
output from xsessions-errors file:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/andriy/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/none.
gnome-session[2525]: EggSMClient-WARNING: Desktop file '/home/andriy/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
GNOME_KEYRING_CONTROL=/tmp/keyring-3qwrOL
GNOME_KEYRING_CONTROL=/tmp/keyring-3qwrOL
SSH_AUTH_SOCK=/tmp/keyring-3qwrOL/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-3qwrOL
SSH_AUTH_SOCK=/tmp/keyring-3qwrOL/ssh

(polkit-gnome-authentication-agent-1:2600): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2600): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

progname=nvidia-settings; RGBA=on

progname=cairo-dock; RGBA=on

 ============================================================================ 
	Cairo-Dock version: 2.1.3-10-lucid
	Compiled date:  Apr 22 2010 01:07:55
	Running with OpenGL: 0
 ============================================================================


(gnome-power-manager:2605): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x984bb28'

(gnome-settings-daemon:2573): GLib-GObject-WARNING **: IA__g_object_notify: object class `GkbdStatus' has no property named `name'
Unable to find a synaptics device.

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/andriy/.compiz/session/106e1857fcfef1b522129576423922594600000025250037"
[1;38mwarning : [0m [0;37m(cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:406) [0m 
  while trying to load 01f-spot.desktop : Key file does not have key 'Is container'
separateur necessaire
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed

progname=canberra-gtk-play; RGBA=on

(gnome-appearance-properties:2689): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2689): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
separateur necessaire
/usr/share/themes/MurrinaCandido/gtk-2.0/gtkrc:84: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaVerdeOlivo/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaCappuccino/gtk-2.0/gtkrc:41: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:54: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:60: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:63: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:89: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:105: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:121: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:137: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:153: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:174: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:214: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:259: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Light/gtk-2.0/gtkrc:275: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/MurrinaEalm/gtk-2.0/gtkrc:47: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaFancyCandy/gtk-2.0/gtkrc:46: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Kiwi/gtk-2.0/gtkrc:78: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Kiwi/gtk-2.0/gtkrc:82: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaAzul/gtk-2.0/gtkrc:75: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaAzul/gtk-2.0/gtkrc:78: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:54: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/NOX/gtk-2.0/gtkrc:233: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:54: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:60: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:63: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:89: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:105: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:121: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:136: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:151: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:172: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:206: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:233: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:257: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:272: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/MurrinaBleu/gtk-2.0/gtkrc:85: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaLoveGray/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:86: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:134: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:187: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:249: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:294: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlue/gtk-2.0/gtkrc:83: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaCandy/gtk-2.0/gtkrc:46: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/A-New-Hope/gtk-2.0/gtkrc:118: error: unexpected identifier `trough_border_shades', expected character `}'
/usr/share/themes/A-New-Hope/gtk-2.0/gtkrc:118: error: unexpected identifier `trough_border_shades', expected character `}'
/usr/share/themes/MurrinaNeoGraphite/gtk-2.0/gtkrc:52: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Orangine/gtk-2.0/gtkrc:46: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaCream/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaAquaIsh/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 1504 error_code 2 request_code 113 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 760 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

progname=nautilus; RGBA=on
Initializing nautilus-gdu extension
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

progname=update-notifier; RGBA=on

progname=nautilus; RGBA=on
Attempting to load libmoonloaderxpi 

progname=gnome-appearance-properties; RGBA=on

progname=nautilus; RGBA=on
separateur necessaire
cairo_dock_search_icon_s_path: assertion `cFileName != NULL' failed
separateur necessaire

```

---

### Post by Krytarik on 2011-01-23
"Elegant Gnome" enables RGBA in Nautilus by default, try disabling it:

- press Alt+F2
- enter gconf-editor
- browse to "apps/nautilus/preferences"
- uncheck "rgba_colormap"

EDIT: And upgrade the murrine package again.

---

### Post by Eremis on 2011-01-23
Could not find that option, check screenshot...

BTW it seems like something is painting over the current wallpaper, because like I said before the wallpaper appears for split of a second when I kill nautilus, or restart x, then it looks like something is painting over it just white color...

---

### Post by Eremis on 2011-01-23
Tried to update the murrine package, but it does not let me (see screenshot), I think it's because there are no other versions ...

---

### Post by Krytarik on 2011-01-23
> **Eremis said:**
> Could not find that option, check screenshot...

BTW it seems like something is painting over the current wallpaper, because like I said before the wallpaper appears for split of a second when I kill nautilus, or restart x, then it looks like something is painting over it just white color...
Sorry, this should got reset by renaming the config dir.

Try those suggestion, although you get a different error message:
[http://ubuntuforums.org/showthread.php?t=1384038](http://ubuntuforums.org/showthread.php?t=1384038)

Try the new-user thing next please.

(I have to go to bed now.)

---

### Post by Krytarik on 2011-01-23
> **Eremis said:**
> Tried to update the murrine package, but it does not let me (see screenshot), I think it's because there are no other versions ...
That's because you disabled the PPA of Elegant Gnome. You may re-install those also.

---

### Post by Eremis on 2011-01-23
"(I have to go to bed now.)"

me too lol

I will try to do the user thing... Will get back to this probably sometime tommorow, again thanks for the help so far...

---

### Post by Krytarik on 2011-01-23
If you need to use a working file-manger in the meantime, try "gnome-commander", I use it occasionally, fast, but not really comfortable.;-)

---

### Post by Eremis on 2011-01-30
Personalty I dont mind browsing with terminal it's just this is my dads computer (he is not so computer savvy) so I need nautilus...

I fixed this issue with a bit of brute force... Since I did not have that many new software installed, I just reinstalled ubuntu without formating the partition, so I still have all my settings/ documents...

I was wondering, do you know if nautilus elementary devs will fix that issue?

---

### Post by Krytarik on 2011-01-30
> **Eremis said:**
> 
I fixed this issue with a bit of brute force... Since I did not have that many new software installed, I just reinstalled ubuntu without formating the partition, so I still have all my settings/ documents...

I'm surprised that this even possible! You could have instead just saved the "home" directory on another linux partition, and after install pulled it back.
> **Eremis said:**
> 
I was wondering, do you know if nautilus elementary devs will fix that issue?
I doubt it, I don't even have an idea how many users are affected by this. It seems to only affect really old machines, like we have.;-) We should search for a respective bug report, or file one.

---

### Post by Eremis on 2011-01-30
yeah well thanks for the help again...

---

