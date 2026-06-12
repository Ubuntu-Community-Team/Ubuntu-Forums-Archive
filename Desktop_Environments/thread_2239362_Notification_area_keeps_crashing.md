---
title: "Notification area keeps crashing"
date: 2014-08-13
forum: Desktop Environments
---

### Post by WB0HYQ on 2014-08-13
Pretty much every time I do anything (like open a window, or do some sort of search for a given app, or re-arrance desktop icons) I get a pop-up message that the Notification Area of the xfce Panel has crashed.  This happens perhaps 20 or 25 times a day and is very annoying.  Is there a solution?  I would really like to find one because this is the only way I can scroll through my desktop backgrounds with Variety, as it does not put an "in operation" icon anywhere on the xfce desktop other than in this notification are.

Bill

---

### Post by WB0HYQ on 2014-08-13
Here is a 100% guaranteed way to crash the Notification area:

Go to the Ubuntu Software Center and choose ANY piece of sotware.  Use the "Info" button and see if it has a Screenshot of the software.  If it does, click on it to give you the pop-up screen for that software.  When you hit the "Close" button, the Notification Area immediately gives you the failure notification and you have to restart it again.


EDIT:  ANother thing that crashes the Notification Area is editing ANY file using either 'gedit' or 'notepad'.  When you open the file it crashes and when you close the file it crashes again.
Surely, there must be SOMEONE out there who has fixed this problem.


Bill

---

### Post by Toz on 2014-08-13
Which version of *buntu are you using? Which version of Xfce?

You can try this to see if you get some more helpful information. From a terminal window, kill xfce4-panel then run it in debug mode:
```
xfce4-panel -q && PANEL_DEBUG=1 xfce4-panel
```
..then make the crash happen again and look at the debug info that is being printed out in the terminal window.

If the first crash notification is the apport crash notification, the associated crash log can be found in /var/crash.

Feel free to post back the information from above.

Note: To get xfce4-panel running normally again, press Ctrl+c in the terminal window to kill the process, then Alt+F2 and run "xfce4-panel".

---

### Post by WB0HYQ on 2014-08-13
I'm running Ubuntu 14.04LTS. The version of xfce is 4.10.

Let me give your information a try and I'll get back to you.

Bill

---

### Post by WB0HYQ on 2014-08-13
Okay.  I've done what you asked and here's what I get.  I get a whole lot of lines in the terminal and then it pauses.  I cause a crash, and the terminal window gets the error dumped and the the same lines flash by again, waiting for another crash.  Here's the output:

```

init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-datetime main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-session respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-datetime respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth respawning too fast, stopped

****** HERE IS WHERE THE TERMINAL PAUSES - WAITING
****** THEN THE RRROR HITS

(wrapper-2.0:14204): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=14552, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-application main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-datetime respawning too fast, stopped
init: indicator-sound respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-session respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped


```

What I did to cause the error was double-click a TXT file for gedit to open.  That caused the crash.

Bill

---

### Post by Toz on 2014-08-13
> (wrapper-2.0:14204): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=14552, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue

Indicator-31 is the problem - next we need to figure out which one it is. Run the panel debug again, and when it crashes you will see something like above again. The line:
> xfce4-panel(external): indicator-31: child spawned; pid=14552, argc=8
...will appear again but the pid will be different. With that new pid, run:
```
ps -ef | grep NEW_PID
```
...and replace NEW_PID with the pid that is displayed.

Can you also post back the contents of ~/.cache/xfce4-indicator-plugin.log (right after a crash) and well as the results of:
```
ls -l ~/.cache/upstart
```

---

### Post by WB0HYQ on 2014-08-13
Now I am unable to kill xfce4-panel.  The instant I issue a kill -9 <PID>  for xfce4-panel, another panel immediately starts up again.

Bill

---

### Post by Toz on 2014-08-13
> **WB0HYQ said:**
> Now I am unable to kill xfce4-panel.  The instant I issue a kill -9 <PID>  for xfce4-panel, another panel immediately starts up again.

Bill

