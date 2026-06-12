---
title: "Unity and Compiz don't seem to mix well"
date: 2011-05-01
forum: Desktop Environments
---

### Post by lildigiman on 2011-05-01
I feel these pictures illustrate an issue that should to be addressed:

[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot.png[/IMG]
[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot-1.png[/IMG]
[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot-2(edit).png[/IMG]
[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot-3.png[/IMG]
[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot-4(edit).png[/IMG]
[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot-5.png[/IMG]
[IMG]http://cwmoran.com/images/Unity-Compiz/Screenshot-6.png[/IMG]

What appears to be happening is that when I try to switch desktops it will select the window I have open and try to move it at the same time. As you can see from the images, as soon as I select a viewpoint, compiz's wobbly windows stay in their warped positions while the application is still completely operational. It's quite funny actually, but is also a problem. I'm using Ubuntu 11.04 with Unity and Compiz's wobbly windows enabled. I should note that my Unity Panel on the left side of the screen often freezes and will not auto-hide as I have set it to do, which is an unrelated issue, I believe.

I guess I'm wondering if this is some sort of bug that should be posted and where to post it, whether this is a Unity or Compiz issue.

---

### Post by Blasphemist on 2011-05-01
Ya heck, that's an advanced feature :D

Have you looked at what this shows? 

```
/usr/lib/nux/unity_support_test -p
```

You should see something like this. 

> jim@jim-Satellite-L505:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


---

### Post by lildigiman on 2011-05-01
This is what my output is:

> OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R300
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

---

### Post by Blasphemist on 2011-05-02
Wow, well so much for that. I don't begin to know how to describe this but I suggest you try some searches in this to see if it is an already reported bug. This searches only ubuntu related sites.

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

If you turn off wobbly windows, does it go away? Just asking, not offering that as a solution.

---

### Post by lildigiman on 2011-05-02
Yes, it does in fact go away when wobbly windows is not enabled. Frankly, I find this to be more funny of a bug than annoying. Hehe. I'll try to see if this bug has been reported, thanks.

---

