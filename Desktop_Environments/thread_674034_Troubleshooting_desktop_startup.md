---
title: "Troubleshooting desktop startup"
date: 2008-01-21
forum: Desktop Environments
---

### Post by cmulcahy on 2008-01-21
Hey, all.

My wife's profile on our system is no longer working properly.  I am using Ubuntu 7.10 with Kubuntu-desktop installed.  KDE is my preferred environment.  When she enters her username/password, it immediately returns her to the login screen.  This happens whether she chooses KDE, Gnome or anything else.  It happens within a second or two, no major pauses.

.xsession-errors has a last modified date/time of January 19th, two days ago, approximately when the problem started.  This file has not been touched with any errors from today's attempts.

Here is the last few lines anyway:

```

SNIP a few hundred "refresh" messages
refresh
refresh
refresh
refresh
refresh
refresh
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
kwin: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
kio_uiserver: Fatal IO error: client killed
kblueplugd: Fatal IO error: client killed
kded: Fatal IO error: client killed
kicker: Fatal IO error: client killed
kmix: Fatal IO error: client killed
kweatherservice: Fatal IO error: client killed
knotify: Fatal IO error: client killed
klipper: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
kaccess: Fatal IO error: client killed
konqueror: Fatal IO error: client killed
amarokapp: Fatal IO error: client killed
The application 'gecko' lost its connection to the display Annette-Remote.local:1.0;
most likely the X server was shut down or you killed/destroyed
the application.
kdeinit: sending SIGHUP to children.
klauncher: Exiting on signal 1
kicker: sighandler called
warning: leaving MCOP Dispatcher and still 14 object references alive.
  - Arts::SampleStorage
  - Arts::Synth_MULTI_ADD
  - Arts::Synth_MULTI_ADD
  - Arts::Synth_PLAY
  - Arts::StereoVolumeControl
  - Arts::StereoEffectStack
  - Arts::Synth_BUS_DOWNLINK
  - Arts::SoundServerV2
  - Arts::Synth_BUS_UPLINK
  - Arts::AudioManagerClient
  - Arts::Synth_AMAN_PLAY
  - Arts::Synth_BUS_UPLINK
  - Arts::AudioManagerClient
  - Arts::Synth_AMAN_PLAY
warning: leaving MCOP Dispatcher and still 151 types alive.
*** kdesktop got signal 1 (Exiting)
klauncher: Fatal IO error: client killed
kdeinit: sending SIGTERM to children.
kdeinit: Exit.
kicker: sighandler called

```

It looks like a bunch of KDE components died and has not come back since.  

I am uncertain where else to look for troubleshooting.  My profile is working fine so the system should be OK.  It is just hers.

Any help is appreciated!

---

### Post by cmulcahy on 2008-01-21
Replying to myself, sorry.

One more bit of info.  No files in her home directory have been updated since the 19th.  

Here's the top bit of `ls -lat`:

```
-rw-------   1 annette annette  638207 2008-01-19 09:41 .xsession-errors
-rw----rw-   1 annette annette     169 2008-01-19 09:41 .Xauthority
drwx---rw-  16 annette     408    4096 2008-01-18 11:14 .opera
-rw-r--r--   1 annette annette   33151 2008-01-13 11:59 .recently-used.xbel
drwxr-xrw-  16 annette     408    4096 2008-01-13 11:53 .gnome2
-rw----rw-   1 annette annette      31 2008-01-13 11:53 .mcoprc
```

[EDIT]  As I mentioned in the thread of another person experiencing the same problem, I have created a brand new user which is exhibiting the same behavior.  I believe that if I were to log out of my own session, I would experience the same behavior on my own profile.

---

### Post by cmulcahy on 2008-01-21
By the way, I'm using KDM.  

I have asked on the irc forum and was unable to resolve my issue.  It is still an issue with a system outage for me.  I see several other unresolved threads over the last few days about this problem.  I'm not sure if I am happy that others are experiencing it or not..

---

### Post by cmulcahy on 2008-01-21
Not sure how widespread this problem is, but Jimbo99 just posted a message about the xorg being updated recently which caused several problems such as I and several others reported.  I am going to try reinstalling the video drivers.

Unfortunately, I am extremely confused about the video drivers with respect to nvidia.  

With all of the different nvidia driver options between free, non-free, glx, etc.  I am uncertain which ones I used.  I remember I putzed around for a while until I stumbled on a working combination.

Since I am about to risk my config again, what is recommended?  Please let me know what package is recommended and what the xorg.conf configuration is that is recommended.

Thanks for any help!

From lspci:
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600XT] (rev a1)

---

### Post by cmulcahy on 2008-01-21
Wow, a thread all to myself!  :)

So far, I have been unsuccessful.  The video driver update did not seem to resolve my problem.  Anyone else gotten past the problem yet?

Thanks
Chris

---

