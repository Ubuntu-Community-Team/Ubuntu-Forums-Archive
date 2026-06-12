---
title: "sudo konqueror (Solved)"
date: 2005-11-01
forum: Desktop Environments
---

### Post by phil66 on 2005-11-01
When I type "sudo konqueror" in konsole the screen displays the following message

Error:"/var/tmp/kdecache-(user)" is owned by uid 1000 instead of uid 0  Link points to "/var /tmp/kdecache-root"

"/tmp/kde-(user) link points to "/tmp/kde-root

"/tmp/ksocket-(user) link points to "/tmp/ksocket-root"

Message prints out a number of times then goes ahead and open "konqueror"

How do I correct this error

Thanks 
Ray

---

### Post by aysiu on 2005-11-01
kdesu konqueror

---

### Post by jeremy on 2005-11-02
kdesu konqueror gives me this:

kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: 'overview.desktop' specifies undefined mimetype/servicetype 'KitchenSync/ActionPart'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-math.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish-project.desktop' specifies undefined mimetype/servicetype '
application/bluefish-project'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-javascript'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/ser
vicetype 'text/x-python'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-perl'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 't
ext/x-php'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'application/x-cgi'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/math
ml'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-dtd'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-sql'
kbuildsycoc
a: WARNING: '/usr/share/applications/kde/konversation.desktop' specifies undefined mimetype/servicetype 'DCOP/InstantMessenger;DCOP/Unique'
kbuildsycoca: WARNING: 'kfile_ooo.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer
.global'
kbuildsycoca: WARNING: 'kfile_ooo.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: 'klinkstatus_part.desktop' specifies undefined mimetype/servicetype 'text/english'
kbuildsycoca: WARN
ING: 'klinkstatus_part.desktop' specifies undefined mimetype/servicetype 'text/x-c'
kbuildsycoca: WARNING: 'klinkstatus_part.desktop' specifies undefined mimetype/servicetype 'text/x-c++'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'application/rdf+xml'

kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav-p
refer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/kde/amarok.desktop' specifies undefined mimetype/servicetype 'audio/midi'
kbuildsycoca: WARNING: '/usr/share/applications/kde/amarok.desktop' specifies undefined mimetype/servicetype 'audio/
x-aac'
kbuildsycoca: WARNING: '/usr/share/applications/kde/amarok.desktop' specifies undefined mimetype/servicetype 'audio/x-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/kde/amarok.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-real
audioaudio/x-scpls'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'KMediaPart'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: 'gstre
amer_part.desktop' specifies undefined mimetype/servicetype 'audio/x-ogg'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies unde
fined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuild
sycoca: WARNING: '/usr/share/applications/kde/krita.desktop' specifies undefined mimetype/servicetype 'image/x-xcf'
kbuildsycoca: WARNING: 'kcertpart.desktop' specifies undefined mimetype/servicetype 'application/binary-certificate'
kbuildsycoca: WARNING:
 '/usr/share/applications/kde/kaffeine.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/kde/kaffeine.desktop' specifies undefined mimetype/servicetype 'audio/x-ogg'
kbuildsycoca: WARNING: '/u
sr/share/applications/kde/kaffeine.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: '/usr/share/applications/kde/kaffeine.desktop' specifies undefined mimetype/servicetype 'video/msvideo'
kbuildsycoca:
 WARNING: '/usr/share/applications/kde/kaffeine.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: '/usr/share/applications/kde/kaffeine.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARN
ING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'KMediaPart'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mi
metype/servicetype 'audio/x-ogg'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: '/usr/share/applications/vlc
.desktop' specifies undefined mimetype/servicetype 'video/dv'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'video/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undef
ined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servic
etype 'video/x-avi'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'video/x-nsv'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'video/x-flc'
kbu
ildsycoca: WARN
ING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'application/x-matroska'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-asf'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-asx'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-wax'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-real-audio'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'misc/ultravox'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'application/x-matroska'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-aiff'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-au'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-wav'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-windows-acm'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'image/vnd.rn-realpix'
kbuildsycoca: WARNING: '/usr/share/applications/vlc.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/g3fax'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-compressed-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-fits'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-sgi'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-sun-raster'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xwindowdump'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.ms-powerpoint'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/wav'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/mp3'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: 'kformulapart.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.formula-template'
kbuildsycoca: WARNING: 'kxsldbg_part.desktop' specifies undefined mimetype/servicetype 'text/english'
kbuildsycoca: WARNING: 'kxsldbg_part.desktop' specifies undefined mimetype/servicetype 'text/x-c'
kbuildsycoca: WARNING: 'kxsldbg_part.desktop' specifies undefined mimetype/servicetype 'text/x-c++'
kbuildsycoca: WARNING: 'katepart.desktop' specifies undefined mimetype/servicetype 'text/x-fortran'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.text-web'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.text-master'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.wordperfect'
kbuildsycoca: WARNING: 'knotify.desktop' specifies undefined mimetype/servicetype 'KNotify'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-base.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.database'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-base.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.base'
kbuildsycoca: WARNING: 'gvimagepart.desktop' specifies undefined mimetype/servicetype 'image/x-krl'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-wax'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'audio/x-pls'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'video/x-mpeg2'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'video/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'video/x-ms-afs'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'video/x-ms-wma'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'video/x-ms-wmx'
kbuildsycoca: WARNING: '/usr/share/applications/mplayer.desktop' specifies undefined mimetype/servicetype 'video/x-ms-wvx'

---

### Post by phil66 on 2005-11-02
Hi Aysiu

Kdesu works for me 

Thanks for the help
Ray

---

### Post by jeremy on 2005-11-03
[QUOTE=phil66]Hi Aysiu

Kdesu works for me 

Thanks for the help
Ray[/QUOTE]
do you not get errors in your konsole like I posted above?

---

### Post by phil66 on 2005-11-03
Jeremy

I do not get any messages when using "kdesu"

I get screen to enter password then on to Konqueror

Ray

---

### Post by Princey on 2005-11-03
[QUOTE=jeremy]do you not get errors in your konsole like I posted above?[/QUOTE]

The first time you type kdesu konquerer you may get the error messages like you described. It happened to me too. But when I closed the terminal, re-opened konsole and typed it again, it opened a dialogue box asking for my password then opened without the first error message.

Give it a try again, see what happens.

---

### Post by jeremy on 2005-11-04
I have tried again, and the same thing happens, to clarify, konq opens fine, and I use it as root, then close it. I am then left with konsole showing the errors as I posted previously.
It is no big deal, doesn't seem to do any harm, but I prefer sudo konqueror myself.

---

