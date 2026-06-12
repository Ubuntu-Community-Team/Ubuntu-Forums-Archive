---
title: "Unable to log in, even with failsafe, terminal works. See error message"
date: 2005-12-17
forum: General Help
---

### Post by Bad.Andy on 2005-12-17
After rebooting today, though I'm not sure what I've changed recently: When I log in (even with failsafe session) I get the following error message and then kicked back to the welcom screen.. 

-----
Your Sessions only lasted less than 10 seconds.... (cut for brevity) ... Try logging in with one of the failsafe sessions to see if you can fix this problem.

/etc/gdm/PreSession/Default: Registering your session wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:0.Xservers" -h "" -l ":0" "badandy"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X wil not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer:mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Badness:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Badness:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8435): WARNING **: Unable to read ICE authority file: /home/badandy/.ICEauthority
-----

I can however get to the failsafe terminal and all my network services seem to be running fine. I'm new to linux, sorry if this is a stupid post. Any help or direction to help is appreciated.
-Bad Andy

---

### Post by zoiks on 2005-12-17
Wild guess: try deleting your .ICEAuthority file in your home directory and restart.  Also try posting your xorg.conf file.  What settings did you mess with?

---

### Post by Bad.Andy on 2005-12-17
Awesome,

Zoiks, I owe you a beer. I deleted the .ICEauthority file, and everything is back to normal. I didn't mess with any setting (this session) other than installing KVirc.

I also found this (Warty) thread: [http://ubuntuforums.org/archive/index.php/t-1583.html](http://ubuntuforums.org/archive/index.php/t-1583.html)
Which explains that the permissions of the file somehow changes, and you can simply chown it... But no explaination of why this happens. If anybody out there knows I'm interested to learn.

Again thank you Zoiks for the quick help,
-Bad Andy

---

