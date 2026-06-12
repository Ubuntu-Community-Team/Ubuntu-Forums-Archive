---
title: "Mouse Triggering Accidental Shutdown"
date: 2009-01-23
forum: General Help
---

### Post by odelay on 2009-01-23
After nearly driving me mad, I found a pattern behind my "random" power downs I was experiencing in 8.10.  They seem to be related to the new Apple Mighty Mouse I found lying around the office.  I'm able to reproducibly trigger [COLOR="Red"]X to stop[/COLOR] by clicking the "back" of the mouse (the part closest to you).  Weird.

[COLOR="Red"]**Edit**[/COLOR]: For those jumping onto this thread, feel free to ignore what I originally wrote below.  In essence, the problem is the "middle click" button on the Mighty Mouse triggers the equivalent of "stop x".

When it shuts off, it doesn't go through the typical shutdown sequence...a black screen with text immediately appears:
```
* Starting System Tools Backends system-tools-backends		[OK]
* Starting anac(h)ronistic cron anacron				[OK]
* Starting deferred execution scheduler atd			[OK]
* Starting period command sceduler crond			[OK]
* Enabling additional executable binary formats binfmt-support	[OK]
* Checking battery state...
/dev/sda:
 Setting Advanced Power Management level to 0xfe (254)
								[OK]
```

[COLOR="Gray"]I don't know if this is specific to Apple's Mighty Mouse or what.  Around this same time I started getting an error on booting my Dell e1505 about not having a 60W power supply connected...I disabled this message so I can't give you the exact text.  Perhaps the power strip I very recently started using is being over-taxed ([COLOR="Red"]Edit[/COLOR]: unlikely, considering it's clearly mouse-triggered).  On top of all the other variables, I also started using a second monitor via ATI Catalyst Control Center.  As you might have guessed, I just moved my laptop into a new office so I'm having a terrible time separating all the recent changes.

I coudln't find anyone else with this problem, which isn't encouraging.  I'll be away from my computer for the weekend in a few hours, but I'll do my best to provide any additional information.[/COLOR]

Thanks a million!

---

### Post by dcstar on 2009-01-23
> **odelay said:**
> After nearly driving me mad, I found a pattern behind my "random" power downs I was experiencing in 8.10.  They seem to be related to the new Apple Mighty Mouse I found lying around the office.  I'm able to reproducibly trigger Ubuntu to power down by clicking the "back" of the mouse (the part closest to you).  Weird.

When it shuts off, it doesn't go through the typical shutdown sequence...a black screen with text immediately appears.  It contains keywords like "boot" and "anachron" and the final line is:
```
/dev/sda:
Setting Advanced Power Management level to 0xfe (254)
```

I don't know if this is specific to Apple's Mighty Mouse or what.
........

Press CTRL-ALT-F8 after booting up and logging in and you will probably see that screen, it is just the output of the startup sequence. You are only seeing it because something in the shutdown sequence is killing your X session on the way to closing down the PC.

Check what is set to trigger shutdowns/hibernate etc, you may well have a mouse code set to trigger these events.

---

### Post by odelay on 2009-01-23
Sorry, I'm not sure where a "mouse shortcut" could be.  I didn't see anything peculiar in Prefs > Keyboard Shortcuts.

I went into Prefs > SCIM Input Methods Setup and found this in Front End> Global Setup > Trigger:
Control+space,Alt+grave,Zenkaku_Hankaku,Hangul

But it doesn't say what it's triggering.

I'm totally forgetting the name of the file that has all the mouse/inputs prefs in it.

**[COLOR="Red"]Edit[/COLOR]**: I checked /etc/X11/xorg.conf and there wasn't a section for a mouse input.

---

### Post by odelay on 2009-01-23
I should also add that if I manually shutdown the computer it goes through the proper shutdown sequence.  This screen only comes up through the mouse error.

Knowing the Apple mouse, it was also my hunch that some "extra" click was binded to something--I just don't think it could be the regular Shutdown.  

BTW, the click I'm referring to isn't the "side-squeeze" click.  It works the "best" when I invert the mouse and tap the back-bottom surface.

Again, thanks so much

---

### Post by HyperHacker on 2009-01-23
When that happens, on next bootup look at /var/log/syslog and /var/log/kern.0.log. Those might contain some information about what caused the shutdown.

---

