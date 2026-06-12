---
title: "unity not work"
date: 2010-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by parsibox on 2010-05-15
hi
i install unity but unity not start.
i tried call it from terminal and this is my log :


```
mohsen@mohsen-davari:~$ unity

(unity:3863): liblauncher-WARNING **: Unable to read comment from desktop file /usr/share/applications/nautilus.desktop: Key file does not have key 'Comment'

(unity:3863): GConf-WARNING **: gconf_engine_notify_add: You can't use a GConfEngine that has an active GConfClient wrapper object. Use GConfClient API instead.

(unity:3863): Clutter-WARNING **: The actor 'UnityWidgetsScroller' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityQuicklauncherManager' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityQuicklauncherView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.


(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(unity:3863): Indicator-Sound-DEBUG: At start-up attempting to set the image to audio-volume-muted-panel

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (unity:3863): DEBUG: Connected to Application Indicator Service.
** (unity:3863): DEBUG: Setup proxy signals
** (unity:3863): DEBUG: Connect to them.
** (unity:3863): DEBUG: Request current apps
(unity:3863): Indicator-Sound-DEBUG: about to connect to the signals

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(unity:3863): Indicator-Sound-DEBUG: at the indicator start up and the volume percent returned from dbus method is 34.002686
(unity:3863): Indicator-Sound-DEBUG: at the indicator start up and the MUTE returned from dbus method is 0
(unity:3863): Indicator-Sound-DEBUG: IndicatorSound::fetch_sink_availability_from_dbus -> AVAILABILTY returned from dbus method is 1

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (unity:3863): DEBUG: Updating username label
** (unity:3863): DEBUG: loading avatar from file /home/mohsen/.face

** (unity:3863): WARNING **: /home/mohsen/.face: not found or empty

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(unity:3863): Indicator-Sound-DEBUG: slider parent changed
(unity:3863): Indicator-Sound-DEBUG: Just caught a style change event

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.0/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorItem' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorItem' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorItem' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(unity:3863): Clutter-WARNING **: The actor 'UnityPanelIndicatorsIndicatorItem' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
Allocating 1 x 1 radeon RBO (pitch 16)
Allocating 1 x 1 radeon RBO (pitch 16)
Allocating 1280 x 800 radeon RBO (pitch 1280)

(unity:3863): Clutk-WARNING **: [CheckGLError] GL_INVALID_VALUE error in File ./ctk-render-target.c at line: 285

(unity:3863): Clutk-WARNING **: [CheckGLError] OpenGL Error 1281 in File ./ctk-render-target.c at line: 285 

mohsen@mohsen-davari:~$ 

```

my laptop is dell inspiroon 6400  AND my kernel is 2.6.32-22-generic
my os is ubuntu 10.04

---

