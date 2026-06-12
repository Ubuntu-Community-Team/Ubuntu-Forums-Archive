---
title: "KDE constant crash"
date: 2005-07-25
forum: Desktop Environments
---

### Post by maruchan on 2005-07-25
I have this annoying crash that happens every day or so, whether I'm in Gnome or KDE. I noticed that it tends to happen when I'm using Konversation, but I'm not exactly sure if that causes it.

The KDE crash handling system reports that "artsd" has crashed. I click "close" to close the crash handler window, but it pops up again every 5 seconds or so. Here is the output:

> Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1217965952 (LWP 22253)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#42 0xffffe410 in ?? ()
#43 0xbffff69c in ?? ()
#44 0x00000006 in ?? ()
#45 0x000056ed in ?? ()
#46 0xb7786175 in raise () from /lib/tls/i686/cmov/libc.so.6
#47 0xb77877d8 in abort () from /lib/tls/i686/cmov/libc.so.6
#48 0xbffff6b0 in ?? ()
#49 0x00000000 in ?? ()
#50 0x00000020 in ?? ()
#51 0x00000000 in ?? ()
#52 0x00000000 in ?? ()
#53 0x00000000 in ?? ()
#54 0x00000000 in ?? ()
#55 0x00000000 in ?? ()
#56 0x00000000 in ?? ()
#57 0x00000000 in ?? ()
#58 0x00000000 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000000 in ?? ()
#61 0x00000000 in ?? ()
#62 0x00000000 in ?? ()
#63 0x00000000 in ?? ()
#64 0x00000000 in ?? ()
#65 0x00000000 in ?? ()
#66 0x00000000 in ?? ()
#67 0x00000000 in ?? ()
#68 0x00000000 in ?? ()
#69 0x00000000 in ?? ()
#70 0x00000000 in ?? ()
#71 0x00000000 in ?? ()
#72 0x00000000 in ?? ()
#73 0x00000000 in ?? ()
#74 0x00000000 in ?? ()
#75 0x00000000 in ?? ()
#76 0x00000000 in ?? ()
#77 0x00000000 in ?? ()
#78 0x00000000 in ?? ()
#79 0x00000000 in ?? ()
#80 0x00000000 in ?? ()
#81 0x00000000 in ?? ()
#82 0xb77c9307 in _IO_file_write () from /lib/tls/i686/cmov/libc.so.6


I started killing KDE processes out of desperation, and killing KNotify seemed to get rid of all the error popups this time.

Can anybody help me fix this?

---

### Post by Xian on 2005-07-25
That really appears to be just a basic sound conflict. 
In your KDE Control Center what setting do you have for the following:

Sound & Multimedia > Sound System > Auto Suspend

Tick the box and try setting it to just 1 second.

---

### Post by maruchan on 2005-07-26
Thanks for the reply. Actually, it was set to 60 seconds. I changed it to 1 second - why would this matter though?

---

### Post by PhilippWollermann on 2005-07-27
Well, if your soundcard hasn't got a hardware mixer, no other application will be able to output sound, when artsd is running and uses the card. No app should crash, just because it isn't able to use the soundcard, but.. they do, even if they shouldn't. ;) If you set suspend time to 1 second, the chances are big, that arts "unlocks" the card, so that the other app won't crash.

But I'm not that sure, if this is the reason, why your KDE is crashing.. after all, Konversation is a KDE app too and uses arts. Did you upgrade to KDE 3.4.1? Which soundcard are you using? (If you don't know, open a terminal, do a "sudo lspci" and post the output here)

Philipp

---

### Post by maruchan on 2005-07-27
Thanks for the help...for some reason I can't get any sound out of Konversation at all now.

My sound card is an SB Audigy (series 1). KDE version is 3.4.1.

---

### Post by maruchan on 2005-07-27
I should amend that - I cannot get any system sounds to work in KDE. The "test sound" works, but that's it. Strange!

---

### Post by PhilippWollermann on 2005-07-31
Mmh.. I have no idea what may cause this.. :-( You could try to explicitly set ALSA as the sound output device in KControl -> Sound System. Try to look at the status of arts, using the program "artscontrol", in the main menu click on "arts status". If you play a sound in KDE, the sound server shouldn't be suspended.

Philipp

---

### Post by maruchan on 2005-08-01
Thanks for the artscontrol tip! It says Arts is suspended so that legacy applications can use sound. Now, I remember following an Ubuntu HOWTO that made sound (midi?) work better, but seemed to disable system sounds, if I recall. 

How can I unsuspend Arts?

---

