---
title: "Gnome crashes on start"
date: 2006-06-04
forum: Desktop Environments
---

### Post by tryl on 2006-06-04
I've just installed Drapper - previously SuSE, but Ubuntu is really SuSE done right + lots more!
Unfortunally the screen goes black when Gnome loades, and I'm send back to the login screen.

The first day I ran Ubuntu, Gnome did that one time, then it booted well one time, then it did it the next and now it does it all the time. The live CD is running perfectly every time (currently using it).

The screen goes black when the bling-bling sound has plaied, the task bar and usually one gnome applet has loaded, but transparency does not seem to have been applied to the task bar.

I got some log output, that hopefully can help:
**.xsession-errors**:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tryl"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mille:/tmp/.ICE-unix/4499
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
The application 'update-notifier' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'nm-applet' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Vindueshåndteringsadvarsel: Mistede forbindelsen til terminalen ':0.0';
sandsynligvis blev X-serveren lukket ned eller du afsluttede
vindueshåndteringen.

** (gnome-panel:4937): WARNING **: Failed to send buffer

** (gnome-panel:4937): WARNING **: Failed to send buffer
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
```

Translation of the danish stuff.
```
Vindueshåndteringsadvarsel: Mistede forbindelsen til terminalen ':0.0';
sandsynligvis blev X-serveren lukket ned eller du afsluttede
vindueshåndteringen.
```
Means```
Window manager warning: Lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
```

And from **/var/log/messages** (not translated):
```
Jun  4 13:58:03 mille gconfd (tryl-4781): starter (version 2.14.0), pid 4781 bruger 'tryl'
Jun  4 13:58:03 mille gconfd (tryl-4781): Bestemte adressen "xml:readonly:/etc/gconf/gconf.xml.mandatory" til en skrivebeskyttet konfigureringskilde ved position 0
Jun  4 13:58:03 mille gconfd (tryl-4781): Bestemte adressen "xml:readwrite:/home/tryl/.gconf" til en skrivbar konfigureringskilde ved position 1
Jun  4 13:58:03 mille gconfd (tryl-4781): Bestemte adressen "xml:readonly:/etc/gconf/gconf.xml.defaults" til en skrivebeskyttet konfigureringskilde ved position 2
Jun  4 13:58:03 mille gconfd (tryl-4781): Bestemte adressen "xml:readonly:/var/lib/gconf/debian.defaults" til en skrivebeskyttet konfigureringskilde ved position 3
Jun  4 13:58:03 mille gconfd (tryl-4781): Bestemte adressen "xml:readonly:/var/lib/gconf/defaults" til en skrivebeskyttet konfigureringskilde ved position 4
Jun  4 13:58:03 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  4 13:58:03 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  4 13:58:10 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun  4 13:58:10 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  4 13:58:10 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  4 13:58:10 mille gconfd (tryl-4781): Bestemte adressen "xml:readwrite:/home/tryl/.gconf" til en skrivbar konfigureringskilde ved position 0
Jun  4 13:58:29 mille gconfd (tryl-4781): Modtog signal 15, lukker pænt ned
Jun  4 13:58:30 mille gconfd (tryl-4781): Afslutter
```

And now **translated**:
```
Jun  4 13:58:03 mille gconfd (tryl-4781): starting (version 2.14.0), pid 4781 user 'tryl'
Jun  4 13:58:03 mille gconfd (tryl-4781): Located the address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a write protected configuration source at position 0
Jun  4 13:58:03 mille gconfd (tryl-4781): Located the address "xml:readwrite:/home/tryl/.gconf" to a write**able** configuration source at position 1
Jun  4 13:58:03 mille gconfd (tryl-4781): Located the address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a write protected configuration source at position 2
Jun  4 13:58:03 mille gconfd (tryl-4781): Located the address "xml:readonly:/var/lib/gconf/debian.defaults" to a write protected configuration source at position 3
Jun  4 13:58:03 mille gconfd (tryl-4781): Located the address "xml:readonly:/var/lib/gconf/defaults" to a write protected configuration source at position 4
Jun  4 13:58:03 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  4 13:58:03 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  4 13:58:10 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun  4 13:58:10 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  4 13:58:10 mille dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  4 13:58:10 mille gconfd (tryl-4781): Located the address "xml:readwrite:/home/tryl/.gconf" to a write**able** configuration source at position 0
Jun  4 13:58:29 mille gconfd (tryl-4781): Received signal 15, closing down nicely
Jun  4 13:58:30 mille gconfd (tryl-4781): Shutting down
```

Finally a bit of hardware info:
My box is an Acer TravelMate 2413WLMi.
lspci:```
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
```

I hope anybody can help, because I can't find the problem myself and I will NOT go back to SuSE!

---

### Post by tryl on 2006-06-04
Some of the times, the following message appears just after the screen have blanked (i managed to snap a photo):

```
glibc detected *** malloc(): memory corruption: 0x083f6b60 ***
```

One time it was followed by:
```
[4295102.019000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

---

### Post by freddo on 2006-06-05
Jepp! I have exactly the same problems witch my Dell D620. It worked fine with dapper during the beta-era until a week agon when this *very* annoying thing happened. Will reinstall tomorrow... It sucks.

Can't get around it either, as far as I've got..
](*,)

