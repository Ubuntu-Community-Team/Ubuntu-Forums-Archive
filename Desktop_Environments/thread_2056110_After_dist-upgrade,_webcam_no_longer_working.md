---
title: "After dist-upgrade, webcam no longer working"
date: 2012-09-10
forum: Desktop Environments
---

### Post by bobdobbs on 2012-09-10
I'm using KDE and ubuntu 12.04

This morning I ran 'apt-get dist-upgrade'. After a restart, most everything worked. But I no longer have video from my webcam.

The skype video test gives me a black space. I installed Cheese, and that just gives me black as well. The blue led that usually lights up on my microsoft lifecam is dark.

I tried opening the device in VLC, and I got this message:

```
Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/video0'. Check the log for details.
```

How can I recover the use of my camera?

---

### Post by alexmoon on 2013-02-23
Did you ever work this out? I have a similar problem.

---

### Post by bobdobbs on 2013-02-24
Hi.

I must have figured something out, because that configuration is working for me.

I'm afraid I don't remember what my solution was.

What have you tried so far?

---

### Post by alexmoon on 2013-02-24
I didn't mind much in the way of suggestions apart from to try this:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
[or 'skype' in place of 'cheese'].

I got this response:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(cheese:10396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10396): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

** (totem-video-thumbnailer:10405): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:10405): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:10405): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:10405): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:10405): WARNING **: Could not take screenshot: no last video frame
totem-video-thumbnailer couldn't get a picture from 'file:///home/sky/Videos/Webcam/2011-12-20-174120.ogv'

** (cheese:10396): WARNING **: could not generate thumbnail for /home/sky/Videos/Webcam/2011-12-20-174120.ogv (video/ogg)


** (cheese:10396): WARNING **: could not generate thumbnail for /home/sky/Pictures/Webcam/2012-11-30-154257.jpg (image/jpeg)

```

---

