---
title: "Configuring Nvidia: How to enable 'HW cursor'"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Ric95 on 2006-08-04
Some of us using Blender have a problem with the screen draw around the cursor. Elsewhere I've read the solution is to enable HW curosr in an 'XF86.config file. Where can I find these configurations in Dapper?

---

### Post by msandersen on 2006-08-04
The config file is at /etc/X11/xorg.conf
Ubuntu now use the newer x.org, hence the different name of the file.

Don't know about the specific config option, it would depend on your graphics card, eg nVidia. You may want to mention your graphics card model.
The option would go in the "device" section.
Section "Device"

---

### Post by Ric95 on 2006-08-05
At the moment I'm using a TNT2. ( I also have ATI x200 integrated, but NV is more compatible with some software I need)
And Thanks, I now notice the mouse configurations are in there. I'll need to research how to work with that.

---

### Post by RawMustard on 2006-08-05
For nvidia ```
Option "HWcursor" "1"
```
Put that in device section for your gfx card.

---

### Post by Ric95 on 2006-08-05
Thanks :)

---