Use the "-q" (quit) parameter. This command will work:
```
xfce4-panel -q && PANEL_DEBUG=1 xfce4-panel
```

---

### Post by WB0HYQ on 2014-08-13
That is the EXACT command I am using -- it will not quit.  It blinks and immediate a new panel restarts with a new PID.  Each time I kill it, the new one has a new PID.

Bill

---

### Post by Toz on 2014-08-13
Try them one at a time. 

```
xfce4-panel -q
```
...should stop all instances of xfce4-panel from running. If not, try also:
```
killall -9 xfce4-panel
```

Once its stopped, run it in debug mode:
```
PANEL_DEBUG=1 xfce4-panel
```

---

### Post by WB0HYQ on 2014-08-13
Well, here are some more results:

There were 5 errors in here after I finally got the 'normal' panel killed and restarted in debug

```

bill@bill-UBU:~/Desktop$ xfce4-panel -q && PANEL_DEBUG=1 xfce4-panel
xfce4-panel(main): version 4.11.0 on gtk+ 2.24.23 (2.24.22), glib 2.40.0 (2.39.90)
xfce4-panel(module-factory): reading /usr/share/xfce4/panel/plugins
xfce4-panel(module-factory): reading /usr/share/xfce4/panel-plugins
xfce4-panel(application): found window manager after 1 tries
xfce4-panel(base-window): 0x7f023500a120: rgba colormap=0x7f023500c880, compositing=true
xfce4-panel(base-window): 0x7f023500a120: rgba colormap=0x7f023500c880, compositing=true
xfce4-panel(display-layout): 0x7f023500a120: display=:0.0{comp=true}, screen-0[0x7f0234fc31c0]=[1600,900] (VGA-0=[0,0;1600,900])
xfce4-panel(positioning): 0x7f023500a120: screen=0x7f0234fc31c0, monitors=1, output-name=(null), span-monitors=false, base=800,15
xfce4-panel(positioning): 0x7f023500a120: working-area: screen=0x7f0234fc31c0, x=0, y=0, w=1600, h=900
xfce4-panel(struts): 0x7f023500a120: top=31, start_x=0, end_x=1599
xfce4-panel(module): new item (type=object-type, name=applicationsmenu, id=1)
xfce4-panel(module): new item (type=object-type, name=tasklist, id=3)
xfce4-panel(module): new item (type=object-type, name=separator, id=15)
xfce4-panel(external): register dbus path /org/xfce/Panel/Wrapper/16
xfce4-panel(module): new item (type=external-wrapper, name=screenshooter, id=16)
xfce4-panel(external): screenshooter-16: child spawned; pid=1502, argc=8
xfce4-panel(module): new item (type=object-type, name=separator, id=18)
xfce4-panel(module): new item (type=object-type, name=pager, id=4)
xfce4-panel(module): new item (type=object-type, name=clock, id=5)
xfce4-panel(module): new item (type=object-type, name=separator, id=21)
xfce4-panel(external): register dbus path /org/xfce/Panel/Wrapper/31
xfce4-panel(module): new item (type=external-wrapper, name=indicator, id=31)
xfce4-panel(external): indicator-31: child spawned; pid=1504, argc=8
xfce4-panel(module): new item (type=object-type, name=separator, id=20)
xfce4-panel(external): register dbus path /org/xfce/Panel/Wrapper/30
xfce4-panel(module): new item (type=external-wrapper, name=systray, id=30)
xfce4-panel(external): systray-30: child spawned; pid=1506, argc=8
xfce4-panel(module): new item (type=object-type, name=separator, id=19)
xfce4-panel(base-window): 0x7f023500a3a0: rgba colormap=0x7f023500c880, compositing=true
xfce4-panel(base-window): 0x7f023500a3a0: rgba colormap=0x7f023500c880, compositing=true
xfce4-panel(base-window): 0x7f02350b3050: rgba colormap=0x7f023500c880, compositing=true
xfce4-panel(display-layout): 0x7f023500a3a0: display=:0.0{comp=true}, screen-0[0x7f0234fc31c0]=[1600,900] (VGA-0=[0,0;1600,900])
xfce4-panel(positioning): 0x7f023500a3a0: screen=0x7f0234fc31c0, monitors=1, output-name=(null), span-monitors=false, base=0,0
xfce4-panel(positioning): 0x7f023500a3a0: working-area: screen=0x7f0234fc31c0, x=0, y=0, w=1600, h=900
xfce4-panel(module): new item (type=object-type, name=showdesktop, id=7)
xfce4-panel(module): new item (type=object-type, name=separator, id=8)
xfce4-panel(module): new item (type=object-type, name=launcher, id=9)

(xfce4-panel:1499): liblauncher-CRITICAL **: Failed to start file monitor: Unable to find default local directory monitor type
xfce4-panel(module): new item (type=object-type, name=launcher, id=10)

(xfce4-panel:1499): liblauncher-CRITICAL **: Failed to start file monitor: Unable to find default local directory monitor type
xfce4-panel(module): new item (type=object-type, name=launcher, id=11)

(xfce4-panel:1499): liblauncher-CRITICAL **: Failed to start file monitor: Unable to find default local directory monitor type
xfce4-panel(module): new item (type=object-type, name=launcher, id=12)

(xfce4-panel:1499): liblauncher-CRITICAL **: Failed to start file monitor: Unable to find default local directory monitor type
xfce4-panel(module): new item (type=object-type, name=separator, id=13)
xfce4-panel(module): new item (type=object-type, name=directorymenu, id=14)
xfce4-panel(external): screenshooter-16: child is embedded; 6 properties in queue
xfce4-panel(systray): registered manager on screen 0
xfce4-panel(external): systray-30: child is embedded; 6 properties in queue
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-application main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-datetime main process ended, respawning
init: indicator-session respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped

(wrapper-2.0:1504): Gtk-CRITICAL **: gtk_label_set_text_with_mnemonic: assertion 'str != NULL' failed

(wrapper-2.0:1504): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel-Message: Plugin indicator-31 has been automatically restarted after crash.
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=1813, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-datetime respawning too fast, stopped
init: indicator-session respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth respawning too fast, stopped

(wrapper-2.0:1813): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=2423, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-session respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-datetime respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped

(wrapper-2.0:2423): Indicator-Appmenu-CRITICAL **: menus_destroyed: assertion 'wm != NULL' failed

(wrapper-2.0:2423): Gtk-CRITICAL **: gtk_label_set_text_with_mnemonic: assertion 'str != NULL' failed

(wrapper-2.0:2423): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=2655, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-session respawning too fast, stopped
init: indicator-sound respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-datetime respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth respawning too fast, stopped

(wrapper-2.0:2655): Indicator-Appmenu-CRITICAL **: menus_destroyed: assertion 'wm != NULL' failed

(wrapper-2.0:2655): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=2901, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-session main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-datetime respawning too fast, stopped
init: indicator-session respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped
init: indicator-power respawning too fast, stopped

(wrapper-2.0:2901): Indicator-Appmenu-CRITICAL **: menus_destroyed: assertion 'wm != NULL' failed

(wrapper-2.0:2901): Gtk-CRITICAL **: gtk_label_set_text_with_mnemonic: assertion 'str != NULL' failed

(wrapper-2.0:2901): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=3124, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-session main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-datetime respawning too fast, stopped
init: indicator-session respawning too fast, stopped
init: indicator-sound main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped

(wrapper-2.0:3124): Gtk-CRITICAL **: gtk_widget_realize: assertion 'widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.10.8/./gtk/gtkwidget.c:11538:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))
xfce4-panel(external): indicator-31: child is unembedded
xfce4-panel(external): indicator-31: child exited with status 134
xfce4-panel(external): indicator-31: scheduled a respawn of the child
xfce4-panel(external): indicator-31: child spawned; pid=3335, argc=8
xfce4-panel(external): indicator-31: child is embedded; 6 properties in queue
init:/home/bill/.config/upstart: Unable to watch configuration directory: Too many open files
init:/usr/share/upstart/sessions: Unable to watch configuration directory: Too many open files
init: indicator-power main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-session main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime main process ended, respawning
init: indicator-messages respawning too fast, stopped
init: indicator-session main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-datetime respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-session respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped


```

