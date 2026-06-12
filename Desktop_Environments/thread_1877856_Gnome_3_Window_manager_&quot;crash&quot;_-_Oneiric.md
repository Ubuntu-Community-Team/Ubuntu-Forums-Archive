---
title: "Gnome 3 Window manager &quot;crash&quot; - Oneiric"
date: 2011-11-08
forum: Desktop Environments
---

### Post by felipunk on 2011-11-08
Hi everyone.

I hope you're (all) doing great!

Right now I'm facing a problem in Oneiric that's its getting really annoying for me.

From time to time my window manager sort of crash, I perceive that this happens mostly when I minimize a window (sometimes VMplayer window, sometimes LibreOffice, but sometimes also happens with GTK native application windows). The symptom is that when the window manager crashes all the window decorations go away and although everything remains "operating" (music and videos keep playing, apps continues to run) I'm not able to manipulate the windows (nor moving closing or even invoke "activities" with windows key), and since the top bar goes away to, I can't log out of gnome.

So far the only thing that I can do is to change to a terminal (CTRL + ALT + F2) and reboot my system from there.

I've tried to kill gnome-shell process and see if they recover automatically but no, they only end and sometimes I just ended with a text screen (on CTRL + ALT + F7) with the mouse being able to move and that's it.

So my questions are:

1 - Have anyone of you experienced this and solved?
2 - Do you know of a workaround in the meantime? something that allows me to recover the desktop without reboot (BTW, the ALT + F2 shortcut does not work either)
3 - Is there anything that I can provide so you guys can more easily help me?

The configuration is: 
- Oneiric installed from CD but keeping my /home partition. (BTW I've already remove all the configuration files that remained from previous Ubuntu versions).
- Desktop used, Gnome 3 with many WebUpd8 extensions.
- Hardware-wise the system is a Lenovo T420s with Intel Graphics.

** I'm posting the last 200 lines from .xsessions-errors in case it help.

Thank you very much in advanced for your attention!

---

### Post by Frogs Hair on 2011-11-08
I know that some are having problems with crashes only with 3rd party themes , but if you are using the default theme that would not apply .

---

### Post by felipunk on 2011-11-10
Hi Frogs.

Thanks for your reply, I've suspected that, let me revert the themes to default and take it for a spin.

Now when you say 3rd party themes, you mean gtk3 themes? shell themes? icons? or all of them? and, what should I consider as "default" the adwaita ones? or the ones from ubuntu (you know, Ambiance and Radiance)

Hopefully that do the trick.

---

### Post by felipunk on 2011-11-15
Ok, guys.

Everything looks the same even with all of the themes set as default. My gnome-shell is still crash/hanging.

The news is that now I've found that if I switch to the console in CRTL+ALT+F1 I can recover the desktop doing this:

[LIST]
ps ux | grep gnome-shell
[/LIST]
[LIST]
kill -1 <gnome-shell PID> (with a "one" not an "L")
[/LIST]

After that I can return to the CTRL+ALT+F7 and the desktop flicker a little bit but will recover after a short while.

The downside is that it looks like the gnome-shell notification system goes down, because now, instead of see them on the bottom of the screen, they show as pop-up GTK alert windows (which is very annoying).

I hope you found this useful and any other information that you have that you think could help me with this problem will be very appreciated.

Bye.

---

### Post by Frogs Hair on 2011-11-15
Just a guess , but it could be graphics card related . Are you using a proprietary driver ? . You could enable the Alt + F2 command prompt from keyboard > shortcuts > system . Use the following command to open Looking Glass and check for errors .```
lg
```

---

### Post by Raev33 on 2011-11-17
I have the exact same problem. If anybody finds an solution/explanation for the behavior, please share it :)

---

### Post by paul555 on 2011-11-18
I have also exactly the same problem. Any solution to this?

---

### Post by iMerlin on 2011-11-21
Happening here as well. Less common after I uninstalled the auto-move-workspace extension, but still happens and it's totally random.

I wasn't even at my computer when it just crashed Gnome Shell, twice. Then I am left with a desktop that I can't launch the shell from and have to restart the DM to get it up and running again.

This doesn't appear to be a segfault, can't find any records in the logs at least. Extremely annoying, I'm otherwise very happy with Gnome Shell.

---

### Post by Raev33 on 2011-11-21
It's also random for me. Sometimes gnome-shell crashes and relaunches itself to normal state, and sometimes the window manager doesn't restart, and I'm left without the window manager.
Does anyone know if this bug already has been reported? I searched but couldn't find anything...

---

### Post by kinamic on 2011-11-24
I'm having the exact symptoms as Raev33.  Besides this I am really liking Gnome 3 over Unity.

---

### Post by haico85 on 2011-11-25
Same for me!

---

### Post by flammon on 2011-12-08
I'd like to add a me too and that the crashes happen much more often when I'm running vmplayer. To the point that I'm nervous when I start it up.

Here are some of the errors that I'm seeing in my logs.