### Post by odelay on 2009-01-23
I'm about to check that...thanks.

This is extremely weird.  After seemingly no change, when I perform the mouse-click it's bringing me to the Login Screen now.  I disabled the Log Out shortcut (Ctrl-Alt+Del) to no avail.  Even more unusual, the Log Out only happens when the mouse is on my Primary Screen, and doesn't trigger anything on my secondary desktop.  ???

**[COLOR="Red"]Edit[/COLOR]**:  Pressing Ctrl-Alt+F8 switches to the same screen as before.  Ctrl-Alt+F7 switches back to the virtual screen running X.  So I was wrong about the computer shutting down...it was just changing virtual screens...or whatever they're called.  Unfortunately, it's now logging out as I mentioned.  Where on earth (other than Prefs > Keyboard Shortcuts) could a mouse click get binded to either Logging Out or Ctrl-Alt+F8??

---

### Post by odelay on 2009-01-23
> **HyperHacker said:**
> When that happens, on next bootup look at /var/log/syslog and /var/log/kern.0.log. Those might contain some information about what caused the shutdown.

This occurred between performing the mouse click and subsequently logging back into gdm.  I find it odd that it mentions compiz...since I'm not using it.  A few days ago (not sure why...curiosity?) I ran 'apt-get install compiz' which didn't seem to do anything.

```
Jan 23 17:05:04 ubuntubook kernel: [ 7104.672235] compiz.real[12361]: segfault at 2 ip 08055c8c sp bfa91ec0 error 4 in compiz.real[8048000+34000]
Jan 23 17:05:04 ubuntubook gdm[12098]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jan 23 17:05:05 ubuntubook acpid: client connected from 13241[0:0] 
Jan 23 17:05:07 ubuntubook kernel: [ 7108.048876] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jan 23 17:05:07 ubuntubook kernel: [ 7108.048889] [fglrx] Reserved FB block: Unshared offset:7fb7000, size:44000 
Jan 23 17:05:07 ubuntubook kernel: [ 7108.048892] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
Jan 23 17:05:09 ubuntubook gdmgreeter[13275]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Jan 23 17:05:19 ubuntubook pulseaudio[13359]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 23 17:05:19 ubuntubook pulseaudio[13361]: pid.c: Stale PID file, overwriting.
Jan 23 17:05:19 ubuntubook pulseaudio[13361]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 23 17:05:19 ubuntubook pulseaudio[13361]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 23 17:05:30 ubuntubook x-session-manager[13299]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Jan 23 17:05:40 ubuntubook x-session-manager[13299]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jan 23 17:05:40 ubuntubook pulseaudio[13361]: module-x11-xsmp.c: X11 session manager not running.
Jan 23 17:05:40 ubuntubook pulseaudio[13361]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 23 17:05:41 ubuntubook anacron[13617]: Anacron 2.3 started on 2009-01-23
Jan 23 17:05:41 ubuntubook anacron[13617]: Normal exit (0 jobs run)
Jan 23 17:05:41 ubuntubook kernel: [ 7141.685100] CPU0 attaching NULL sched-domain.
Jan 23 17:05:41 ubuntubook kernel: [ 7141.685112] CPU1 attaching NULL sched-domain.
Jan 23 17:05:41 ubuntubook kernel: [ 7141.701095] CPU0 attaching sched-domain:
Jan 23 17:05:41 ubuntubook kernel: [ 7141.701104]  domain 0: span 0-1 level MC
Jan 23 17:05:41 ubuntubook kernel: [ 7141.701107]   groups: 0 1
Jan 23 17:05:41 ubuntubook kernel: [ 7141.701114] CPU1 attaching sched-domain:
Jan 23 17:05:41 ubuntubook kernel: [ 7141.701117]  domain 0: span 0-1 level MC
Jan 23 17:05:41 ubuntubook kernel: [ 7141.701119]   groups: 1 0
```

---

### Post by Yashiro on 2009-01-23
Try changing your desktop theme back to 'Human'.

---

### Post by odelay on 2009-01-27
> **Yashiro said:**
> Try changing your desktop theme back to 'Human'.

I tried that to no avail.

I also fully removed compiz to no avail.

Thanks for the help--I'm out of ideas!

---

### Post by odelay on 2009-03-20
Bump.  See edit to original post.  Any and all help appreciated!

---

