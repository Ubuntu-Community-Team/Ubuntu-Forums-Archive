---
title: "Automatic login to Kodi login session"
date: 2023-04-03
forum: Desktop Environments
---

### Post by redvenomweb on 2023-04-03
My uncle has an old XBMCbuntu (Lubuntu) 12.04 nettop that I built for him years ago.  The media scrapers have finally broken beyond my ability to repair them, so I'm finally just wiping it and doing a full reinstall/upgrade from scratch.  Aiming for a similar config, I've installed Lubuntu 22.04 with the newest version of Kodi.

I set up the box for autologin, and it's logging into the Lubuntu session by default.  The problem I'm having is in trying to change the default login session to Kodi instead of Lubuntu.  **/etc/sddm.conf** originally looked like this:

[Autologin]
User=<the user name I set up>
Session=Lubuntu

When I change it to **Session=Kodi** autologin stops working.

Am I on the right path with **/etc/sddm.conf** ? What am I missing?

(In searching for other answers to this problem, I've seen people recommending creating a startup script for this user that starts Kodi as soon as you autologin to Lubuntu, but that's not what I'm trying to do.  I'm trying to recreate the same setup from XBMCbuntu/Kodibuntu where the system autologins to a Kodi session.)

---

### Post by guiverc on 2023-04-03
I haven't used Kodi in years, thus I can't help with it.

Sddm can use any *session* that is defined in /usr/share/xsessions/.   Do you have a *session* defined in that directory so that sddm can run it?

(A quick look at [https://packages.ubuntu.com/jammy/amd64/kodi/filelist](https://packages.ubuntu.com/jammy/amd64/kodi/filelist) doesn't show any that get installed there, but as stated I haven't used kodi in years & don't have it installed to see what gets installed; nor know how you installed it.  The box I'm using currently has 19 defined *sessions* in my /usr/share/xsessions/ directory; my primary Lubuntu box however has 7 but a new Lubuntu install I'd expect to have only 3 options)

---

### Post by ActionParsnip on 2023-04-03
[https://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux](https://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux)

---

### Post by redvenomweb on 2023-04-03
> **guiverc said:**
> I haven't used Kodi in years, thus I can't help with it.

Sddm can use any *session* that is defined in /usr/share/xsessions/.   Do you have a *session* defined in that directory so that sddm can run it?

Thanks!  **/usr/share/xsessions** had the answer.  While the session is listed in the login screen as uppercase **Kodi**, the session file itself is lowercase **kodi**.
Works like a charm.

---

### Post by ActionParsnip on 2023-04-03
> **redvenomweb said:**
> Thanks!  **/usr/share/xsessions** had the answer.  While the session is listed in the login screen as uppercase **Kodi**, the session file itself is lowercase **kodi**.
Works like a charm.

Great news. Please mark as solved if the issue is sorted

---

### Post by TheFu on 2023-04-03
Please mark as **solved** using the thread tools button, but as long as I'm here, a raspberry Pi v2, v3, v4 can be used as media players. Load up **OSMC**, which is the Kodi version optimized for that purpose on those devices.  

v2 Pis will struggle with 1080 mpeg2 content without the $3 license the Pi-foundation sells, but handles h.264 easily.  No 4K works.
v3 Pis will handle 1080 content all in software easily, but struggle with h.265/VP9 videos.  No 4K works.
v4 Pis handle pretty much anything, including 4K content, but they are expensive and hard to find for another 6 months as post-COVID supplies are being refilled.

Anyway, my point is that silent, HDMI connected, Kodi systems that use 10W, peak power, are available and maintained.  I've been using OSMC on v2 and v3 Pis for about 5 yrs now.

Beware, the switch from python2 to python3 happened a few years ago and broke a number of kodi streaming addons. Many have been fixed, but a few that I cared about were never fixed.  A pi3 can support booting from an external USB SSD/HDD, if you want to avoid the microSD corruption issues or want to have all the data local. Just be certain that any external storage is also externally powered. The pi USB ports aren't meant to be used to power spinning HDDs.  BYOP - bring your own power.

---

