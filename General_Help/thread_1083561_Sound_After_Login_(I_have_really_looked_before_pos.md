---
title: "Sound After Login (I have really looked before posting)"
date: 2009-03-01
forum: General Help
---

### Post by ibob_gr on 2009-03-01
I had 8.04 and updated to 8.10.

In 8.04 I had the login sounds disabled. In 8.10 I disabled the sound gdm does when the user is prompted for credentials, but I didn't manage to disable the sound after login.

I know there is a GUI solution (System->Administration->Login Window->Accessibility) but I want to be able to reproduce the change. Please either give me a non-GUI solution or tell me what configuration files this GUI changes.

```
/etc/gdm$ sudo grep Sound *

gdm.conf:SoundProgram=/usr/lib/gdmplay
gdm.conf:# If SoundOnLogin is true, then the greeter will beep when login is ready for
gdm.conf:# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
gdm.conf:# executable (see daemon/SoundProgram) it will play that file instead of just
**gdm.conf:SoundOnLogin=false**
gdm.conf:SoundOnLoginFile=/usr/share/sounds/question.wav
gdm.conf:# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
**gdm.conf:SoundOnLoginSuccess=false**

gdm.conf-custom:SoundOnLogin=false

gdm.conf.dpkg-old:SoundProgram=/usr/lib/gdmplay
gdm.conf.dpkg-old:# If SoundOnLogin is true, then the greeter will beep when login is ready for
gdm.conf.dpkg-old:# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
gdm.conf.dpkg-old:# executable (see daemon/SoundProgram) it will play that file instead of just
gdm.conf.dpkg-old:SoundOnLogin=false
gdm.conf.dpkg-old:SoundOnLoginFile=/usr/share/sounds/question.wav
gdm.conf.dpkg-old:# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
gdm.conf.dpkg-old:SoundOnLoginSuccess=false
gdm.conf.dpkg-old:#SoundOnLoginSuccessFile=
gdm.conf.dpkg-old:# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
gdm.conf.dpkg-old:#SoundOnLoginFailure=false
gdm.conf.dpkg-old:#SoundOnLoginFailureFile=

gdm.conf.save:SoundProgram=/usr/lib/gdmplay
gdm.conf.save:# If SoundOnLogin is true, then the greeter will beep when login is ready for
gdm.conf.save:# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
gdm.conf.save:# executable (see daemon/SoundProgram) it will play that file instead of just
gdm.conf.save:SoundOnLoginFile=/usr/share/sounds/question.wav
gdm.conf.save:# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
gdm.conf.save:#SoundOnLoginSuccess=false
gdm.conf.save:#SoundOnLoginSuccessFile=
gdm.conf.save:# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
gdm.conf.save:#SoundOnLoginFailure=false
gdm.conf.save:#SoundOnLoginFailureFile=
```

---

### Post by ibob_gr on 2009-03-04
Since I couldn't find a response I simply created a new /usr/share/sounds/ubuntu/stereo/desktop-login.ogg  which is a muted sound file. 

If you have any idea how to configure this issue, I would really like to hear it :)

---

### Post by wyth on 2009-03-05
> **ibob_gr said:**
> Since I couldn't find a response I simply created a new /usr/share/sounds/ubuntu/stereo/desktop-login.ogg  which is a muted sound file. 

If you have any idea how to configure this issue, I would really like to hear it :)


Check
```
System > Preferences > Sounds
```All the system sounds are under the Sounds tab in that gui.

---

### Post by ibob_gr on 2009-03-16
> **wyth said:**
> Check
```
System > Preferences > Sounds
```All the system sounds are under the Sounds tab in that gui.

All sounds are disabled in this gui, yet the sound after login still plays :)

Do you happen to know where to disable it in a conf file? I want to reproduce the change in 70 computers, so I can't go in 70 different guis... (the only massive change I did was muting the sound file itself :P, crappy - and in order to check your trick I did reverted the file in its original form)

---

### Post by ibob_gr on 2009-06-09
I bring this thread up again, since no one replied for a month or so. 

Any ideas how to setup the login sound **WITHOUT** the Gui? From the config file?

---

### Post by sedawk on 2009-06-09
Welcome to the jungle!  (of gnome config files)

I hope this trick helps:

1) Create a new user (so you do not have too much data in
  his/her home directory).
2) rsync the whole home directory of that user to another location.
   (e.g. in a terminal with sudo rsync -rv /home/newuser /dev/shm/testing/)
3) Change some settings from gui (try to disable that sound for
   the new user. Do one change at a time).
4) run rsync again (use -rvn flag first to see which files will be
   changed without doing the real change).
   This should give you a good idea which files are changed when
   changing sound preferences
   (e.g. in gnome-control-center->Sound->Login/Logout).
   You can view changes with (of files or whole directories) 
   diff /home/newuser/... /dev/shm/testing/newuser/...

To check for changed files (without that nice "history" the above
solution gives you) you can simply do this:

a) Create a file "just_now" with "touch just_now" in your home directory
b) Do the change with the gnome GUI
c) run "find . -newer just_now -print"
This will show all files that are newer (modification time) than file
"just_now". You see which files have changed (but not what changed)

Hope that helps!

---

