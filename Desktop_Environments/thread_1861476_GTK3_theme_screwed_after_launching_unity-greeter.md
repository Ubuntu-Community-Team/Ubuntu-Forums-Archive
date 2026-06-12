---
title: "GTK3 theme screwed after launching unity-greeter"
date: 2011-10-15
forum: Desktop Environments
---

### Post by uilt on 2011-10-15
I accidentally ran the command "unity-greeter" and my theme got screwed. The icons are changed and the buttons don't seem to be ambiance themed anymore. The buttons and icons are the same in Gnome3 shell as well as in unity. Gnome tweak tool doesn't work in changing it back. I also tried reinstalling ubuntu-desktop. It may be a problem with some sort of configuration because the guest session looks fine. I've attached a screenshot. Is there a way to fix it?

Edit: In .xsession-errors there are multiple instances of "(gnome-settings-daemon:6086): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed"...
Nautilus also consistently crashes after a couple minutes of use with this error: "(gnome-settings-daemon:6086): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed"

I'm using 64 bit Ubuntu 11.10

---

### Post by uilt on 2011-10-16
Okay, it seems to be the same problem as this: [http://askubuntu.com/questions/61671/tragedy-after-login-unity-from-unity-greeter-lightdm-launched-from-processing](http://askubuntu.com/questions/61671/tragedy-after-login-unity-from-unity-greeter-lightdm-launched-from-processing)  Unfortunately, that question was closed off for being unintelligible.  I was able to restore some of the windows by adding a settings.ini to ~/.config/gtk-3.0 but is seems to be only a stopgap measure because most of the icons, fonts, and windows are still clearlooks    

Update: Running gnome-settings-daemon with gksudo and gnome-tweak-tool with gksudo works...is it some sort of permissions problem that causes gnome-settings-daemon to fall back on clearlooks?

---

### Post by markjensen on 2011-10-16
I was able to duplicate your problem by running the ubuntu-greeter. What you listed to fix it would work for that session, but logging out and in has not.

I am going to look into this a bit more when I can - especially as I have (unwisely?) put myself into the same position you were in. :P

I think maybe removing some .xxxxxx file or folder will allow automatic recreation and fix the problem, as well.

---

### Post by uilt on 2011-10-16
Oh no! D:  Yeah, I actually hit this problem when logging in a couple times, but this one is more permanent :(

> I think maybe removing some .xxxxxx file or folder will allow automatic recreation and fix the problem, as well.

This is probably true. I took another try at it this morning and I was able to "fix" the problem for now by completing replacing my dconf file in ~/.config/dconf with one from a guest session. Now I'm trying to figure out exactly which dconf entry went wrong so I can fix it without destroying my settings for my other apps....

---

### Post by uilt on 2011-10-16
I seemed to have solved the problem! :D
unity-greeter seems to have disabled a host of gnome-settings-daemon plugins, so in order to re-enable them, I ran "dconf-editor," and then going to org/gnome/settings-daemon/xsettings and checking the "active" value, gnome-settings-daemon will actually start working properly again. I also enabled a couple other disabled plugins along the way. 

*Edit: Correct dconf path is org/gnome/settings-daemon/plugins/xsettings  as markjensen pointed out below. Thanks for the correction!*

In the end, i managed to get everything back, even my color scheme (carried over somehow from gtk2), although it seems like my docky settings were destroyed along the way somehow :P

---

### Post by markjensen on 2011-10-16
Yup, that did it for me, too!

Just want to clarify the path in dconf-editor a bit more. It is:
org/gnome/settings-daemon/plugins/xsettings

Good find!

---

### Post by Jaginus on 2011-10-23
Hi,

It worked !!!. Thank you so much for the help !!!

Jag

---

### Post by 14quartz on 2011-12-27
Thank You so much....

I too tried & got stuck.

---

### Post by simön on 2012-03-11
Thats really weired. It also changed my monitor settings what took me a while to re-setup... :-/

But thanks for your steps here! Worked for me! I (re-)activated all of the plugins.

---

### Post by pecinta_linux on 2012-03-22
thank it work :D

---

