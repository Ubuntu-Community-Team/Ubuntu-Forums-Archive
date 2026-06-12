---
title: "Weather applet updates too soon"
date: 2008-12-24
forum: General Help
---

### Post by forrestcupp on 2008-12-24
My problem with the Gnome panel weather applet is that it updates as soon as it loads.  Since I use a wireless connection, the weather applet updates before I'm connected to the internet, which leaves it blank.  So I either have to wait the 30 minutes until it automatically updates again, or manually do it myself.

Does anyone know of a way to get it to wait a minute or two before it updates the first time, or maybe to have it load *after* the network manager is done with its thing?

---

### Post by dcstar on 2008-12-25
> **forrestcupp said:**
> My problem with the Gnome panel weather applet is that it updates as soon as it loads.  Since I use a wireless connection, the weather applet updates before I'm connected to the internet, which leaves it blank.  So I either have to wait the 30 minutes until it automatically updates again, or manually do it myself.

Does anyone know of a way to get it to wait a minute or two before it updates the first time, or maybe to have it load *after* the network manager is done with its thing?

CTRL-ALT-Backspace will restart X and force an update, as will logging out and in again.

The real solution is to have your networking up before the desktop starts.

---

### Post by forrestcupp on 2008-12-25
> **dcstar said:**
> 
The real solution is to have your networking up before the desktop starts.

Is it possible to do that with a wireless connection?

---

### Post by bonesdds on 2009-05-02
Bump.  I have the same problem.  The weather application tries to retrieve info before my wireless is connected.  This results in a blank segment in the panel.  Running 9.04, but my problem has been around for years.  Am I missing something?  Any guidance out there?  Thank you.

---

### Post by anjilslaire on 2009-05-02
Not sure what to tell you. I've used the gnome weather applet on my mini 9, both in 8.10 & now 9.04, and it always loads & updates right after the wireless.

---

### Post by paradigm2 on 2009-05-02
> **forrestcupp said:**
> Is it possible to do that with a wireless connection?

It is but it isn't the default Ubuntu way.  You can for instance call it at bootup in the default runlevel from /etc/init.d/net.wlan0 (or whatever you have), but this would probably involve not using Network Manager or the like but instead messing with either Wireless-Tools or wpa_supplicant manually.

For CTRL+ALT+BACKSPACE:

Now it is "(RT ALT) + SYSREQ + K" to do this.  Of course, it'd be easier just to hit update. :/

Another option perhaps might be to create a script which loads the applet but put a 'sleep 15' (sleep for 15 seconds) before the weather applet is set to load.

---

