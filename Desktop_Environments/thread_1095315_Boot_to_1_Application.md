---
title: "Boot to 1 Application"
date: 2009-03-13
forum: Desktop Environments
---

### Post by smith3 on 2009-03-13
BTW total Ubuntu noob; have had it for 1 day.

I have an application that  will be used as an appliance.

I want Ubuntu (8.04) Gnome 2.22.3 to launch app on power on. I have go to the point where I can get it to auto login and was looking at sessions to launch the app. But I do not want anything else to run but this app (or appear to) ctrl alt delete and ctrl tab must be suppressed.

I looked into sessions but i was hoping for something like a they have in windows where u just launch it in the registry so no other apps will run (Firefox etc.) Is there a similar construct in Ubuntu?

Killing of usb /mouse and KB ports would be nice 2

Any input  would be great.

Thanks

---

### Post by Locutus_of_Borg on 2009-03-13
```

gedit /etc/X11/xorg.conf

```

Paste:
Option "DontZap" "true"

into the Server Layout section

This will disable ctrl+alt+backspace

I don't know what you mean by ctrl+tab


If this is an application that requires X running, I would recommend switching default window manager to something like twm, put the application in it's startup, and then lock the screen after it launches

something like this should probably work:

/usr/share/xsessions/TWM.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=twm
Comment=twm
Exec=/usr/bin/start_twm.sh
Type=Application

```

/usr/bin/start_twm.sh
```

#!/bin/bash
THE_APPLICATION_YOU_WANT_TO_RUN &
(sleep 10 && alock -auth pam) &
/usr/bin/twm

```

be sure to run `chmod 755 /usr/bin/start_twm.sh`

after you create it

also do not forget the & symbols after each app you want to run
and you will need to install alock (sudo apt-get install alock)


What this will, i think, do is start up a very minimal X session with nothing but your application running, locked, and without the ability to kill X or open any other programs

You can still switch to a different VT with the ctrl+alt+F[1-6] combination.

If you want to disable that as well, i think you can edit /etc/inittab and remove all but the first reference to agetty

```
sudo nano /etc/inittab
```

look for:

# TERMINALS
c1:12345:respawn:/sbin/agetty 38400 tty1 linux
c2:2345:respawn:/sbin/agetty 38400 tty2 linux
c3:2345:respawn:/sbin/agetty 38400 tty3 linux
c4:2345:respawn:/sbin/agetty 38400 tty4 linux
c5:2345:respawn:/sbin/agetty 38400 tty5 linux
c6:2345:respawn:/sbin/agetty 38400 tty6 linux

and add a # at the beginning of all but the first..though this would still leave you able to switch to first VT, but i dont think it would work if you disabled all of them

and without at least one of them, you couldn't really do anything apart from hold the power button and turn the computer off

---

### Post by smith3 on 2009-03-16
Borg-

Just got back from weekend. Thanks for very thorough answer. I have not implemented any suggestions but will today. Will keep u updated on progress. Thanks again.

-3

---

### Post by oldos2er on 2009-03-16
Ubuntu has no /etc/inittab, instead it uses something called Upstart. See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by smith3 on 2009-03-16
Progress:
[I]

Code:

gedit /etc/X11/xorg.conf[/I]

I used "file manager" and edited and saved xorg.conf to desktop xorg.conf.new  Then used:


Paste:
Option "DontZap" "true"

into the Server Layout section

This will disable ctrl+alt+backspace[/I]

sudo mv xorg.conf xorg.conf.old
sudo mv xorg.conf.new xorg.conf

[I]
I don't know what you mean by ctrl+tab[/I]
ctrl+Backspace is also suppressed (relaunching x11 I guess) ( did not know this existed as I am a noob)


Still looking  to suppress ctrl+alt+delete. 
alt+tab is what i meant I need to find a way to suppress that 2
upstart seems to replace /etc/inittab so i am looking into that.

The middle part of launching is still in work as well.

---

### Post by smith3 on 2009-03-16
oldos2er-

Looking into upstart it seems to be the place to be to start and suppress ctr+alt+delete.

I found the dir /etc/event.d
If I understand correctly I can add scripts to start apps in here.

There is also a file called ctrl-alt-delete that you would think set behavior for that key combo but does not seem to. When I remarked out the commands in it and re-booted it ctrl-alt-del still brings up the login/restart window.

Any  thoughts? Do you think it has something to do with rc0-rcS files?

---

### Post by smith3 on 2009-03-17
Found An important bit of the puzzle:

With Ubuntu 8.04 and Gnome 2.22.3

To disable ctr-alt-del 2 actions must be taken :

1. go to system>Preferences>Keyboard Shortcuts then under the Action Shortcut  section find desktop/log out and highlight. Then hit backspace to disable this keyboard binding. (other bindings can be disabled as well such as alt-tab)

2. in the /etc/event.d there is a file called control-alt-delete. Edit this file to remark out the behavior by adding # in front of these lines:

[FONT="Fixedsys"]start on control-alt-delete
exec /sbin/shutdown -r now "Control-Alt-Delete pressed"
[/FONT]
they should now look like:
[FONT="Fixedsys"]#start on control-alt-delete
#exec /sbin/shutdown -r now "Control-Alt-Delete pressed"[/FONT]

Not sure if the second action is actually necessary if you only boot into gnome but I think it will prevent virtual consoles from getting the ctr-alt-del.

---

### Post by Locutus_of_Borg on 2009-03-17
The ctrl+alt+delete key binding is specific to your desktop environment.

If you don't plan on using GNOME, and instead use TWM, there won't be any such key binding.  Ctrl+alt+backspace is built into X and you need that Option "DontZap" "True" in xorg.conf to disable it.

I wouldn't worry too much about /etc/inittab unless you really do not want the ability to change vt's.

You can try adding 

Option "DontVTSwitch" "true"

into xorg.conf, under ServerLayout.  This is supposed to disable the ctrl+alt+F# combination.

I forgot to mention, after you create those two files form my first post, when you are at the GDM login screen, you have to select TWM from the sessions menu.  You can then make it default, and if you don't want the ability to start another session, you should be able to edit the gdm theme and erase the section that presents the session chooser menu

/usr/share/gdm/themes


I dont have gdm installed here otherwise i would give an example, but it's just an xml file and shouldn't be hard to find where to edit

---

### Post by smith3 on 2009-03-19
Thanks for input, you have been very helpful.

- I am a bit of a noob so i don't want to get to far away from the base install. Once once I get all the pieces in place i will document it and post here.

---

