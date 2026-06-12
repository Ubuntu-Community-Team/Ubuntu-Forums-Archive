---
title: "Firefox crash while browsing Cisco ACS webgui"
date: 2009-06-05
forum: General Help
---

### Post by DukeLuke on 2009-06-05
Firefox crashes when I navigate to my Cisco ACS web-gui. I did an --strace and here is what I get:

The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 20690 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Can anyone help me fix this?

---

### Post by nicolasbussieres on 2009-09-09
Confirmed , i have the same problem : 
Ubuntu 9.04 updated to the latest patches
Using firefox with suns java plugin
Cisco ACS 4.2 , patched

The problem seems related to firefox 3.X , since there is no crash with firefox 2.x

This is really annoying. It seems related to other image crashes too. I tried other distros and don't get the same problem.

---

### Post by nicolasbussieres on 2009-09-09
A cpuple of experiments later , it seems the probleme is library related . I get the same problem with any browsers.

---

### Post by nicolasbussieres on 2009-09-09
I probably didnt get errors with Firefox 2.0 since i did a standalone installation with its own libraries and all.

---

### Post by placidoaps on 2009-10-29
Same problem any solution?

---

### Post by fedoraboy on 2009-11-05
Karmic/9.10 update on this:

No firefox crash... but it doesn't seem to work still.  I get a blank browser screen after login.

---

### Post by DukeLuke on 2009-11-10
I also upgraded to 9.10 and get the same result - no crash, but get blank screen after log in.

---