I have also attached the xfce4-indicator-plugin.log file

EDIT: Forgot to add this:

```


bill@bill-UBU:~/Desktop$ ps -ef | grep 3335
bill      8055  7775  0 22:42 pts/6    00:00:00 grep --color=auto 3335
bill@bill-UBU:~/Desktop$ 


```

Bill

---

### Post by Toz on 2014-08-13
And:
```
ps -ef | grep 3335
```

---

### Post by WB0HYQ on 2014-08-13
Added as an EDIT in my last post.  Sorry

Bill

---

### Post by Toz on 2014-08-13
Can you try quitting the Variety plugin and see if it still crashes?

---

### Post by WB0HYQ on 2014-08-13
Yep.  Still crashes big time.

Bill

---

### Post by Toz on 2014-08-13
Lets try something different. Lets try clearing your sessions cache in case there is something buggy in there. Go to Settings Manager >> Session and Startup >> Sessions tab and "Clear saved sessions". Log out and back in again to reload the session. See if you can make it crash again.

---

### Post by Toz on 2014-08-13
Just reviewing your logs and I see that you have indicator-appmenu loading. I don't believe this indicator works with xfce4-panel. See: [https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606"). Follow the instructions in the 7th post of that bug report to disable it.

---

### Post by WB0HYQ on 2014-08-13
Great.  Now I can't even log out.  I get a pop-up asking:

