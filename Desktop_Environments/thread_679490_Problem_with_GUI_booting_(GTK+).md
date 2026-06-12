---
title: "Problem with GUI booting (GTK+)"
date: 2008-01-27
forum: Desktop Environments
---

### Post by Spaelus on 2008-01-27
Hi, I got this message after enter my username/password :
> 
(process:6646) : Gtk-WARNING **: This process is currently running stuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead.  For further details, see:

	[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6650) : Gtk-WARNING **: This process is currently running stuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead.  For further details, see:

	[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning sessions setup...
x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

I got this message after restarting my laptop (Toshiba U300-NS5).  I was trying to get the sound working.  I restart it because, after closing the terminal, I wasn't able to open it anymore.  When I clicked on the terminal icon, all I saw was the "window" Opening (or Starting) Terminal and then nothing the window disappear with no terminal.  
Exactly, I was doing the procedure for the sound found there : [http://www.matusiak.eu/numerodix/blog/index.php/2007/10/31/gutsy-on-the-toshiba-u300/](http://www.matusiak.eu/numerodix/blog/index.php/2007/10/31/gutsy-on-the-toshiba-u300/)
I closed the terminal when the ./install command was finish.

Can someone help me?  By the way it's the fist time I use linux, I installed Ubuntu 7.10 last week, so I'm not really good with linux command yet.

---

### Post by mali2297 on 2008-01-27
You can ignore the gtk warnings, the critical error was stated last:
> 
x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory


Did you try what was suggested in the last update?
```

sudo apt-get install linux-backports-modules-generic

```

If that doesn't solve the problem, post the output of
```

locate libasound.so
aplay -l
lspci -v | grep -A5 [Aa]udio
uname -a

```

---

### Post by breaking on 2008-01-27
Are you sure, mali2297?  If you look around the forums there are several other people having very similar problems who do not have the asound error, or even any other "error" appearing at all, but *do* have those same warnings.

For example, what I'm getting is:
> (process:15040): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:15044): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.Note the complete absence of any kind of "error" in there at all, or any reference to libasound.  The only thing my log has in common with Spaelus' log is those GTK warnings, and everyone else who's having this problem also seems to have those warnings, so it seems a bit hasty to completely rule out any possibility that they relate to the problem!

---

### Post by mali2297 on 2008-01-27
> **breaking said:**
> Are you sure, mali2297?  If you look around the forums there are several other people having very similar problems who do not have the asound error, or even any other "error" appearing at all, but *do* have those same warnings.

For example, what I'm getting is:
Note the complete absence of any kind of "error" in there at all, or any reference to libasound.  The only thing my log has in common with Spaelus' log is those GTK warnings, and everyone else who's having this problem also seems to have those warnings, so it seems a bit hasty to completely rule out any possibility that they relate to the problem!

OK, I didn't know that this was a common problem. Perhaps you could post links to the other threads.

---

### Post by Spaelus on 2008-01-27
I've done what mali2297 told me and it's didn't change anything.  Here the output :

> 
locate libasound.so =>

aplay -1 => aplay -1: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

lspci -v | grep -A5 [Aa]udio => 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0700000 (64-bit, non-prefetchable) [size=16k]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0

uname -a => Linux Sovereign 2.6.22-14-generic #/ SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux


Every time I try to logging in the GUI, I get different precces error.  (i.e. process:6707 or 6711)

Is there a way to undo the change I've done?  I don't know if there a way to repair file with the installation CD.  I tried but I wasn't able to find that option.

---

### Post by PeterJS on 2008-01-27
This is the third thread like this I've seen, I was hoping somebody here knew what was going on. My original theory that didn't stand up was that the session manager as trying to restart something like synaptic, or the update manager, with elevated privliages and GTK was having none of it (ie the setuid error). After a bunch of boondoggles involving the gnome session manager nothing has come of it.

---

### Post by mali2297 on 2008-01-27
At the login screen, look through the options menu and choose the failsafe session. Then try to login.

If that does not work, boot into recovery mode and start the GUI with
```

startx

```

These are two similar threads:
[http://ubuntuforums.org/showthread.php?t=678038](http://ubuntuforums.org/showthread.php?t=678038)
[http://ubuntuforums.org/showthread.php?t=678846](http://ubuntuforums.org/showthread.php?t=678846)

Are there any more?

---

