---
title: "Workspace Margins Limit (too small)       :("
date: 2009-02-10
forum: Desktop Environments
---

### Post by shadow_code on 2009-02-10
Hi,

I had this great idea of using workspace margins for pseudo window positioning. Basically, by increasing the right margin by a large amount (say 1/2 screen width), maximized windows would auto-position themselves to the left of the screen.

The problem is Xfce puts a limit on how big the margins can be (1/4 of the resolution).

I found the following code in [margins.c](http://svn.xfce.org/svn/xfce/xfwm4/tags/xfce_4_4_2/mcs-plugin/margins.c):

```
wmax = gdk_screen_width () / 4;
hmax = gdk_screen_height () / 4;
```

Though I think this might only be for the settings GUI. I'm not sure if the limit is enforced anywhere else? I'm guessing it is since I've tried overriding the settings in /home/user/.config/xfce4/mcs_settings/margins.xml to no avail...

Is there an easy way of doing this or would I have to modify and compile Xfce myself?

It would be great if this limit was increased for future versions of Xfce. (at least I'd find it great  :D)

Thanks

---

