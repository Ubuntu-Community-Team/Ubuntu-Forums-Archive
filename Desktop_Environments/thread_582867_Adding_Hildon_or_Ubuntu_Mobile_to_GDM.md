---
title: "Adding Hildon or Ubuntu Mobile to GDM"
date: 2007-10-20
forum: Desktop Environments
---

### Post by deadguy87 on 2007-10-20
Is it possible to have Ubuntu mobile in the Session list on GDM. I have the packages installed already just can't find a way to run it as the native desktop manager.

---

### Post by deadguy87 on 2007-10-21
bump. I think I need to find the equivalent of gnome-session or matchbox-session. Any help?

---

### Post by rcoconnell on 2007-10-27
Which packages did you install?  I'd like to try Hildon out, but I'm not sure where to start.  I've got a Ramline touchscreen pc set up in my kitchen.  It's running xfce right now, but I'd be interested in a proper touchscreen interface.  Does it run on top of matchbox?  Is it separate?

Is Hildon ready for primetime?  I thought that the Mobile and Embedded stuff was going to be working in Gutsy, but some launchpad documents make it sound like part of it won't work until Hardy is released.

---

### Post by malaprohibita on 2007-12-14
Curious about this myself, if there are any updates.

---

### Post by Thomaseov on 2008-01-02
I'm in a similar situation...ttrying to get a small via system with 8" touchscreen going using UME.  I've installed packages but...how do I run a session?  Anyone?

---

### Post by edrex on 2008-01-07
I'm experimenting with UME on my lifebook w/touch.

Remember, UME is early pre-alpha or somesuch, it will probably break! That said, I'm not using a chroot, or a seperate user, cuz I'm reckless.

[https://wiki.ubuntu.com/MobileAndEmbedded/HildonDesktopManualProcedure](https://wiki.ubuntu.com/MobileAndEmbedded/HildonDesktopManualProcedure)

In the guide they use a chroot env. To get hildon running inside xephyr I just did:
```
sudo aptitude install ubuntu-mobile xserver-xephyr
Xephyr :1 -host-cursor -screen 800x480x16 -dpi 96 -ac
start-hildon
```

Now to create an Xsession for hildon. The start-hildon script has display :1 hardcoded.

Create the file /usr/share/xsessions/hildon.desktop containing
```
[Desktop Entry]
Encoding=UTF-8
Name=Hildon
Exec=/usr/local/bin/start-hildon-session
Type=Application
```

Copy the hildon startup script:
```
sudo cp `which start-hildon` /usr/local/bin/start-hildon-session
```
Edit /usr/local/bin/start-hildon-session to change the line
```
export DISPLAY=:1
```
to
```
#export DISPLAY=:1
```
($DISPLAY should already be set by gdm)

Restart GDM.  I'm just typing up this procedure as I do it. Will update after.

---

### Post by edrex on 2008-01-07
Well, I'm posting using MidBrowser from a GDM session of hildon, so it appears to have worked. The hildon desktop still wants to be 800x480, but other windows use the full screen. I will use for a week or so and post my experiences. Also, if you have a touchscreen device (otherwise running UME doesn't make much sense) check out my forum post on setting it up and calibrating it using evtouch. Oh, and don't try this with your main user account, since it'll probably screw up your gtkrc or some such.

---

### Post by edrex on 2008-01-07
UME is pretty badly broken at this stage. By all means, try it out with Xephyr, but don't expect to be able to use it as your regular environment.

---

