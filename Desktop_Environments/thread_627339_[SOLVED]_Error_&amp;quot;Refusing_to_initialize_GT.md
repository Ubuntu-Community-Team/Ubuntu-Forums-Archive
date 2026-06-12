---
title: "[SOLVED] Error: &amp;quot;Refusing to initialize GTK+&amp;quot; can't login"
date: 2007-11-30
forum: Desktop Environments
---

### Post by aliencam on 2007-11-30
When I try to log into Gnome I get a "your session has lasted less than 10 seconds" error, and have to use my computer in the failsafe gnome mode.  

The full xsession errors file is  here: 

```

(process:5831): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5835): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/home/cameron/.profile: 1: [scaleaddon]: not found
/home/cameron/.profile: 2: as_close: not found
/home/cameron/.profile: 3: as_zoom: not found
/home/cameron/.profile: 4: s0_window_title: not found
/home/cameron/.profile: 5: s0_title_bold: not found
/home/cameron/.profile: 6: s0_title_size: not found
/home/cameron/.profile: 7: s0_border_size: not found
/home/cameron/.profile: 8: s0_font_color: not found
/home/cameron/.profile: 9: s0_back_color: not found
/home/cameron/.profile: 10: s0_window_highlight: not found
/home/cameron/.profile: 11: s0_highlight_color: not found
/home/cameron/.profile: 12: s0_layout_mode: not found
/home/cameron/.profile: 14: [place]: not found
/home/cameron/.profile: 15: s0_workarounds: not found
/home/cameron/.profile: 16: s0_mode: not found
/home/cameron/.profile: 17: s0_position_matches: not found
/home/cameron/.profile: 18: s0_position_x_values: not found
/home/cameron/.profile: 19: s0_position_y_values: not found
/home/cameron/.profile: 20: s0_viewport_matches: not found
/home/cameron/.profile: 21: s0_viewport_x_values: not found
/home/cameron/.profile: 22: s0_viewport_y_values: not found
/home/cameron/.profile: 24: [decoration]: not found
/home/cameron/.profile: 25: as_shadow_color: not found
/home/cameron/.profile: 26: as_shadow_x_offset: not found
/home/cameron/.profile: 27: as_shadow_y_offset: not found
/home/cameron/.profile: 28: as_command: not found
/home/cameron/.profile: 29: as_mipmap: not found
/home/cameron/.profile: 30: as_decoration_match: not found
/home/cameron/.profile: 31: as_shadow_match: not found
/home/cameron/.profile: 33: [scale]: not found
/home/cameron/.profile: 34: Syntax error: redirection unexpected
```


I don't know what I did that caused this to occur, but here is what I have tried so far: 


deleting the /home/cameron/.gnome folder 

I have reinstalled all of the following packages in Synaptic:
```
compiz (version 1:0.6.2+git20071119-0ubuntu1~gutsy1) will be re-installed
compiz-gnome (version 1:0.6.2+git20071119-0ubuntu1~gutsy1) will be re-installed
displayconfig-gtk (version 0.3.7) will be re-installed
gksu (version 2.0.0-4ubuntu2) will be re-installed
gtk2-engines (version 1:2.12.2-0ubuntu1) will be re-installed
gtk2-engines-pixbuf (version 2.12.0-1ubuntu3) will be re-installed
gtk2-engines-ubuntulooks (version 0.9.12-8) will be re-installed
libgtk2.0-0-dbg (version 2.12.0-1ubuntu3) will be installed
libgtk2.0-doc (version 2.12.0-1ubuntu3) will be installed
libio-stringy-perl (version 2.110-2) will be installed
libpod-escapes-perl (version 1.04-1) will be installed
libpod-simple-perl (version 3.04-1) will be installed
libgtk2-perl (version 1:1.140-1build1) will be re-installed
libgtk2.0-0 (version 2.12.0-1ubuntu3) will be re-installed
libgtk2.0-bin (version 2.12.0-1ubuntu3) will be re-installed
libgtk2.0-cil (version 2.10.2-1ubuntu2) will be re-installed
libgtk2.0-common (version 2.12.0-1ubuntu3) will be re-installed
libgtk2.0-dev (version 2.12.0-1ubuntu3) will be re-installed
```


Each time I boot i get a different process ID in the errors file. 




I posted this earlier with a bad title, and bad description, and got to solutions, so I thought it would be best to start from scratch:
[http://ubuntuforums.org/showthread.php?p=3864812#post3864812](http://ubuntuforums.org/showthread.php?p=3864812#post3864812) 

I have already reinstalled gutsy 3 times and before that reinstalled feisty even more just from messing around with things, but I have been careful this time and this time was not "pushing it to the limit" as i have before... so I really don't want to have to reformat again.

---

### Post by aliencam on 2007-11-30
SOLVED!!!

kind of a waste, surprised I didn't think of it before, and more or less a brute-force attempt at solving it, this worked: 

```
sudo apt-get install --reinstall gnome
```

i did that in the terminal in the failsafe gnome. 


the problems are that first of all it used up another 169MB of space, which doesn't matter, I have almost 1 TB of hard drive space scattered about my room (iPods & external HDDs included) and it took a few minutes to download (actually less than 3... yay for university dorm bandwidth!) but it did work. 

the first time i logged in after doing this gnome came up with an extremely old-gnome theme and I got this error: 
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

and everything was extremely slow (something to do with using xgl and not having compiz enabled i believe... it always happens if im not using beryl/compiz) 

but all I had to do was log out and log back in, and everything is back to normal.  

Hope this helps someone else. 
-aliencam.

---

### Post by klausner on 2007-12-17
Well it DIDN'T work for me. I've been having trouble ever since the security updates a few days ago. I can only log in in failsafe mode. My .xsession-errors looks like this:

```
(process:6014): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6018): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present.
xauth: (argv):1:  bad display name ":0" in "nextract" command
No matches found, authority file "-" not written
xauth: (argv):1:  bad "add" command line
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Mon Dec 17 20:05:09 2007: 6079 Xgl: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

xmodmap:  unable to open display ':1'
can't lock memory: Cannot allocate memoryWARNING: not using secure memory for passwords
AUDIT: Mon Dec 17 20:05:10 2007: 6079 Xgl: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

cannot open display:
Run '/usr/bin/seahorse-agent --help' to see a full list of available command line options.

```

I understand there is a setuid problem, but WHICH file is the problem? I did a global search for setuid permissions, but nothing jumps out as suspicious.

---

### Post by aliencam on 2007-12-18
you might want to try 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

i don't know if there could be an error in your /etc/X11/xorg.conf file, but that re configures it to the original. (this will erase any modifications you made to xorg.conf)

---

### Post by klausner on 2007-12-18
> you might want to try


```
sudo dpkg-reconfigure -phigh xserver-xorg

i don't know if there could be an error in your /etc/X11/xorg.conf file, but that re configures it to the original. (this will erase any modifications you made to xorg.conf)
```

Nope. No effect.

---

### Post by klausner on 2007-12-19
Well it broke for me with a security update, and now, today's update seems to have fixed things. Seems like Beta testing on Gutsy has gone way downhill.

---

