---
title: "x11vnc timing out"
date: 2010-12-02
forum: Desktop Environments
---

### Post by SBLMsurfer on 2010-12-02
I am working with a local company and trying to connect ssh tunnel/vnc.  It has worked for the last two months flawlessly until now.  For some reason it is timing out.

Here's the log:
> 
ids482@Powernet:~$ x11vnc -safer -localhost -nopw -once -diplay :0
02/12/2010 13:54:49 passing arg to libvncserver: -diplay
02/12/2010 13:54:49 passing arg to libvncserver: :0
02/12/2010 13:54:49 -safer mode:
02/12/2010 13:54:49    vnc_connect=0
02/12/2010 13:54:49    accept_remote_cmds=0
02/12/2010 13:54:49    safe_remote_only=1
02/12/2010 13:54:49    launch_gui=0
02/12/2010 13:54:49 x11vnc version: 0.9.3 lastmod: 2007-09-30
02/12/2010 13:54:49
02/12/2010 13:54:49 *** XOpenDisplay failed. No -display or DISPLAY.
02/12/2010 13:54:49 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
02/12/2010 13:54:49 *** 1 2 3 4
No protocol specified
02/12/2010 13:54:53

02/12/2010 13:54:53 ***************************************
02/12/2010 13:54:53 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: [http://www.karlrunge.com/x11vnc/#faq](http://www.karlrunge.com/x11vnc/#faq)


Can someone help me?

I'm using a Windows Laptop with PuTTY and TightVNC to get into Ubuntu Server 8.04

---

### Post by krunge on 2010-12-05
You typed '-display :0' incorrectly in your example.

But I don't think that matters because x11vnc tried :0 by default.

From your output messages it looks like the user you are running x11vnc as does not have permission to connect to display :0. Which user are you running x11vnc as? Does that user have permission to connect to display :0?  Read the information that x11vnc printed out for an explanation.

---

