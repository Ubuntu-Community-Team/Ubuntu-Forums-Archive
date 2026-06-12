---
title: "Compiz Crashing on GDM after --replace"
date: 2018-04-27
forum: Desktop Environments
---

### Post by apanpie on 2018-04-27
Compiz crashes every time in GDM I manually apply changes by:
```
compiz --replace
```
**What happens:**
[LIST]
[*]**Title Bars** **disappear**
[*]Window Overlay Glitches after a window is closed
[*]The **Top Taskbar** (Time, Power/Login Buttons, Date, Applications, Extensions etc.) **disappears too**.
[/LIST]
**What I do after:**[INDENT]I just enter into **tty** mode and restart the GDM service. But then, it's like CompizSettings never applied.[/INDENT]

So Compiz currently is completely useless, since if I apply the changes, it crashes instantly.

Some **Specs**:

[LIST]
[*]NVIDIA binary driver - version 384.111 from Nvidia-384 (proprietary, tested)
[*]GTX 650
[/LIST]
Anything else you want you can ask me. Not sure what to provide, since I didn't see anything useful in the System Logs.

[B]UPDATE: - ERRORS
[/B]- compizconfig - Error: dlopen: /usr/lib/x86_64-linux-gnu/compizconfig/backends/libgsettings.so: cannot open shared object file: No such file or directory
- compizconfig - Warning: unable to open backend gsettings, falling back to ini
- /bin/sh: 1: /usr/bin/gtk-window-decorator: not found - Window Decorator setting from Compiz

---

### Post by #&amp;thj^% on 2018-04-27
this is also neeed to help you:
```
lsb_release -a
```
And some specs on your video card
```
inxi -G
```
You may have to install inxi via:
```
sudo apt install inxi
```
And one more while we are at it:
```
echo $DESKTOP_SESSION
```

---

### Post by apanpie on 2018-04-27
Output:
```
lsb_release -a && inxi -G && echo $DESKTOP_SESSIONNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
Graphics:  Card: NVIDIA GK107 [GeForce GTX 650]
           Display Server: X.Org 1.19.5 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1600x900@59.98hz, 1920x1080@74.97hz
           GLX Renderer: GeForce GTX 650/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 384.111
gnome

```

Also, I updated my initial post! Thanks.
[B]
UPDATE: 
[/B]I went to **Window-Decorator **in **Compiz **and changed the "Command" attribute from 
```
/usr/bin/gtk-window-decorator
```
to 
```
compiz-decorator
```
Then it told me that 
```
metacity was not found
```
Installed metacity by 
```
sudo apt-get install metacity -y
``` 
and then **Title Bars** appeared. Although the whole system is still glitched, the Title bars in Terminals look ugly ... and I want GTK-WINDOW-DECORATOR, the one I've been using till now and it doesn't find it in Compiz.

---

### Post by #&amp;thj^% on 2018-04-27
Hmm?
try this it might give me or someone else some clues here:
```
compiz --debug --replace &
```
Please use pastebin for the out put found here:[https://paste.ubuntu.com](https://paste.ubuntu.com)
And give us the link from paste bin from that output back here in your thread.

---

### Post by apanpie on 2018-04-27
Here is the debug info from your instruction:
[https://paste.ubuntu.com/p/tb8kgS4MD9/](https://paste.ubuntu.com/p/tb8kgS4MD9/)

But I changed it back to "/usr/bin/gtk-window-decorator" in order to debug this.

**UPDATE:**
Alright, so I'm really confused. I've tried placing as a **command **in **Window-Decorator** the GnomeShell.
```
/usr/bin/gnome-shell
``` 
and what it said was 
```
Window manager warning: Display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.org.gnome.Shell already exists on bus and --replace not specified
Segmentation fault (core dumped)

```
So, the only Window-Decorator that exists in my system, can't run because it already "exists in the bus"? What is this supposed to mean? I mean I'm first running Metacity on purpose in order for the Gnome-Shell to be removed from the bus, but it still remains on the bus for some reason.

I'm really confused on how this whole thing works. **gtk****-window-decorator **doesn't even exist, I can't run **gnome-shell** because it's "already on the bus" and ** metacity** not only glitches, but it looks ugly too.

---

### Post by apanpie on 2018-04-27
Do not bother. "Obviously", you can't use **Compiz** along with **Gnome-Shell**. You can only use **Gnome-Tweak-Tool ** with it. That's why I couldn't find anything in google about my issue. Although, I saw only one person saying that you can't use Gnome-Shell with Compiz. Learned something today :P

---