---

### Post by cyaconi on 2006-08-02
Same here.... 
Any help is very preciated!!

---

### Post by cyaconi on 2006-08-02
Same here.... 
Any help is very preciated!!

---

### Post by tryl on 2006-08-03
I "solved" it by reinstalling Ubuntu.

Later I read that you should be carefull about using wifiradar and ndiswrapper with the Broadcom BCM4318 (and others in that series) wifi chip. The reason is that the kernel has an open source driver build in and it will conflict. Because I had wifiradar running as a Gnome applet, it may have been that.

I got the wifi-stuff via Automatix. This time I didn't install it, and have not had any problems.

---

### Post by Leonivek on 2006-09-28
If this has happened to you, **don't re-install Ubuntu**!  Read this...

I've had the same problem for the past few days.  I was able to log in to other accounts without any problems, so it was a per-user problem.  I was also able to log in to KDE and use a nested window (xnest) to login to the faulty Gnome account **and it would work**!  But only through xnest.  Why?  I don't know.

I figured this was because I had just install **Murrine** and configured my desktop the way I wanted it, and as soon as I logged out and back in, it would crash.

After deleting the Gnome related folders in my home folder (**.gnome, .gnome2, .gconf, .gconfd, .metacity**), I was able to log back in.  This reverted me back to the **default Ubuntu settings**.

I re-customized my desktop the way I like it, and AGAIN, it crashed! :confused: **So removing Murrine didn't work**.

I deleted all of my Gnome folders and started over, but this time, after every little change I did to my desktop, I logged out and back in.

After going through this process of elimination, I've determined that _**this problem is caused by turning on panel transparency**_.  As soon as I made a panel use transparency, I could no longer log in.

To remove the transparency without deleting all of my Gnome folders, I simply logged into KDE, used xnest to login to the crashing gnome account, removed the transparency, ran a **gnome-session-save** in terminal, logged out of KDE, and logged back in to my Gnome account. 8) No problems!  

For now, I will not use transparency until I figure out what is causing it.  **Maybe it's a gtk2 problem??**  I don't know.

Hope this helps anyone with this problem...

---

### Post by tryl on 2006-09-28
That sounds very reasonable. I actually used transparency in my faulty gnome, and I just hadn't set it up in the new one.

One odd thing is, however, that it wasn't every time I logged into my gnome with transparency that it failed. And for a time it actually ran fine with transparency. But of cause, an update can have killed that...

---

### Post by Leonivek on 2006-10-08
I'm still having the problem... Can't seem to figure out how to fix it.  As soon as I set transparency, I can no longer log in to my Gnome desktop. :confused:

[COLOR=SeaGreen]**Does anyone know where or in which file this transparency setting is stored or where the problem may lie?**  [/COLOR]It has to be in the _home folder_ somewhere because this problem is specific to this user.  *I don't have this problem signing in any other accounts* on my computer with transparency set. ](*,)

If anyone has any inkling of an idea, even if you're unsure, I am willing to try anything at this point! :-k

Thanks! :-?

---

