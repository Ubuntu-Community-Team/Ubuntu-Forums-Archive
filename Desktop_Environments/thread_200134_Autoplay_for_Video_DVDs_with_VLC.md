---
title: "Autoplay for Video DVDs with VLC?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Cyrus XIII on 2006-06-19
I've been playing around with KDE's options for automounting storage media. Neat feature but I just cannot figure out the syntax needed to play DVDs directly in VLC on mount. There is no help entry available so I'm a bit stuck here. My guess is, that the drive's device name must be parsed in order to complete the command "vlc dvd://[dev name]".

Any suggestions?

---

### Post by master_b on 2006-06-19
Check out 
[http://jamesthornton.com/linux/REF/VideoLAN-Quickstart/VideoLAN-Quickstart-2.html](http://jamesthornton.com/linux/REF/VideoLAN-Quickstart/VideoLAN-Quickstart-2.html)

from which I quote
"To make vlc read a DVD, you can tell him from the command line : 
% vlc dvd:/dev/dvd
where /dev/dvd is the device that corresponds to your DVD drive."

Personally, I'm trying to figure out how to get VLC to play DVD.isos from one PC tbut display (with audio) on another, without downloading from the ist (server) pc.

Good luck

Bill

---

### Post by Cyrus XIII on 2006-06-20
You got me wrong.

This about correctly configuring a custom service in the Removable Media module of the KDE Control Center.

---

### Post by disturbed1 on 2006-06-20
wxvlc dvd://

In VLC define the option for your default dvd device, mine is /dev/hdc. I also set the option to start in full screen on VLC so that when ever a dvd is inserted in out media PC, it's auto played and full screened with VLC :)

---

### Post by Cyrus XIII on 2006-06-20
Nope, KIOExec gave me the following error:

"/media/hdc is a folder, but a file was expected"

---

### Post by disturbed1 on 2006-06-20
[quote=Cyrus XIII]Nope, KIOExec gave me the following error:

"/media/hdc is a folder, but a file was expected"[/quote]

That's a correct error ;)

The run command is

wxvlc dvd://

In vlc, under the option define the dvd device

/dev/hdc

^^ an actual device, not a link ;).

---

### Post by Cyrus XIII on 2006-06-22
But I did... :-? 

I assume KDE's HAL backend passes the mount point to the application, even without any %-value in the command line.

---

### Post by disturbed1 on 2006-06-22
Don't know how exactly KDE does it, what Gnome does is this. DVD inserted? Run command "wxvlc dvd://"

"wxvlc dvd://" tells VLC you want to play a dvd with menus, and that dvd is in the default location defined in the VLC preferences.

What happens when you run 
wxvlc dvd://
from the command line?

---

### Post by Cyrus XIII on 2006-06-25
Starts the DVD right away. :(

---

