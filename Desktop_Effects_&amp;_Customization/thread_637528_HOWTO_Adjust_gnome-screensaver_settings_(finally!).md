---
title: "HOWTO: Adjust gnome-screensaver settings (finally!)"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by Crashmaxx on 2007-12-11
Ever since Dapper Drake when they replaced xscreensaver with gnome-screensaver there have been people wondering how to adjust the settings of the selected screensaver. There has been a LOT of debate about this and Gnome refuses to do anything about it. Finally, someone has written a replacement for the settings window so we can have the basic feature back.

Here is a screenshot of it:
[http://software.xfx.net/utilities/sss/images/sss_ss.gif](http://software.xfx.net/utilities/sss/images/sss_ss.gif)

This guide is how to install xfX's Sceensaver Settings package. He has only made a package for Gutsy Gibbon so far, and the program is still in its very early stages, so all this is subject to change and crashes. But since it just adjusts settings and doesn't actually run the screensaver, it is still reasonably safe to use, even at this early stage.

This guide is only for Gnome users, users of other DE's like KDE(Kubuntu) and XFCE(Xubuntu) do not use gnome-screensaver and therefore should not use this guide.

First, download the most recent deb from xFX's site:
[http://software.xfx.net/utilities/sss/index.htm](http://software.xfx.net/utilities/sss/index.htm)

Second, browse to where you downloaded the file (most likely Desktop or home) and simply double-click it. GDebi Package Installer will open it and check for dependencies. If you have Mono on your machine as per a default Ubuntu install, all should check out fine. Otherwise, install any requested dependencies and try again. When this is good, just click "Install" and type in your password.

Last, the launcher will be under Applications>Other, so you may want to go to System>Preferences>Main Menu and move it to Preferences. You may also want to change the name slightly, most likely to xFXSceensaver, and change the icon to something pretty. You can also run it from command line with:
```

screensaver-settings 

```

There is a good chance it will crash at some point. It is still in early development, so that is expected. If it does crash, best bet is to open it from command line and try to repeat the crash. Then explain the crash and post the output in terminal here:
[http://software.xfx.net/ss.htm?redir=sss](http://software.xfx.net/ss.htm?redir=sss)

That is it and enjoy!

---

### Post by K.Mandla on 2007-12-20
Moved to Desktop Effects and Customization.

---

### Post by Chipmaster on 2008-01-11
Very nice, I've been looking for a way to do this for a long time.

---

### Post by urosh2 on 2008-01-11
U are a time saver.
Thanks for this.

---

### Post by PhilCash on 2008-04-02
A vast improvement on the packaged screen saver, well done!
Will the next version support F-Spot, or allow the definition of user directories for images to use for GLSlideshow? The help screen seems to indicate that latter is in the mill - although it doesn't work at present - no "Advanced" button to select...

cheers,
Phil

---

### Post by notwen on 2008-04-02
Wow, I may reconsider using screensavers again.  Thanks for the link and the heads up.  =]

---

