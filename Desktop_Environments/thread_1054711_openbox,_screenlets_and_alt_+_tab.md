---
title: "openbox, screenlets and alt + tab"
date: 2009-01-30
forum: Desktop Environments
---

### Post by timroberts on 2009-01-30
I just got openbox up and running and i have some screenlets on my desktop. Is there any way to remove said screenlets from the alt + tab menu? They kind of fill it up and take up a large amount of space (i'm running like 4 of them) and it gets pretty annoying.

---

### Post by urukrama on 2009-01-30
You can set specific applications to skip the taskbar and alt-tab window switching in your rc.xml. See [the documentation]("http://icculus.org/openbox/index.php/Help:Applications") for more info.

The setting you'll want to specify is <skip_taskbar>yes</skip_taskbar>, for example:

> <application class="MPlayer">
    <desktop>all</desktop>
<skip_taskbar>yes</skip_taskbar>
  </application>

With these settings, MPlayer will not be shown in the taskbar or alt-tab dialog. Don't forget to reconfigure Openbox after you add those lines to your rc.xml.

---

### Post by timroberts on 2009-01-30
Ok so i copied the code you pasted, and put that into my rc.xml file, edited it for each screenlet, however the screenlets still show in the dialog. Does it have something to do with them being run from screenlets? i'm not too clear on whether they're actual programs or whether they're widgets. This is what my rc.xml file code looks like:

<application class="SysmonitorScreenlet.py">
<desktop>all</desktop>
<skip_taskbar>yes</skip_taskbar>
</application> 
<application class="ClearWeatherScreenlet.py">
<desktop>all</desktop>
<skip_taskbar>yes</skip_taskbar>
</application>

---

### Post by timroberts on 2009-01-30
i also reconfigured.

---

### Post by urukrama on 2009-01-30
You'll need to use the proper application class. To find that out, open a terminal and type *xprop WM_CLASS*. Click on the application you want to configure. Using xfce4-terminal as an example, you'll get something like this: 

> WM_CLASS(STRING) = "xfce4-terminal", "Xfce4-terminal"

The first string (xfce4-terminal) is the name, the second string (Xfce4-terminal) is the application class. See the documentation page I linked to earlier for more details.

---

### Post by timroberts on 2009-01-31
So i did some digging around in the documentation, and did everything that made sense to do. As a result, my rc.xml file now has this:

<application name="SysmonitorScreenlet.py"  class="SysmonitorScreenlet.py" type="_NET_WM_WINDOW_TYPE_TOOLBAR" >
<desktop>all</desktop>
<skip_taskbar>yes</skip_taskbar>
</application> 

<application name="ClearWeatherScreenlet.py" class="ClearWeatherScreenlet.py" type="_NET_WM_WINDOW_TYPE_TOOLBAR">
<desktop>all</desktop>
<skip_taskbar>yes</skip_taskbar>
</application> 

and still a no-go. Any more ideas? i really appreciate the help you've given me thus far.

---

