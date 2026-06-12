---
title: "AWN Curves Not Appearing"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by Abu_Dayya on 2008-01-19
Hi all
I installed AWN Curves as its shown in the HowTo. After the install, I opened AWN Manager to change the 3D Look to Curves and the bar did change its look but not like what I saw in the pictures in the HowTo thread. Then I rebooted the PC and now nothing. AWN isn't starting at all. I tried running it again and running the AWN Manager again, but still nothing. I can't see AWN at all.

This is what I get when I run 'avant-window-navigator' in a terminal

```

yousef@YousefPC:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/awnterm.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
Awn Terminal applet alloc

(awn-applet-activation:6296): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1715: handler `30' of instance `0x80bc000' is not blocked
APPLET : /usr/lib/awn/applets/PyClock.desktop
APPLET : /usr/lib/awn/applets/PySwitcher.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop

(awn-applet-activation:6294): Gdk-WARNING **: GdkWindow 0x4600022 unexpectedly destroyed

(awn-applet-activation:6294): Gdk-WARNING **: GdkWindow 0x4600004 unexpectedly destroyed
Segmentation fault (core dumped)
yousef@YousefPC:~$ /usr/lib/awn/applets/showdesktop/showdesktop.py:61: GtkWarning: GdkWindow 0x4a00022 unexpectedly destroyed
  gtk.main ()
/usr/lib/awn/applets/showdesktop/showdesktop.py:61: GtkWarning: GdkWindow 0x4a00004 unexpectedly destroyed
  gtk.main ()

(awn-applet-activation:6296): Gdk-WARNING **: GdkWindow 0x4400022 unexpectedly destroyed

(awn-applet-activation:6296): Gdk-WARNING **: GdkWindow 0x4400004 unexpectedly destroyed
The program 'showdesktop.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 279 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'awn-applet-activation' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 219 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'awn-applet-activation' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 197 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
<gtk.gdk.Pixbuf object at 0x82c0cac (GdkPixbuf at 0x8375e80)>
/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py:32: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  self.ObjSwitcher.DrawSwitcher(self)
/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py:32: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  self.ObjSwitcher.DrawSwitcher(self)
/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py:32: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.ObjSwitcher.DrawSwitcher(self)
/usr/lib/awn/applets/PyClock/PyClock.py:185: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  self.SetIconFromSurface(applet, surface)
/usr/lib/awn/applets/PyClock/PyClock.py:185: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  self.SetIconFromSurface(applet, surface)
/usr/lib/awn/applets/PyClock/PyClock.py:185: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.SetIconFromSurface(applet, surface)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
<gtk.gdk.Pixbuf object at 0x82c41bc (GdkPixbuf at 0x838aec0)>
/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py:19: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  return ObjSwitcher.DrawSwitcher(applet)
/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py:19: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  return ObjSwitcher.DrawSwitcher(applet)
/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py:19: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  return ObjSwitcher.DrawSwitcher(applet)
yousef@YousefPC:~$ 
yousef@YousefPC:~$ 



```

Can anyone please help?

---

### Post by Abu_Dayya on 2008-01-19
Anyone??

---

### Post by Abu_Dayya on 2008-01-19
One more time... bump

---

### Post by Abu_Dayya on 2008-01-20
Come on now guys!

---

### Post by Abu_Dayya on 2008-01-21
another bump

---

### Post by dustman on 2008-01-27
i get a similar message: ```
dustman@dustman-laptop:~/awn-curves$ avant-window-navigator
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
Segmentation fault (core dumped)
dustman@dustman-laptop:~/awn-curves$ /home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

```
dunno what the problem might be :|. It was working before trying to install awn curves


Radu

[EDIT] fixed it!!! [https://answers.launchpad.net/awn/+question/16840](https://answers.launchpad.net/awn/+question/16840) - follow the instructions from here, then remove your compiled version of avant-window-navigator:
1.go to where you downloaded the sources (that "awn-curves" folder)
2. type```
sudo make uninstall
```
3. go to synaptics package manager and remove all the remains of "awn" or "avant" (there should be only 2 packages or so)
4. reinstall "awn-curves" using nikoPSK's tutorial (complete all the steps)
5. that's it...i've done exactly the same steps and i got it working...hope to solve your problem too ;)

---

### Post by nikoPSK on 2008-01-27
> **dustman said:**
> i get a similar message: ```
dustman@dustman-laptop:~/awn-curves$ avant-window-navigator
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
Segmentation fault (core dumped)
dustman@dustman-laptop:~/awn-curves$ /home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

```dunno what the problem might be :|. It was working before trying to install awn curves


Radu

[EDIT] fixed it!!! [https://answers.launchpad.net/awn/+question/16840](https://answers.launchpad.net/awn/+question/16840) - follow the instructions from here, then remove your compiled version of avant-window-navigator:
1.go to where you downloaded the sources (that "awn-curves" folder)
2. type```
sudo make uninstall
```3. go to synaptics package manager and remove all the remains of "awn" or "avant" (there should be only 2 packages or so)
4. reinstall "awn-curves" using nikoPSK's tutorial (complete all the steps)
5. that's it...i've done exactly the same steps and i got it working...hope to solve your problem too ;)

thank you very much ;), my guide works under gutsy, and if you do it any other way, unfortunately it won't work. :|

---

### Post by dustman on 2008-01-27
well i did it as you stated (i mean i followed all the instructions) but i dunno why something got mixed up along the way :). anyways, the important thing is that i got it working i guess :D

---

### Post by nikoPSK on 2008-01-27
Well, I hope you enjoy awn, I could never live with a dock full time... :(

---

