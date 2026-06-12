---
title: "cups / printing"
date: 2005-12-16
forum: General Help
---

### Post by notepad on 2005-12-16
when i try to run gnome-cups-manager i get this error message " the cups server could not be contacted."

and on the command line i get this:

(gnome-cups-manager:9475): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gnome-cups-manager:9475): WARNING **: IPP request failed with status 1280

** (gnome-cups-manager:9475): WARNING **: IPP request failed with status 1280

ive had a look at /etc/cups/cupsd.conf and everything looks good in there. 

when i run ps -A i dont see cups or cupsys anywhere. when i try browsing to 127.0.0.1:631 i am told that the connection is refused. i suppose it would be if cups isnt running and according to ps it isnt. even after i issue /etc/init.d/cupsys start it still doesnt seem to be running.

i can see myself booting windows in a minute. any better ideas?

---

### Post by kosmic on 2005-12-16
One of the solutions i've found for this problem is to go to synaptic and do a complete remove of the Cupsd program and then reinstall, and it should work again.
 
 
Do not do Remove only do a Complete Remove

---

### Post by hajk on 2005-12-16
Why are you (OP) running gnome-cups-manager? And why are you trying to login to [http://localhost:631?](http://localhost:631?) The Ubuntu setup of printing is exclusively through  the System/Administration/Printing menu -- I would guess that it runs gnome-cups-manager in its own way. Anyway, the [http://localhost:631](http://localhost:631) route is disabled in Ubuntu (but you could comment out the lines with
"AuthType Basic'' and "AuthClass System'' near the end of /etc/cups/cupsd.conf to get around this to get access without even a password). My advice is like the previous reply (to clean up a probably messed-up cups system), then after reinstallation to use only the Ubuntu way of setting up printing (otherwise you might as well switch to Debian:smile: ).

---

### Post by notepad on 2005-12-16
youre on the money kosmic. i found that cupsys wasnt installed at all so i installed it ofcourse and little surprise that gnome-cups-manager works now. the next trick is to get my canon lbp-1210 printer to work. i see that my printer is detected properly but no driver is listed for it.

canon europe has put this page up 
[http://software.canon-europe.com/software/canon_capt_printer_driver_for_linuxs21386.asp?model=]("http://software.canon-europe.com/software/canon_capt_printer_driver_for_linuxs21386.asp?model=")

with 'linux' drivers on it but for some strange reason they are all *.rpms. perhaps all i need to do is convert rpm to deb? the other thing i will try is using a *.ppd file.

---

