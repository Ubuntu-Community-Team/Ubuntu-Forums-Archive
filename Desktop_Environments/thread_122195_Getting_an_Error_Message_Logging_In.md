---
title: "Getting an Error Message Logging In"
date: 2006-01-26
forum: Desktop Environments
---

### Post by troether on 2006-01-26
Hi 
I was working with the Image Magick program that came with Ubuntu5.04 and had saved several images. Then I noticed it was due for an upgrade so  I successfully upgraded Image Magick using the synaptic program manager. Afterwards I noticed that I couldn't open my terminal window, it would try to load for a few seconds but then just quit. Not knowing what was going on I logged off and rebooted.  When I tried to log back in I got this message:

   Your session only lasted less than 10 sec. If you have not logged out 
   yourself this could mean that there is some installation problem or that
   you mat be out of diskspace. Try logging in with one of the failsafe 
   sessions to see if you can fix this.

I shouldn't be running out of disk space as I've only used about 2 1/2 gigs on a 4 gig hard drive.  By the way, I'm running on a intel 686 with a 400MH Celeron processor and 190Mb of RAM. Clicking on the view details window I get this:

   (~/.xsession-errors file)
   /etc/gdm/Presession/Default:Registering your session wtmp and utmp
   /etc/gdm/Presession/Default: running: /usr/bin/x11/sesreg -a -w/var/
   log/wtmp -u /var/run/utmp -x "/var/lib/gdm/: 0.xservers " -h " " -1 ":
   0 " " ["My log in name"]
   etc/gdm/xsession: beginning setup
   usr/bin/dbus -launch: error while loading shared libraries: libSM.so.6:
   cannot open shared object file: No such file or directory.

I found out  that Image Magick has had some security issues and that it is possible it could trigger a heap overflow but this does'nt help me. I'm fairly new to linux so any suggestions on how to fix this would be appreciated - the more explicit the better.
Thanks

---

