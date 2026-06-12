---
title: "[SOLVED] kde-window-decorator won't start (Gutsy)"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by odiseo77 on 2007-11-01
Hi people. I installed Ubuntu Gutsy a couple of days after it came out. Then, today, I installed the kubuntu-desktop metapackage in order to install kde since I like to switch from Gnome to KDE sometimes. Then I installed the compiz-kde package through synaptic and proceeded to launch compiz with ***kde-window-decorator &***, but the problem is, it doesn't start, so, I tried with ***kde-window-decorator --replace&*** and it doesn't start either (no error message even; only a PID number). So, what am I doing wrong here?

As a side note, I have a nvidia card with it's driver installed and I have desktop effects enabled in Gnome and they work perfect there, so what could be wrong with KDE?

Thanks in advance.

---

### Post by Biggus on 2007-11-04
Fo shizzle d00d, imha having me them same probs.

Anywun abel to help?

Kthxby.

---

### Post by benerivo on 2007-11-04
What error messages (if any) do you get when you just try to run```
compiz
```

---

### Post by odiseo77 on 2007-11-04
Hi benerivo, this is the error message I get when running compiz from a terminal:

```
vicente@ubuntu-box:~$ compiz&
[1] 4074
vicente@ubuntu-box:~$ Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:01df (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting kde-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

vicente@ubuntu-box:~$
```

So, I guess it's this Xgl not being present error? The weird thing is that compiz works A-OK on Gnome. So, do I have to edit my xorg.conf and add some line, I guess?

Thanks for your answer.

---

### Post by benerivo on 2007-11-04
Look to [this]("http://ubuntuforums.org/showthread.php?t=582207&highlight=xgl+nvidia") thread for similar problems and a possible solution in installing the xserver-xgl package and restarting. I haven't really got any other suggestions at this point, other than you are very probably correct in assuming that it is a problem with Xgl not loading.

---

### Post by odiseo77 on 2007-11-04
Thanks a lot for your help, benerivo! I installed the xserver-xgl package, and added the following section to my xorg.conf:

```
Section "Extensions"
Option  "Composite"     "1"
EndSection
```

Restarted my X session and now compiz is working perfect here in KDE :D

Thank you again!

---

