---
title: "starting custom desktop environment"
date: 2012-02-22
forum: Desktop Environments
---

### Post by v923z on 2012-02-22
Hi All,

I would like to have a minimalistic desktop, so I created /usr/share/xsession/custom.desktop, which looks like this
```

[Desktop Entry]
Encoding=UTF-8
Name=Custom
Comment=Nothing
Exec=/home/v923z/desktop.sh
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm

```and the file desktop.sh, which reads as 
```

compiz --use-root-window &
gnome-do &

```However, I cannot log on to this desktop. I appears in the list of available desktops, but it crashes immediately as I try to activate it. I have tried other desktop managers, like metacity, or gnome-wm, with the same results. Could someone point out, where the problem is?
Cheers,
v923z

---

### Post by Krytarik on 2012-02-22
For running a Compiz Standalone session, and since you are also running Oneiric 11.10, try setting it up following this guide:

[http://www.webupd8.org/2012/02/how-to-create-standalone-compiz-session.html](http://www.webupd8.org/2012/02/how-to-create-standalone-compiz-session.html)

Hope that helps.

---

### Post by v923z on 2012-02-23
Hi,

Thanks for the link! I have done everything as written, but I still have the same problem: at login, I am thrown back to the desktop manager, no matter what I do. It seems to me that I cannot run a script from the custom.desktop or similar files. Really odd.
Cheers,
v923z

---

### Post by Krytarik on 2012-02-23
> **v923z said:**
> Thanks for the link! I have done everything as written, but I still have the same problem: at login, I am thrown back to the desktop manager, no matter what I do.
Upon checking that guide again, I've just noticed that there is one major difference between my session script and those stated there: besides different parameters to actually invoke the session - which are proven to be needed differently from one Ubuntu version to another (I'm running Lucid 10.04) - I need to have (at least) one dedicated app that keeps the session open, also run through the session script; I've chosen AWN for that, for obvious reasons. In my setup, when I quit AWN, the session also quits. See below precisely how I'm invoking AWN for that matter.

"/usr/local/bin/compiz-session":
```
#!/bin/bash
ck-launch-session dbus-launch --exit-with-session compiz ccp & wmpid=$! 
sleep 1
if [ -f ~/.compiz-session ]; then
    source ~/.compiz-session &
else
    gnome-terminal &
fi
# Wait for WM
wait $wmpid &
**avant-window-navigator**
```

---

### Post by v923z on 2012-02-23
> **Krytarik said:**
> 
```
#!/bin/bash
ck-launch-session dbus-launch --exit-with-session compiz ccp & wmpid=$! 
sleep 1
if [ -f ~/.compiz-session ]; then
    source ~/.compiz-session &
else
    gnome-terminal &
fi
# Wait for WM
wait $wmpid &
**avant-window-navigator**
```

This indeed fixes the problem, though I am a bit wary of this solution: what if the user, either by accident or on purpose, closes awn? Is there really no other way of keeping the desktop alive? If I start fluxbox, e.g., it does not crash. What is it that prevents fluxbox from crashing?

---

### Post by Version Dependency on 2012-02-23
Yea...make sure you have a dock or panel loading or you won't get far with a compiz session.  I ran compiz standalone for some time but not recently.  I remember using a script to logout/reboot/shutdown out of compiz (which is tricky).  I'll attach it to see if it's of any use to you.  Just create a new launcher on your dock/panel pointing to it and clicking on it should provide you with the option in the photo.

```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk
import os

class DoTheLogOut:

    # Cancel/exit
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def onkeypress(self, widget, event):
        if event.keyval == gtk.keysyms.Escape:
            gtk.main_quit()
            return False

    def lost_focus(self, widget, event):
        if self.focus_check:
            gtk.main_quit()
            return False


    # Logout
    def logout(self, widget):
        os.system("killall start-fusion.sh")

    # Reboot
    def reboot(self, widget):
        os.system("dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart")

    # Shutdown
    def shutdown(self, widget):
        os.system("dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop")


    def __init__(self):
        # Create a new window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Exit? Choose an option:")
        self.window.set_resizable(False)
        self.window.set_position(1)
        self.window.connect("delete_event", self.delete_event)
        self.window.set_border_width(20)

        # Create a box to pack widgets into
        self.box1 = gtk.HBox(False, 0)
        self.window.add(self.box1)

        # Create cancel button
        self.button1 = gtk.Button("_Cancel")
        self.button1.set_border_width(10)
        self.button1.connect("clicked", self.delete_event, "Changed me mind :)")
        self.box1.pack_start(self.button1, True, True, 0)
        self.button1.show()

        # Create logout button
        self.button2 = gtk.Button("_Log out")
        self.button2.set_border_width(10)
        self.button2.connect("clicked", self.logout)
        self.box1.pack_start(self.button2, True, True, 0)
        self.button2.show()

        # Create reboot button
        self.button3 = gtk.Button("_Reboot")
        self.button3.set_border_width(10)
        self.button3.connect("clicked", self.reboot)
        self.box1.pack_start(self.button3, True, True, 0)
        self.button3.show()

        # Create shutdown button
        self.button4 = gtk.Button("_Shutdown")
        self.button4.set_border_width(10)
        self.button4.connect("clicked", self.shutdown)
        self.box1.pack_start(self.button4, True, True, 0)
        self.button4.show()


        self.focus_check = True
        self.window.connect("focus-out-event", self.lost_focus)
    self.window.connect("key-press-event", self.onkeypress)

        self.box1.show()
        self.window.show()

def main():
    gtk.main()

if __name__ == "__main__":
    gogogo = DoTheLogOut()
    main()
```

---

### Post by Krytarik on 2012-02-23
> **v923z said:**
> Is there really no other way of keeping the desktop alive?
I don't know of any yet. But you could ask Andrew from WebUpd8, as the setup he outlines in his post is supposedly working for him (and some others in the post's comment thread; no issues raised there so far).

---

### Post by gldearman on 2012-02-23
I'm trying the same thing right now. You can exit your session by killing the app keeping it open, but that's inelegant. The big desktop environments run a session manager to identify all the programs as part of a single session, so that you can log out of the session gracefully.

I'm trying to set that up right now using lxsession; no luck so far.  It's harder to configure than the documentation would make it seem. I'll post here if I achieve success.

---

### Post by v923z on 2012-02-23
> **Version Dependency said:**
> .  I'll attach it to see if it's of any use to you.  Just create a new launcher on your dock/panel pointing to it and clicking on it should provide you with the option in the photo.


Thanks for the code! This is certainly useful.
Cheer,
v923z

---

