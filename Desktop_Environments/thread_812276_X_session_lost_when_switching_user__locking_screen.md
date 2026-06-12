---
title: "X session lost when switching user / locking screen"
date: 2008-05-29
forum: Desktop Environments
---

### Post by diazruy on 2008-05-29
Hi,

I am a recent convert to Linux and I am having a bit of a hard time getting my system right. I installed Ubuntu 7.10 (can't upgrade to 8.04 because some of the tools I need have compatibility issues on Hardy) and I am having trouble when locking my screen (Ctrl-Alt-L) as this seems to somehow manage to kill the X server. After attempting to lock the screen, I am presented with the Ubuntu login screen (beige background), and after logging in, my previously open applications have all been closed and I am pretty much on a fresh desktop. I have managed to salvage this from .xsession-errors:

> 
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
The application 'x-session-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'vino-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gecko: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'nm-applet' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'bluetooth-applet' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'pidgin' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'update-notifier' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
X connection to :0.0 host broken (explicit kill or server shutdown)
The application 'gnome-terminal' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'applet.py' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.


Any pointers on what's going on? 

Thanks
Ruy

---

### Post by diazruy on 2008-05-29
Hmmmm... I changed the screensaver and this solved the problem.

I originally had 'Endgame' selected and changed it to 'Blank screen'. After verifying that things worked fine, I tried a couple of others and have come to the conclusion that the problem is somehow related to the video card and/or driver, given that 'simple' screensavers like Blank screen or Floating Ubuntu seem to work fine, but when I choose a 3D screensaver, things break. 

I am using an ATI X550 videocard and using the ATI proprietary driver.

Any suggestions or ideas on whether this conclusion is valid and if there's a solution?

thanks
Ruy

---

