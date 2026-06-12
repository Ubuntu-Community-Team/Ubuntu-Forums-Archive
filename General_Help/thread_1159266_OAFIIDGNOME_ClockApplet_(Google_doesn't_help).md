---
title: "OAFIID:GNOME_ClockApplet (Google doesn't help)"
date: 2009-05-14
forum: General Help
---

### Post by navneeth on 2009-05-14
All of a sudden, the clock and weather applet on the panel decided not to load after a bunch of Gnome updates. I have tried removing and re-installing the said updates, but that did not work. 

Every time the desktop comes up after a boot or re-boot there are these umpteen dialogs pop-up informing me of the error and the OAFIID:GNOME_ClockApplet. It also gives me the option to delete or not delete the configuration files for these applets. I always choose the 'Don't Delete' option. 

I want my panel clock back! Any help will be appreciated.

---

### Post by navneeth on 2009-05-15
Bump.

---

### Post by soro2005 on 2009-05-15
Sometimes it helps if you delete the configuration files/applets, and then put them back on the panel (right click anywhere on the dock and "add ro panel")

---

### Post by navneeth on 2009-05-15
I was unsure whether to delete them or not. I tried it just now and it doesn't work. I get the same errors. Do I need to reboot for it work?

---

### Post by soro2005 on 2009-05-15
Log out and in at least. Perhaps, there's something hanging.

Also, can you post the contents of ~/.xsession-errors? (Hit ctrl+h to make hidden files visible, it's in your home directory)

---

### Post by navneeth on 2009-05-15
Reboot did not work. 

I have attached a text file containing the messages in the .xsession-errors file. The errors start showing up from line 104.

---

### Post by soro2005 on 2009-05-15
nothing attached. You may have to gzip it for filesize:
```
gzip filename
```

---

### Post by navneeth on 2009-05-16
Oh, sorry about that. It's now attached to my earlier post. 

There has been a gap of many hours between my last post and this one, and this time, while I turned my computer on, I did not see those dialogs pop-up automatically, but I'm still unable to use any of those applets.

---

### Post by soro2005 on 2009-05-16
Open Synaptic Package Manager and make sure that you have the package libsoup2.4-1 installed. If you do, reinstall it. Here's your error
```
** (gnome-panel:3161): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_ClockApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : g_module_open of `/usr/lib/gnome-panel/libclock-applet.so' failed with `libsoup-2.4.so.1: cannot open shared object file: No such file or directory'
```

---

### Post by navneeth on 2009-05-16
> **soro2005 said:**
> Open Synaptic Package Manager and make sure that you have the package libsoup2.4-1 installed. If you do, reinstall it. Here's your error
```
** (gnome-panel:3161): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_ClockApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : g_module_open of `/usr/lib/gnome-panel/libclock-applet.so' failed with `libsoup-2.4.so.1: cannot open shared object file: No such file or directory'
```

Thank you so much for your help, soro. Not only did reinstalling that library file solve the applet problem, but I'm now also able to use Totem and Brasero, both of which showed errors regarding the same file when I tried to open them.

---

### Post by Chris1492 on 2011-01-08
I've just been having similar problems with a new installation of Ubuntu Maverick 10.10 -- any applet I tried to add to the panel gave an error beginning "OAFIID:GNOME_...".

I reinstalled libsoup2.4.1 and libsoup-gnome2.4.1, and it's all working well now.

cheers

Chris

---

