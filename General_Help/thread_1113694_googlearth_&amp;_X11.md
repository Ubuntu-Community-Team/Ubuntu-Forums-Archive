---
title: "googlearth &amp; X11"
date: 2009-04-01
forum: General Help
---

### Post by christym on 2009-04-01
I'm trying to install googlearth 5 onto an ACER Aspire 5315 running ubuntu 8.10. 

I get this error:
root@ubuntu:/home/doug/Desktop# ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
You don't seem to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...

Where do I go from here?
Thanks Forum

---

### Post by dcstar on 2009-04-02
> **christym said:**
> I'm trying to install googlearth 5 onto an ACER Aspire 5315 running ubuntu 8.10. 

I get this error:
root@ubuntu:/home/doug/Desktop# ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
You don't seem to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...

Where do I go from here?
Thanks Forum

You have to install it in a terminal **inside** your X session, not on a CTRL-ALT terminal.

---

### Post by hyper_ch on 2009-04-02
add medibuntu repos and install GE from there.

See the link in my sig for adding the medibuntu repo.

---

