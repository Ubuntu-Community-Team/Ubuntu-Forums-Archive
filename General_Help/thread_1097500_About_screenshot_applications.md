---
title: "About screenshot applications"
date: 2009-03-16
forum: General Help
---

### Post by artspace on 2009-03-16
Is there any screen capturing program (for Ubuntu) which can:

1. capture the application specific cursors, such as the cross cursors or two-head arrows in Blender 3D?

2. keep capturing specified area (fixed area) over and over?

3. capture while mouse is still pressed and held?

I've tried several Ubuntu native programs (such as the default "Take Screenshot" and the terminal based Imagemagick... etc.), and the Windows programs (i.e. EasyCaptre, ScreenHunter... etc.) via Wine, but none of them can do the above jobs.

Can anyone help? Any suggestion is appreciated! 

ps. My system is running Ubuntu 8.10.

---

### Post by namaku0 on 2009-03-16
Shutter is the best I can find: [http://shutter-project.org](http://shutter-project.org)

If it doesn't satisfy your needs you may want to record your
desktop instead. Use something like recordMyDesktop or Istanbul:
[http://recordmydesktop.sourceforge.net/](http://recordmydesktop.sourceforge.net/)
[http://live.gnome.org/Istanbul](http://live.gnome.org/Istanbul)

Play the recorded desktop with Totem and use its screenshot
feature (Edit > Take Screenshot...) to take only the pictures
you need.

---

### Post by moma on 2009-03-16
Hello,

I want to mension Gscreendump. It's very young but hugely promising piece of software (by its design!). 
Read: [http://ubuntuforums.org/showthread.php?t=1096860](http://ubuntuforums.org/showthread.php?t=1096860)

BTW: Capturing an application's cursor (mouse pointer) seems to be difficult in Xorg/Xlib.
Currently, Gscreendump takes a screenshot and replaces the cursor(image) with standard [GDK_LEFT_PTR]("http://library.gnome.org/devel/gdk/stable/gdk-Cursors.html") cursor.

---

### Post by binbash on 2009-03-16
Shutter does this : 

[http://www.ubuntu-inside.me/2009/03/shutter-featureful-scroonshot-tool.html](http://www.ubuntu-inside.me/2009/03/shutter-featureful-scroonshot-tool.html)

---

### Post by artspace on 2009-03-16
> **moma said:**
> Hello,

I want to mension Gscreendump. It's very young but hugely promising piece of software (by its design!). 
Read: [http://ubuntuforums.org/showthread.php?t=1096860](http://ubuntuforums.org/showthread.php?t=1096860)

BTW: Capturing an application's cursor (mouse pointer) seems to be difficult in Xorg/Xlib.
Currently, Gscreendump takes a screenshot and replaces the cursor(image) with standard [GDK_LEFT_PTR]("http://library.gnome.org/devel/gdk/stable/gdk-Cursors.html") cursor.

Thanks guys! I've just installed and tried Gscreendump but it seemed that Gscreendump couldn't perform a delayed capturing...

In fact I'm writing tutorials of Blender 3D (in Chinese) and thus I need to do quite a lot of capturing for specific cursors, sub-menus and some special interface effects.

I've also tried Shutter but it can't capture the Blender cursors either. Maybe I should try namaku0's suggestion to use recordMyDesktop first and then extract frames from the video.

---

### Post by artspace on 2009-03-16
[ATTACH]106585[/ATTACH]

I finally got the above screenshot through:

1. using recordMyDesktop to record the screen (joining viewports in Blender where the RMB is pressed and a sub-menu pops up, and then the cursor changes).

2. playing the video (ogv format) with Totem in fullscreen mode.

3. pressing Shift+S to take the screenshot of Totem.

4. cropping the screenshot in GIMP.

This is the only workaround recently I think...:( thank namaku0 for giving me this suggestion!

---

### Post by moma on 2009-03-16
Re-hello,

Thank you for trying Gscreendump. 
I will immediately start work to improve the code so it will have "screenshot delay" and maybe other new features.

---

### Post by artspace on 2009-03-16
> **moma said:**
> Re-hello,

Thank you for trying Gscreendump. 
I will immediately start work to improve the code so it will have "screenshot delay" and maybe other new features.

Thank you moma! for your efforts to develop such great screen capturing program. I'm looking forward to seeing a new version of Gscreendump. :popcorn:

---

### Post by mb_webguy on 2009-03-24
Have you tried xvidcap?  It's a screen capture application like recordMyDesktop, but gives you the option of saving to a number of different formats, including jpg files.

---