```

Clutter-WARNING **: Attempting to add actor of type 'ShellGenericContainer' to a container of type 'StBoxL
ayout', but the actor has already a parent of type 'StBoxLayout'.

St-WARNING **: Actor of type 'ShellGenericContainer' is not a child of the StBoxLayout container
      JS LOG: GNOME Shell started at Thu Nov 03 2011 17:06:06 GMT-0400 (EDT)
      JS LOG: Unable to guess content types on added mount POLARBEAR-Share: Error: Error invoking Gio.gues
s_content_type_finish: mount doesn't implement content type guessing
      JS LOG: Unable to guess content types on added mount POLARBEAR-WWW: Error: Error invoking Gio.guess_
content_type_finish: mount doesn't implement content type guessing
      JS LOG: Unable to guess content types on added mount e6da19f0-b60e-4302-8ae0-1e5cca27977c: Error: Er
ror invoking Gio.guess_content_type_finish: mount doesn't implement content type guessing

libebook-WARNING **: e_book_client_new: Cannot get book from factory: Invalid source

folks-WARNING **: Error preparing persona store 'eds:1299234640.5336.17@cheetah': Couldn't open address bo
ok ‘1299234640.5336.17@cheetah’: Invalid source
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
** DEBUG: The GetProfileForWindow request failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: T
he name org.gnome.ColorManager was not provided by any .service files
** DEBUG: The GetProfileForWindow request failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: T
he name org.gnome.ColorManager was not provided by any .service files
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2c00003 (Workrave) with a timestamp of 0.  This shouldn't
 happen!

Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed

Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1c00004 (Desktop) with a timestamp of 0.  This shouldn't 
happen!
      JS LOG: pushModal: invocation of begin_modal failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1c1db47 (Backup) with a timestamp of 0.  This shouldn't h
appen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1c00004 (Desktop) with a timestamp of 0.  This shouldn't 
happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1c00004 (Desktop) with a timestamp of 0.  This shouldn't 
happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1c00004 (Desktop) with a timestamp of 0.  This shouldn't 
happen!
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x18f16f1
 (Go to Line)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be f
ixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x18000a1
 (Web - inte)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be f
ixed.


```

---

### Post by haico85 on 2011-12-17
Hi everybody!

It seems that I found a solution that worked for me. I'm not sure if it can be the origin of the problem but after upgrading my nvidia driver from 280.13 to 290.10 I did not observe these crashes anymore.

The driver update is in the [XSwat-PPA]("http://ubuntuforums.org/The%20driver%20update%20you%20can%20find%20in%20the%20XSwat-PPA%20%28ppa:ubuntu-x-swat/x-updates%29.") (ppa:ubuntu-x-swat/x-updates). I then updated the packages nvidia-current and nvidia-settings (removed, updated, installed new ones).

Would be interesting to know if somebody can confirm this or if anybody knows why and if the nvidia driver can cause these problems.

EDIT: Some additional information
- I have the GeForce GTS 250 on a 64bit machine. 
- I also solved the same problem with this on a different machine, also 64bit and GeForce (but I don't remember the exact model).

---

### Post by flammon on 2011-12-17
I've been running 290.10 for a while now and gnome-shell didn't stop crashing. The crashing is easily repreducible when I'm running vmplayer. I can make it crash within a few seconds just by going in and out of Activities a few times.

[FONT="Courier New"]Linux cheetah 3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Video: GeForce GTX 460 with 768 MB running at 1920x1200
CPU:   AMD Phenom(tm) II X6 1090T
RAM:   8GB[/FONT]

---

### Post by Fejodor on 2012-02-16
Hi everyone!

Has there been made any progress on this? I've got more or less the same problem: From time to time all the windows start flickering, normally this stops after about two seconds, sometimes the window borders disappear and the system becomes unusable. I found no pattern when this accours - seems completly randomly to me.

Using Gnome 3.2.0 on Linux Mint 12 with an ATI Mobility Radeon HD 4650 card. Driver Version: 8.93-111205a-132081C-ATI
(driver downloaded from the ATI website - the one jockey offered didnt't seem to work)

Not sure what info could be useful, so please tell me what else you need to know.
Thanks to everyone contributing!

---

### Post by jose1711 on 2012-03-11
see [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/899491](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/899491) and if possible continue discussing it there

---

### Post by piemenux on 2012-06-29
ubuntu studio / xfce4 (oneiric) on lenovo with intel graphics. same "crash", but my expierience is when i relog without closing working programs. symptoms are - no window management :/ everything else working fine. in task manager i can't find xwfm or something like this - window frame manager? is there any way to resart it manually?

---

### Post by piemenux on 2012-06-29
while trying to reanable windows manager (sudo xfwm4) there's errors :

(xfwm4:5685): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(xfwm4:5685): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

(xfwm4:5685): GLib-WARNING **: (/build/buildd/glib2.0-2.32.3/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)

(xfwm4:5685): xfwm4-WARNING **: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined

but now working.. please, explain how to prevent same craches later..

---

### Post by lithium85 on 2012-08-05
Hi,

I have the same problem using Linux Mint Debian on a Leonovo T420. I also have a Nvidia hybrid card and integrated Intel Graphics.
Any news on this issue so far?

Thanks already,
Bernhard

---