Are you sure you want to close all programs and log out?
Some software updates won't be applied until the computer next restarts

I click Log Out and nothing happens.

I have to get up early in the morning (0715), Toz.  I greatly appreciate your help, and I will be back around 1000 for another whack at this.  I am really intrigued as to WHY I can't log out.

Bill

---

### Post by WB0HYQ on 2014-08-13
Toz:

Re your last post.  I finally gave up and powered down the computer and restarted it.  I have a feeling that clearing the sessions cache was NOT a good idea.  I have a completely messed up desktop with hardly anything on the top panel - especially anything allowing me to choose keyboards, log out, check my network, etc, etc.  The icons are scattered all over my desktop and when I try to arrange them, they will only fit into orange squares about three inches on a side.  I had them just the way I liked them and now cannot even SEE all of them.

So, I've decided that xfce4 is just too finnicky for me and gone back to my trusty (no joke intended) Ubuntu Desktop for the time being.

I may try again some time if I can find out if this bug has been fixed, but probably not if all the hassle just isn't worth it.

Going to bed right now.

Bill

---

### Post by WB0HYQ on 2014-08-14
I am back again.  Started an xfce session and the crashing is still present.  What bothers me more is that a number of items were gone from the upper panel and I had to put them back into it.  Of supreme importance is the icons -- they have managed to become huge and the orange squares (used to move them around) are now around two inches on a side and I am unable to make that smaller despite how much I reduce the size of the icons themselves.

What I mean is that the icons are now around a quarter-inch in size, but the orange squares remain two inches on a side.  This reduces the amount of icons I can get on the screen - which is NOT all of the programs I like to run.

My current screen resolution is 1600x900, using an NVIDIA driver so that isn't the problem.

In summary: crashing of the Notification area and icon placement are really crushing my interest in the xfce desktop.

Bill

---

### Post by WB0HYQ on 2014-08-14
Aha!  There IS a bug on this problem:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606](https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1311606)

I followed the advice to hide the Notification Area as a workaround and it seems to work.  At least, I can't cause a crash by creating/editing/closing a TXT file.  Other random crashes seem to have stopped also.

My original reason for this whole thread was to get my access to Variety to allow me to change wallpaper by using the various context controls offered by Variety - which I couldn't because the Notification Area kept crashing.

Since this is not really "solved" (because of the open bug report), should I mark this thread solved or not?  I am also going to create a new thread on the big orange boxes for icon placement.

Bill

---

