---
title: "Window manager not starting automatically"
date: 2010-11-02
forum: Desktop Environments
---

### Post by yunchiluo on 2010-11-02
Hi,

For some reason my window manager stopped starting automatically. Sometime just before or after it happened (I may have tried uninstalling before and after, can't remember exactly), I uninstalled wine and xfce4-desktop (wanted to try it out, gnome is running default and is the one running now). Now when I log in, windows have no title bars and Docky complains that compiz was not started.

Running the command "compiz &" inside terminal starts up compiz with no problems but that's still undesirable. I want compiz to start with login.

So I've tried setting the $WINDOW_MANAGER variable inside ~/.gnomerc. Also tried using System -> Preferences -> Appearance to turn visual effects to none and turn it back on.

Finally I tried setting in **/etc/X11/Xsession.d/99x11-common_start**
```
exec $STARTUP --debug
```
Then I found in ~/.xsession-errors
```

gnome-session[11873]: DEBUG(+): GsmManager: Phase WINDOW_MANAGER
gnome-session[11873]: DEBUG(+): app /org/gnome/SessionManager/App45 is disabled by Hidden
gnome-session[11873]: DEBUG(+): GsmManager: ID: /org/gnome/SessionManager/App45 app-id:compiz.desktop   is-disabled:1   is-conditionally-disabled:0 is-delayed:0
gnome-session[11873]: DEBUG(+): GsmManager: Phase PANEL
gnome-session[11873]: DEBUG(+): GsmManager: Phase DESKTOP
gnome-session[11873]: DEBUG(+): GsmManager: Phase APPLICATION

```

and later on

```

gnome-session[11873]: DEBUG(+): GsmManager: ending phase INITIALIZATION

gnome-session[11873]: DEBUG(+): GsmManager: starting phase WINDOW_MANAGER

gnome-session[11873]: DEBUG(+): app /org/gnome/SessionManager/App45 is disabled by Hidden
gnome-session[11873]: DEBUG(+): GsmManager: Skipping disabled app: /org/gnome/SessionManager/App45
gnome-session[11873]: DEBUG(+): GsmManager: ending phase WINDOW_MANAGER

gnome-session[11873]: DEBUG(+): GsmManager: starting phase PANEL

```

Both say that **compiz is disabled by Hidden**. No idea what "Hidden" is and I'm not exactly sure if this is the problem, but either way I don't know how to  enable it.

Does anyone know how to get the window manager to start up correctly again?

---

### Post by Barriehie on 2010-11-02
From a terminal try:
```

compiz --replace
```and reboot.

---

### Post by yunchiluo on 2010-11-02
This turns on compiz but does not persist between sessions. Does anyone know how to change the settings so that
```
GsmManager: ID: /org/gnome/SessionManager/App45 app-id:compiz.desktop   is-disabled:1   is-conditionally-disabled:0 is-delayed:0
```
so that it shows is-disabled:0?

---

### Post by Barriehie on 2010-11-02
In regards to xfce4 did you remove it or purge it???

---

### Post by yunchiluo on 2010-11-02
I did "sudo apt-get remove xfce4*"

---

### Post by Barriehie on 2010-11-02
> **yunchiluo said:**
> I did "sudo apt-get remove xfce4*"

Try it again except use 'purge' where you have 'remove'.  No guarantees given!  WHen you remove packages the config files are left; when you purge then the config files are removed also.

Edit: You'll have to reboot after purging...

---

### Post by yunchiluo on 2010-11-02
Compiz was working in gnome when xfce4 was installed though. Xfce4 had it disabled, but gnome still had compiz working completely. I can only imagine that the uninstall took out some necessary config files or something, not the other way around?

---

### Post by Barriehie on 2010-11-02
Try booting into single user mode and:
```

# > xinit /usr/bin/gnome-session -- :1
```and then save the session after getting to the desktop.  I use fluxbox and am a bit rusty on this!

HTH

---

### Post by yunchiluo on 2010-11-02
I seem to have fixed it by copying compiz.desktop into ~/.config/autostart. Is this the correct way for starting compiz and should it have been there to start with? I may have deleted compiz by accident when doing some cleaning in the menu editor.

Also noticed that the same thing happened to nautilus and fixed it the same way.

---

### Post by Barriehie on 2010-11-02
> **yunchiluo said:**
> I seem to have fixed it by copying compiz.desktop into ~/.config/autostart. Is this the correct way for starting compiz and should it have been there to start with? I may have deleted compiz by accident when doing some cleaning in the menu editor.

Also noticed that the same thing happened to nautilus and fixed it the same way.

Might want to have a look at ~/.gnome2/session file.  That's where metacity is started on my machine.  I think that once you've got:
```

#,Program=compiz
``` entry in the session file you can take it out of autostart.  There will probably be additional lines following that entry before the number (#) changes.  Just make sure to save the session before logging out!

HTH

---

### Post by yunchiluo on 2010-11-02
> **Barriehie said:**
> Might want to have a look at ~/.gnome2/session file.  That's where metacity is started on my machine.

There's no session file in ~/.gnome2 for me. I ran gnome-session-save.

---

### Post by yunchiluo on 2010-11-02
My session information appears to be actually saved in ~/.config/session-state, containing .desktop entries for applications running when I saved the session. Nautilus does get saved now but for some reason if I log in to a saved session, nautilus's file browser starts up repeatedly until my computer runs out of memory.

I also looked into gconf-editor. "/desktop/gnome/session/required_components_list" contains windowmanager, panel, and filemanager. The value for windowmanager is compiz, and value for filemanager is nautilus. But logging into the session without the .desktop files in ~/.config/autostart leaves me without a filemanager nor a window manager. So it appears I'm back at the original problem of figuring out why Compiz and Nautilus were disabled in the session and how to enable them...?

---

### Post by Barriehie on 2010-11-02
Can't help with nautilus; I use thunar, it's much faster.  How about purging/installing compiz?  Pay attention to what it wants to remove!  I'ld go with the -s option and pipe to file; i.e.:
```

# > aptitude -s -y purge compiz > ./what_will_happen

```
I use metacity, once again, faster.

---

### Post by yunchiluo on 2010-11-02
Doesn't seem to say anything interesting. Already tried purging and reinstalling.
```
The following packages will be REMOVED:  
  compiz{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 65.5kB will be freed.
Would download/install/remove packages.
```

---

### Post by Barriehie on 2010-11-02
How about:

launch gconf-editor (Alt F2)

Navigate to /desktop/gnome/applications/window_manager and set the default key to /usr/bin/compiz

Hack Idea: put /usr/bin/compiz at the end of /etc/rc.local

Don't suppose you made a backup before trying all this out? ;)

---

### Post by yunchiluo on 2010-11-02
Already set.

---

### Post by Barriehie on 2010-11-02
Last idea!  Go to a terminal and:
```

metacity --replace &
```
Save the session and then shut down.
Power back up and then reverse it.
```

compiz --replace &
```
save the session / logout / log back in and see.

Edit: Do you have this file?
~/.config/compiz/compizconfig/Default.ini

You can rename it and when compiz is told to start it will regenerate it.

Edit:: Check this:
[http://ubuntuforums.org/showthread.php?t=1608087&highlight=start+compiz](http://ubuntuforums.org/showthread.php?t=1608087&highlight=start+compiz)

[http://ubuntuforums.org/showpost.php?p=9279994&postcount=9](http://ubuntuforums.org/showpost.php?p=9279994&postcount=9)

---

### Post by yunchiluo on 2010-11-03
> **Barriehie said:**
> Last idea!  Go to a terminal and:
```

metacity --replace &
```
Save the session and then shut down.
Power back up and then reverse it.
```

compiz --replace &
```
save the session / logout / log back in and see.
This didn't work for either metacity OR compiz. It still seems like there's simply no window manager being started, not that compiz is failing. Saving session did seem to get Nautilus running again without having it in the autostart folder.

> Edit: Do you have this file?
~/.config/compiz/compizconfig/Default.ini

You can rename it and when compiz is told to start it will regenerate it.
This file does not get regenerated after I rename it.

> 
Edit:: Check this:
[http://ubuntuforums.org/showthread.php?t=1608087&highlight=start+compiz](http://ubuntuforums.org/showthread.php?t=1608087&highlight=start+compiz)

[http://ubuntuforums.org/showpost.php?p=9279994&postcount=9](http://ubuntuforums.org/showpost.php?p=9279994&postcount=9)
I've tried purging everything related to compiz and reinstalling. Didn't fix anything :(

There's also nothing in "/etc/X11/Xsession.d/" that mentions compiz on my computer.

This config issue seems to reinstall Ubuntu for but I don't see another choice at the moment :/

---

### Post by yunchiluo on 2010-11-03
Fixed it! still not sure where the problem is.

I ran
```

sudo apt-get remove --purge compiz.*
sudo apt-get install --reinstall gnome-desktop-environment
sudo apt-get install compiz compiz-gnome

```

Rebooted and all was well again. Maybe uninstalling xfce4 took away some packages gnome needed?

Edit: Reinstalling gnome-desktop-environment pulled in A LOT of packages that I didn't need but whatever. Noticed compiz.desktop is back in ~/.config/autostart, so I may have just confused myself spending too much time playing around with it.

---

### Post by Barriehie on 2010-11-03
Glad you got it! So your last step will be to make a backup???  ;)

---

### Post by Barriehie on 2010-11-03
Here's an idea...  You can install virtualbox-ose and unless you're running 64 bits you can mirror your machine (make a guest), virtually, in a window on your desktop.  Play with whatever and if you like it then install it on your host machine.  I was going to do that to test apache configs but a limitation of vbox is that I wouldn't be able to mirror 64 bits.  If you decide to do that it's still reasonably fresh, haven't trashed the notes yet, in my head.  My notes to get on my wiki are ever growing...

---

### Post by yunchiluo on 2010-11-05
Unfortunately, my machine is 64 bits, but that's a cool idea. My suspend seems to have stopped working after the last fix. I feel like I'm plugging holes. I think I'll just do a clean install and copy over what configs I need. Thanks for all your help.

---

### Post by yunchiluo on 2010-11-05
So random comment. Just noticed we joined in the same month... but you have a LOT more posts than i do :p

---

