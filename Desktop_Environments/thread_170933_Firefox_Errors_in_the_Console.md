---
title: "Firefox: Errors in the Console"
date: 2006-05-05
forum: Desktop Environments
---

### Post by charlie. on 2006-05-05
When I run firefox through the console and observe the stdout errors that are printed, I see long lists of errors beginning with: "(firefox-bin:6847): GLib-GObject-CRITICAL" and ending with "pixbuf != NULL' failed"

They all look similar to this one, with slight variations:

```
(firefox-bin:6847): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed
```

I am sure that this is not normal. I fear that this is causing the performance problem that I have with pages with moving content, such as the Blogger home page.

I am running the Firefox 1.5.0.3 binaries from Mozilla's web page. I have installed the prerequisites libgtk2.0-0 and gtk2-engines-gtk-qt manually - because I never installed the firefox package with APT.

Has anyone else observed this? Any suggestions would be welcome.

---

### Post by kingmonkey on 2006-05-05
there always seems to be errors in console.

---

### Post by louis_nichols on 2006-05-05
I'd agree with kingmonkey here. I don't know what they mean, for the most part, but never seemed to cause any real issues.

it doesn't happen only with Firefox, either. You should try opening kcontrol from the command line! loool

---

### Post by charlie. on 2006-05-06
Firefox does appear to work perfectly.

Whenever I run ANY KDE application in the console, I get this output:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Extension:    148 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Extension:    148 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
```

I have no idea what this is about. I am trying to do some Qt 4 development on my system and this output is incredibly annoying, because I run all my applications in the console!

---

### Post by louis_nichols on 2006-05-06
sorry, but that's the way it is. I guess it's one of those cases where "ignorance is a bliss", i.e. not running apps from console and not knowing about such erors keeps you happy. :))

---

### Post by katiad on 2006-05-10
I posted about this problem ages ago. No response. No one has a clue, it seems. I don't know if it hurts anything in Firefox. I know the version I have crashes an awful lot... but I don't think it's related to those errors, probably. But aside from frequent crashing, I haven't had any problems with Firefox despite those errors.

---

### Post by amm2 on 2006-05-18
In my /etc/X11/xorg.conf I found mention of "wacom" stylus/eraser/cursor devices.
I took them out and got rid of those "device 168" messages.
I have no idea why my config files have these wacom devices in there, when my computer does not have any.
Maybe one of the Ubuntu maintainers has these weird devices and the rest of the world has to suffer ?
Let me know if taking them off fixes the problem.
I would really like to know why these are enabled by default though.

---

### Post by schmidty on 2006-05-20
I am having the crashing problem and lockup with Gnome and FF constantly. How can I error log when running Firefox? I thought I could do this from a terminal but it doesn't seem to work;

 firefox & 2> errors.log

How do I output the errors to a separate file and is there anyway to track the programs execution step-by-step under Linux?
I'm going to pull all my extensions and see if that solves the prob.

Schmidty

---

