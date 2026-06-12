---
title: "Upgrade Experience Threads"
date: 2023-11-05
forum: Forum Feedback &amp; Help
---

### Post by Dennis N on 2023-11-05
What has happened with the "Share with us your Upgrade/Installation Experience" threads that used to exist when a new Ubuntu version released? It appears to have died back in 2022 with Kinetic Kudu. Could we get this going again?

---

### Post by #&amp;thj^% on 2023-11-06
+1
I thought they were helpful, as for some hardware and or kernels might need a tweak here or there.

---

### Post by Claus7 on 2023-11-07
Hello,

gone are the days... The last time I remember these, they didn't have so much participation. In the old days I remember that polls reached easily ~100 voters and lately < 10. 

Regards!

---

### Post by Claus7 on 2024-05-20
Hello,

yet for noble, things seem to be different!

Regards!

---

### Post by fometeo on 2024-06-22
This week, as an IT support technician, I handled two upgrades from Ubuntu 22.04 LTS to 24.02 LTS and would like to share feedback from this experience and the initial impressions from users.


Of course, they appreciated having the latest version, but there were some issues. Notably, Thunderbird stopped working as an application and switched to a SNAP package. I managed to migrate the profiles successfully, but Thunderbird is no longer visible during remote access via xrdp.


Please note that remote work is very common these days, and Ubuntu 24.04 does not seem to be robust in this aspect, which you can verify through testing.

The case of Thunderbird is particularly curious: on a clean installation, Thunderbird opens and is visible during the initial configuration phase via xrdp. However, once closed, it does not appear again on subsequent attempts.


Additionally, the Software Manager does not appear in remote access, and the favorites dock insists on staying at the bottom but disappears once entering one of the desktops. In this regard, xfce4 performs better in showing menus.


What I am highlighting here is a perceived lack of maturity for remote access. I would appreciate it if this could be taken into consideration.

---

### Post by TheFu on 2024-06-22
From my experience, many remote access issues are connected with the switch to Gnome4+ and Wayland.

Mozilla (Firefox and Thunderbird) both try never to be run remotely, but there is a CLI option to tell it you know and to allow it.  That option for both is *-no-remote*.  While I switched from Ubuntu about a year ago due to the entire forced snap packages, so I don't know if those options will work with snap versions, they do work fine with normal .DEB installs.  

I generally don't use a remote desktop unless I'm traveling. For daily running of remote applications, I use ssh X11Forwarding instead. I find this integrates with my local desktop more cleanly and that the performance is just like running it locally for the most part.  Of course, whether the performance will be that good for you will depend on the available bandwidth and latency between the server and the client systems.  I haven't used RDP or VNC since discovering NX-based remote desktops over a decade ago.  Of course, most NX-based remote desktops don't work with modern Gnome or KDE or any DE that demands/expect direct access to GPU hardware.  If you use XFCE/Mate/ any pre-Gnome3 based DE or no DE, the NX remote desktops like x2go work really well AND with greater convenience once ssh-keys are setup.

---

### Post by coffeecat on 2024-06-23
Since there is now a Noble Numbat upgrade experience thread in situ, and since the thread has now veered off-topic for this sub-forum, thread closed.

@fometeo, two points:

1 - the strapline for this sub-forum - Forum Feedback & Help - states, "Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features." It is not for anything else. The OP correctly posted here as theirs was a plea for a missing and traditional thread to be re-instated.

And...

> **fometeo said:**
> I would appreciate it if this could be taken into consideration.

Who are you addressing? This is a forum whose membership consists of end-users. This is not the place to contact Ubuntu developers.

---

