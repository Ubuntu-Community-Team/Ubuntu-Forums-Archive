---
title: "Compiz and Kubuntu (Feisty)"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by SZF2001 on 2007-06-29
OK, so I install my nVidia driver via Ubuntu repositories on my Kubuntu box.

Then I try Beryl. Which didn't work out...

But I remember I like Compiz better anyway, and it usually uses Xorg and free open source drivers...

But it's still not working.

So, how do I change my settings so my nVidia driver is actually being used so I can use these fancy programs? If you haven't noticed, I'm using Kubuntu (Feisty) from the title. I don't think there is a Restricted Drivers Manager like in the default Ubuntu... or is there?

---

### Post by hyperair on 2007-06-29
There isn't. You can use these commands:

```

sudo apt-get install nvidia-glx #(if you haven't installed it already)
sudo nvidia-xconfig --enable --add-argb-glx-visuals

```

Then restart your X server (Ctrl+Alt+Backspace)

---

### Post by SZF2001 on 2007-07-03
So, will nVidia drivers stay on, even after I turn off my computer, with that command?

Last time I tried something else and I got the White Screen of Death, ended up having to do a fresh install...

EDIT: BTW, I get this message when I try:

```
~$ sudo nvidia-xconfig --enable --add-argb-glx-visuals
nvidia-xconfig: unrecognized option: "--enable"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.
```

And when I go to the Help menu, there is no "--enable" option.

```
$ sudo nvidia-xconfig --help

nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST
2006
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 NVIDIA Corporation.


  In its normal operation, nvidia-xconfig finds the system X configuration file
  (or generates a new X configuration if it cannot find the system file), makes
  sure the configuration is usable by the NVIDIA X driver, applies any updates
  requested on the commandline, and writes the new configuration to file.

  Please see the NVIDIA README for a description of NVIDIA X configuration file
  options.


nvidia-xconfig [options]

  -c XCONFIG, --xconfig=XCONFIG
      Use XCONFIG as the input X config file; if this option is not specified,
      then the same search path used by the X server will be used to find the X
      configuration file.

  -o OUTPUT-XCONFIG, --output-xconfig=OUTPUT-XCONFIG
      Use OUTPUT-XCONFIG as the output X configuration file; if this option is
      not specified, then the input X configuration filename will also be used
      as the output X configuration filename.

  -s, --silent
      Run silently; no messages will be printed to stdout, except for warning
      and error messages to stderr.

  -t, --tree
      Read the X configuration file, print to stdout the X configuration data
      in a tree format, and exit.

  -v, --version
      Print the nvidia-xconfig version and exit.

  -h, --help
      Print usage information for the common commandline options and exit.

  -A, --advanced-help
      Print usage information for the common commandline options as well as the
      advanced options, and then exit.


```

---

### Post by hyperair on 2007-07-03
Ah sorry, it's ```
sudo nvidia-xconfig --add-argb-glx-visuals
```. No --enable.

---

### Post by SZF2001 on 2007-07-04
I did the other option in the Help menu.

Didn't even get a white screen. Just a terminal...

Tried to fix xorg.conf ... Well, now I'm back on GNOME. Sorry.

---

