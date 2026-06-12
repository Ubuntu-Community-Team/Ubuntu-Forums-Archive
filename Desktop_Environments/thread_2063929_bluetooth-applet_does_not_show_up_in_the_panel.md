---
title: "bluetooth-applet does not show up in the panel"
date: 2012-09-28
forum: Desktop Environments
---

### Post by Farinet on 2012-09-28
I'm on lubuntu 12.04 i386 here (but the problem apparently seems the same for 12.04 ppc as well).

The bluetooth-applet does not appear automatically after the startup (like the wireless or sound icon e.g.) in the panel's notification area although it's activated in Desktop > Preferences > Startup applications.

What i did up to now:

 I edited the 'bluetooth-applet.desktop' file in '/etc/xdg/autostart' in the way that NoDisplay=True was changed to False and i cancelled all restrictions to Gnome3 or Unity. But without any affect.

I created an autostart.sh file in '/etc' containing also one line: 'blueman-applet &'. Also no effect. May be it's in the wrong directory?

OTOH: I can start blueman-applet from a terminal or from run a command in the application menu - and it shows up. Blueman-applet works correctly (but i would like to stick with default bluetooth since it is nicely integrated to pcmanfm and it's way way faster than blueman).

TIA for any suggestion.

---

### Post by kio_http on 2012-09-28
bluetooth-applet is not used in Kubuntu.

---

### Post by Bucky Ball on 2012-09-28
> **kio_http said:**
> bluetooth-applet is not used in Kubuntu.

OP using Lubuntu.

I'm not familiar with Lubuntu but just guessing: In Xubuntu it is Applications>Settings>Settings Manager>Session and Startup>Application Autostart. Xubuntu uses the Blueman-applet and I think Lubuntu does too. You will see it there as 'Blueman Applet (Blueman Bluetooth Manager)'. If you don't see Blueman you will see something else that handles your bluetooth (or should). Make sure whatever it is is ticked and enabled. Restart (you might be able to just log out/in). You should now have an icon.

---

### Post by kio_http on 2012-09-28
> **Bucky Ball said:**
> OP using Lubuntu.

I'm not familiar with Lubuntu but just guessing: In Xubuntu it is Applications>Settings>Settings Manager>Session and Startup>Application Autostart. Xubuntu uses the Blueman-applet and I think Lubuntu does too. You will see it there as 'Blueman Applet (Blueman Bluetooth Manager)'. If you don't see Blueman you will see something else that handles your bluetooth (or should). Make sure whatever it is is ticked and enabled. Restart (you might be able to just log out/in). You should now have an icon.

Then why is the thread tagged Kubuntu?

---

### Post by Bucky Ball on 2012-09-28
Not sure, but:

> **Farinet said:**
> I'm on lubuntu 12.04 i386 here


@ kio_http: Sorry, I see now it is tagged Kubuntu also.

@ Farinet: We're confused ... which are you using, Kubuntu or Lubuntu??? I'm figuring as it is i386 32bit probably low spec and Lubuntu?

---

### Post by kio_http on 2012-09-28
> **Bucky Ball said:**
> Not sure, but:



@ kio_http: Sorry, I see now it is tagged Kubuntu also.

@ Farinet: We're confused ... which are you using, Kubuntu or Lubuntu??? I'm figuring as it is i386 32bit probably low spec and Lubuntu?

KDE runs well on low spec hardware too on recent releases, my machine is single core 1.6 ghz 32 bit with 2GB ram and I use KDE. But its probably lubuntu since "applet" is mentioned.

---

### Post by Farinet on 2012-09-30
> **Bucky Ball said:**
> Not sure, but:



@ kio_http: Sorry, I see now it is tagged Kubuntu also.

@ Farinet: We're confused ... which are you using, Kubuntu or Lubuntu??? I'm figuring as it is i386 32bit probably low spec and Lubuntu?

Sorry about that. I'm on lubutu and i tagged the thread erroneously as kubuntu but i did not find a way to correct that.

---

### Post by Farinet on 2012-09-30
> **Bucky Ball said:**
> OP using Lubuntu.

I'm not familiar with Lubuntu but just guessing: In Xubuntu it is Applications>Settings>Settings Manager>Session and Startup>Application Autostart. Xubuntu uses the Blueman-applet and I think Lubuntu does too. You will see it there as 'Blueman Applet (Blueman Bluetooth Manager)'. If you don't see Blueman you will see something else that handles your bluetooth (or should). Make sure whatever it is is ticked and enabled. Restart (you might be able to just log out/in). You should now have an icon.

No, lubuntu comes with networ-manager and gnome-bluetooth. Which is clearly better integrated by default to the filemanager (pcmanfm - you can do that with blueman as well, but there are several scripts needed). Moreover, blueman, when it comes to file transfers from your phone (photos) is dead slow in showing up in pcmanfm; gnome-bluetooth is much quicker.

So, i'd like to stick with it. I changed in /etc/xdg/autostart the bluetooth-applet.desktop file and cancelled all restrictions (to Gnome, to not disappear etc. etc.). But no effect. OTOH, i can run bluetooth-applet from the run an application submenu of the application menu in the panel (and from a terminal as well).

---

### Post by Bucky Ball on 2012-10-01
You don't want to autostart gnome-bluetooth? I actually use pcmanfm but don't use bluetooth. Just bought a new phone, though, so that could change and will have a deeper dig into your info ... ;)

---

### Post by Farinet on 2012-10-02
> **Bucky Ball said:**
> You don't want to autostart gnome-bluetooth?

Why do you guess that? It's quite the opposite: I wanted to have started automatically the bluetooth-applet but it does not although i deleted all the NonShownIn, NoDisplay=True etc. restrictions in the bluetooth-applet.desktop file (all files i found somewhere) and i do not understand the reason why. May be there is some other desktop file in some hidden directory???

 > **Bucky Ball said:**
> I actually use pcmanfm but don't use bluetooth. Just bought a new phone, though, so that could change and will have a deeper dig into your info ... ;)

Good luck :)

---

### Post by Bucky Ball on 2012-10-02
> **Farinet said:**
> Good luck :)

Thanks but didn't need it. Tried it out when first got phone and bluetooth setup and connection went without a hitch. ;)

---

