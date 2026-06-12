---
title: "what happened to gst-launch-ext"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Shapierian on 2006-06-22
There used to be a tool that shipped with gstreamer called gst-launch-ext (gst-launch-ext-[version]) that automatically generated a gstreamer pipeline to play a file. I can't find it in dapper. It's not included in any of the packages I've installed and I can't find it on packages.ubuntu.com. Does anyone know where it's gone and/or why it disappeared?

---

### Post by mlind on 2006-06-22
[QUOTE=Shapierian]There used to be a tool that shipped with gstreamer called gst-launch-ext (gst-launch-ext-[version]) that automatically generated a gstreamer pipeline to play a file. I can't find it in dapper. It's not included in any of the packages I've installed and I can't find it on packages.ubuntu.com. Does anyone know where it's gone and/or why it disappeared?[/QUOTE]

gstreamer0.10-tools package contains **gst-launch-0.10**, is this what you're looking for?

---

### Post by Shapierian on 2006-06-22
no gst-launch is used to launch a piple gst-launch-ext should construct one and launch it. For example "gst-launch-0.10 filesrc location=my.ogg ! decodebin ! alsasink" vs "gst-launch-ext-0.10 my.ogg"

---

### Post by mlind on 2006-06-23
[QUOTE=Shapierian]no gst-launch is used to launch a piple gst-launch-ext should construct one and launch it. For example "gst-launch-0.10 filesrc location=my.ogg ! decodebin ! alsasink" vs "gst-launch-ext-0.10 my.ogg"[/QUOTE]

I'm afraid that gst-launch-ext was removed from gst-base-plugins as it's stated on 0.10.1  [release notes]("http://gstreamer.freedesktop.org/releases/gst-plugins-base/0.10.1.html")
You could use *gst-launch0-10 playbin uri=file://path/to/file*

To play myoggfile.ogg from current folder
```

gst-launch-0.10 playbin uri=file://$(pwd)/myoggfile.ogg

```

---

