---
title: "What's in a gnome splash screen"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by mulno on 2007-04-22
Hello,

I tried to use one of my own images for gnome splash screen. I used gTweakUI to set it. When I login, the image is shown but a window pops up telling me that the session has exited after less then 10 seconds. The applications of the session are started anyway and new applications can be started using the top panel. But no gnome-session is running.
The errorlog in .xsession-errors shows the following:

[INDENT]/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "norbert"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/norbertslaptop:/tmp/.ICE-unix/6371
Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>
Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>
Initializing gnome-mount extension
Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>

(nm-applet:6484): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6487): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
(gnome-volume-manager:6485): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
Session management error: IO error occured opening connection

(gnome-power-manager:6483): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

[/INDENT]

Resolution of the image is 72x72 dpi
Using images from art.gnome.org works fine.
Is there anything I can do to make an image usable as gnome splash screen?


Hints would be appreciated!
Norbert

---

### Post by tomfin on 2007-04-24
Not able to help (...yet) but just want to confirm this - changing my splash screen also produced this error.

It may be useful for those who are hunting for a cure to the "GnomeUI-WARNING **:....  IO error occured opening connection" error, as I was.  I'm a relative newbie and had suspected problems between Beryl and my Nvidia 5600 binary driver, having installed [Ext2 Filesystem for Windows]("http://www.fs-driver.org/") (i.e. by inadverently setting my / partition to read-only), or changing the splash screen.  Of the three, changing the Gnome splash screen seemed the most unlikely to cause problems, but there you go... that's what it was.

I used instructions from the Ubuntu Forums [here]("http://ubuntuforums.org/showthread.php?t=11478") to install [this splash logo]("http://art.gnome.org/themes/splash_screens/1217").  After installing I restarted the X server with Ctrl-Alt-Backspace and everything seemed fine so I shut it off for the night.

After logging in the next day, I got these error messages:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tom"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/behemoth:/tmp/.ICE-unix/7947
Initializing gnome-mount extension

(evolution-alarm-notify:8045): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:8046): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 20110 1177459200 1177439090
evolution-alarm-notify-Message:  Wed Apr 25 01:00:00 2007

evolution-alarm-notify-Message:  Tue Apr 24 19:24:50 2007


(update-notifier:8033): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tom"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/behemoth:/tmp/.ICE-unix/5950
Initializing gnome-mount extension

(gnome-panel:6016): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x0820f9e0 ***
```

I think the second message either appeared 'under' the first and was shown after clicking OK, or was shown when logging in with the 'Failsafe Gnome' session.  On startup, the Metacity windows manager displayed the error message, then Beryl-Manager loaded long enough to take the borders and titlebars off all windows before disappearing from the panel.  Yikes.  Clicking the OK button on the error message took me back to the Login Screen, but I could still run most things from the top menu if I left the error message alone.  I couldn't open "gnome-session-properties" to disable startup items.

After finding your post, I realised that renaming the splash image file I had set up at "/home/username/.gnome/splash.png" so that it would not be found and loaded might help.  Doing this and restarting the X server got everything working again with no further effort, the Login splash image has reverted to a Blue-ish Gnome Foot rather than the Ubuntu default but I'm not too bothered by that at the moment.

Thought I'd post this as I seem to have the same result as you, but used gconf-editor to break it directly instead of gTweakUI.  There seem to be some others who are having similar problems, too.

Some System Information:
Ubuntu 7.04 Feisty, 
Gnome 2.18.1, Kernel 2.6.20-15-generic
XOrg 7.2.0 (04 April 2007)
NVidia GeForce FX5600XT 256mb (binary drivers installed via Synaptic)
ASRock K7S8X Motherboard
AMD Athlon(tm) XP 2500+, 1GB RAM
Installation just a few days old....

Anyone else have any ideas why the Splash is causing problems?  I have a few suspicions but I'm not toying with it any further today, just relieved to have my snazzy desktop back for now.

Hope that helps,

Tom

---

### Post by Cervantez on 2007-04-24
Beryl is incompatible with Gnome Splash Screens. You'll notice that if you disable Beryl on startup then you will see your gnome splash screen.

Btw, did you use gnome-splashscreen-manager to install your splashscreen?

---

### Post by mulno on 2007-04-29
I have the reported problems without using Beryl

---

### Post by qamelian on 2007-04-29
> **Cervantez said:**
> Beryl is incompatible with Gnome Splash Screens. You'll notice that if you disable Beryl on startup then you will see your gnome splash screen.

Btw, did you use gnome-splashscreen-manager to install your splashscreen?

Is this documented somewhere? I use Beryl and Gnome splash screens together without a problem. On both my systems Beryl runs on startup and the Gnome splash screen functions fine.

---

### Post by seamus7 on 2007-05-05
I just reinstalled Feist two days ago. Just an hour or so ago I tried changing some themes: gnome splash, login and icons. I've done this before in previous installations of Feisty, Edgy and Dapper. No problems. But this time, when I restarted to see the new themes, I was kicked back to the login screen after logging in. Error message was something like:

~/.xsession-errors blah blah blah blah blah blah and so forth and so forth

I immediately thought: something about the new themes isn't playing well with my system. I began searching these forums but I only found advice to chown certain files or do a complete reinstall or create a test user... blah blah blah ... I wasn't about to do a whole new reinstall ... I had just screwed up my system royally a couple days ago through admitted stupidity but this time i thought: this has got to be a relative simple fix!

I found someone who had a similar experience and decided to simply uninstall all the new themes. I did likewise. And guess what... everything is back to normal. YEAH! I didn't have to reinstall Feisty.

My message to you: don't autmatically assume you need to do a complete reinstall. Search the forums carefully and use logic to backtrack. Don't make major changes to your system in trying to fix it. First, gather information. Usually, if I search long enough and smart enough, I will eventually find that Aha! forum thread which will explain my problem.

If this doesn't apply to you. Sorry.

---

