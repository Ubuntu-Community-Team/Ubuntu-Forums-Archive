---
title: "keyboard problems with tightvnc on feisty"
date: 2007-04-23
forum: Desktop Environments
---

### Post by allyn on 2007-04-23
i've been using tightvnc to access my headless linux file server for years and it has always worked perfectly.

but after the upgrade to feisty, the keyboard is no longer working right.  whatever i type comes out wrong.  i've tried playing with the keyboard layout but nothing seems to make a difference.

when i type "qwerty" it comes out "c.gvn" (the y key doesn't seem to do anything).  the / key is return and the 5 key is backspace.  does this sound familiar to anyone?

i would consider switching to vnc4 but there is a bug that gnome-session doesn't run with that right now.

the console x session works just fine.  the problem seems to be limited to tightvnc.

any ideas?  thanks in advance.

---

### Post by allyn on 2007-04-25
this appears to be a gnome problem.

more info here: [http://ubuntuforums.org/showthread.php?p=2534620](http://ubuntuforums.org/showthread.php?p=2534620)

---

### Post by fourthirtysix on 2007-04-26
i've been following this issue since i am having the same problem. it seems to be referred to as the "abfh" problem since that is what people get when they type "asdf"

i upgraded two computers to feisty at the same time, and i only have the gnome keyboard abfh problem on a headless machine that I use tightvnc to connect to.  i never had a problem running the exact same configuration with edgy.

i tried playing around with keyboard and language settings in gnome a little bit, but nothing seemed to help.

i hope someone can track this problem down. i will attempt to look into more this weekend.

if anyone solves the problem, please post the answer here. i am tracking what appears to be the same problem in a number of threads/posts:

[http://ubuntuforums.org/showthread.php?p=2523097](http://ubuntuforums.org/showthread.php?p=2523097)

[http://ubuntuforums.org/showthread.php?p=2517629](http://ubuntuforums.org/showthread.php?p=2517629)

[http://ubuntuforums.org/showthread.php?t=233613](http://ubuntuforums.org/showthread.php?t=233613)

[http://ubuntuforums.org/showthread.php?t=420179](http://ubuntuforums.org/showthread.php?t=420179)

---

### Post by Labanana on 2007-04-26
I am sorry, my previous solution (uninstalling compiz) worked only on a few systems (namely only on my test pc) :( and that probably was not really related to compiz itself.

I could only manage to make all of my tightvnc servers work by doing something really _ugly_ and dirty.

Please, **don't do that on your systems** if you don't have a clear notion of what side-effects this may have. I have no clue at all about other implications, sorry. I only know that it allowed me to access my machines and still remotely use gnome. Built-in Remote Display was not a viable option for me.

So, the workaround is ugly and the only reason because I am writing these here is that I hope that it may give inspiration for someone to provide a real solution.

I launched gconf-editor, navigated to "/desktop/gnome/peripherals/keyboard/kbd" and added an invalid layout to the "layouts" key, I made sure that it was the only layout in the list. Now gnome starts smoothly on tightvncserver display, and my italian keyboard works as expected. When I launch gnome on local xfree servers it shows a couple of error box about XKB configuration errors, but apart from that, it appears to work correctly...

Please, someone provides a real fix! :)

---

### Post by allyn on 2007-05-03
the above is a yucky workaround but i can verify that it worked for me.  thanks.

---

### Post by John Williams on 2007-05-04
I also have this problem on vncserver (not tightvnc) and this workaround worked for me also... BTW, to get to gconf-editor without a useful keyboard, use the places menu and navigate to /usr/bin/gconf-editor and double click it...  I entered a value of "c.b" and removed the us-101 entry. Left the kbd.sysbackup entry alone. Logged out and back in and it was fixed... 

This is bug [http://bugs.launchpad.net/ubuntu/+source/control-center/+bug/108928](http://bugs.launchpad.net/ubuntu/+source/control-center/+bug/108928)

---

### Post by flabdablet on 2007-07-18
What fixed this for me:
[LIST=1]
[*]Install vnc4server instead of tightvnc:

```
sudo apt-get remove tightvncserver
sudo apt-get install vnc4server
```

[*]Fix a small breakage in the standard vnc4server installation:

```
sudo chmod ugo+x /etc/X11/xinit/xinitrc
```

[*]Start vncserver, to make it create the default ~/.vnc/ folder:

```
vncserver :1
```

[*]Type in the new VNC password when prompted to do so, then kill the VNC server:

```
vncserver -kill :1
```

[*]Edit ~/.vnc/xstartup, and uncomment the two lines it says to uncomment for a normal desktop; the result looks like this (I'm pretty sure you could just get rid of everything after the "exec" line if you want)
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
```

[*]Use the "-extension XFIXES" option when starting vncserver; this makes it work properly with Gnome.

```
vncserver :1 -extension XFIXES
```
[/LIST]
I am using this right now to run stuff on my laptop at home (Feisty) using UltraVNC from a Windows box at work.  I used PuTTY on the Windows box to get a ssh session and a port 5901 tunnel, and did the whole thing remotely.  Keyboard works fine.  Gnome apps don't crash.  I'm a happy camper.

Like me, you may find that leaving the "normal desktop" lines commented out in xstartup, and installing twm
```
sudo apt-get install twm
```
gives you a far more responsive desktop over slow connections.  I've successfully run gimp this way, and provided I use "-extension XFIXES" when starting vncserver, it works just fine.

---

### Post by mcstayinskool on 2007-07-21
> **John Williams said:**
> I also have this problem on vncserver (not tightvnc) and this workaround worked for me also... BTW, to get to gconf-editor without a useful keyboard, use the places menu and navigate to /usr/bin/gconf-editor and double click it...  I entered a value of "c.b" and removed the us-101 entry. Left the kbd.sysbackup entry alone. Logged out and back in and it was fixed... 

This is bug [http://bugs.launchpad.net/ubuntu/+source/control-center/+bug/108928](http://bugs.launchpad.net/ubuntu/+source/control-center/+bug/108928)

Thanks Ubuntu team! This was an infuriating issue for me as well, but made this switch via gconf-editor as John and others described and worked great.

#!/ben

---

### Post by m4dsc1 on 2008-02-13
> **Labanana said:**
> I am sorry, my previous solution (uninstalling compiz) worked only on a few systems (namely only on my test pc) :( and that probably was not really related to compiz itself.

I could only manage to make all of my tightvnc servers work by doing something really _ugly_ and dirty.

Please, **don't do that on your systems** if you don't have a clear notion of what side-effects this may have. I have no clue at all about other implications, sorry. I only know that it allowed me to access my machines and still remotely use gnome. Built-in Remote Display was not a viable option for me.

So, the workaround is ugly and the only reason because I am writing these here is that I hope that it may give inspiration for someone to provide a real solution.

I launched gconf-editor, navigated to "/desktop/gnome/peripherals/keyboard/kbd" and added an invalid layout to the "layouts" key, I made sure that it was the only layout in the list. Now gnome starts smoothly on tightvncserver display, and my italian keyboard works as expected. When I launch gnome on local xfree servers it shows a couple of error box about XKB configuration errors, but apart from that, it appears to work correctly...

Please, someone provides a real fix! :)

This is a good fix for me as well.  Gnome + tightvnc.

Applications -> System Tools -> Configuration Editor
  Desktop -> Gnome -> Peripherals -> Keyboard -> KBD

Edit the layout key to delete what is there and add your "abfh" by typing asdf.

Then go to the Keyboard preferences and put back in US-105 if that's what you like.
System -> Preferences -> Keyboard
  Layouts 
     Add
         Choose your favorite.  Hit OK, mark as default.

Restart VNC, and hope it works.

--

---

