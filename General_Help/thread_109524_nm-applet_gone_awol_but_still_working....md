---
title: "nm-applet gone awol but still working..."
date: 2005-12-28
forum: General Help
---

### Post by stardotstar on 2005-12-28
I successfully switched to nm-applet - it is connecting to my wireless on login (session startup program at 10).  It asks for my keyring password and will connect to unsecured networks but I can no longer see the applet icon in the top right panel since I changed my themes around a fair bit.

I went from Breezy defaults to some gnome-look metacity themes and it disappeared.  I cannot launch it from a terminal or by using alt-F2.  I have removed the default network monitor from the panel which I thought might be overriding it and have tried logging in and out with several different setups for the panel all to no avail.

Since it is working I don't think I know how to access its connection properties or switch between adapters etc.

Troubleshooting ideas appreciated.  I have searched here for nm-applet and network manager problems and saw some similar things but the fixes did not work for me.  Anyone think of anything?

Will.

---

### Post by stardotstar on 2006-01-03
This really perplexes me - perhaps I have missed some critical search - but the applet has disappeared from my panel and provides no other easy way of interfacing with it - I am clearly still working with it - I am asked to provide my keyring password on login and the connection works but I cannot access any icon or other interface that allows me to see the networks or switch to LAN etc...

Any ideas???

---

### Post by kperkins on 2006-01-03
Right click on the panel > Add to panel > Custom application launcher > type in 'netapplet' (no quotes) where it says command, hit ok, and that should do it.

---

### Post by stardotstar on 2006-01-03
That adds the ppp dialer monitor to the panel.  Thanks for the reply but I need the panel applet for the network manager that I am using to handle my WIFI networks.

It is running (asks for the keyring pass on login) and handling the connection to my local wireless router but I cannot access its configuration from the panel icon which used to be in the top right...

```

 7270 root      15   0 77160  29m 8268 S  1.0  2.9   6:37.51 Xorg
 4888 wparker   16   0  2132 1100  844 R  0.7  0.1   0:00.06 top
 7946 wparker   16   0 33308  10m 7956 S  0.3  1.0   0:20.21 nm-applet
 7971 wparker   16   0 33304  10m 7956 S  0.3  1.0   0:19.25 nm-applet
 7998 wparker   16   0 33312  10m 7956 S  0.3  1.0   0:19.92 nm-applet
 8012 wparker   15   0 39076  14m 8960 S  0.3  1.4   0:01.96 gnome-terminal
    1 root      16   0  1560  532  460 S  0.0  0.1   0:01.06 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  101 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
  127 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush

```

I can't find anything in /etc except the directory /NetworkManager which is empty except for an empty directory dispatcher.d

I found a whole bunch of these entries in my .xsession-errors
```

** (nm-applet:7998): CRITICAL **: nmi_dbus_signal_update_network: assertion `connection != NULL' failed

** (nm-applet:7969): CRITICAL **: nmi_dbus_signal_update_network: assertion `connection != NULL' failed

** (nm-applet:7952): CRITICAL **: nmi_dbus_signal_update_network: assertion `connection != NULL' failed

** (nm-applet:7956): CRITICAL **: nmi_dbus_signal_update_network: assertion `connection != NULL' failed
DCOPClient::attachInternal. Attach failed Could not open network socket

```

Is this because the applet is trying to write to the panel and can't because of the theme or something?

---

### Post by kperkins on 2006-01-04
Instead of typing netapplet try nm-applet.  If that doesn't work, you may have to reinstall network-manager.

---

### Post by stardotstar on 2006-01-04
OK I have tried that but the panel manager diverts to an empty search and then offers categories again.

I have run package manager and reinstalled the network manager and funnily enough this caused the battery manager to unexpectedly die and restart in the panel but the nm-applet did not appear so I logged out and back in and it is still missing and still not available in panel manager.

I have also tried removing it from the session startup and rebooting.  It loaded anyway - I can see it in the session processes.

in the console I had a look at the nm-applet itself:

```

wparker@gecko:/usr/share/pixmaps $ nm-applet --usage
Usage: nm-applet [-?|--help] [--usage] [--gdk-debug=FLAGS]
        [--gdk-no-debug=FLAGS] [--display=DISPLAY] [--screen=SCREEN]
        [--sync] [--name=NAME] [--class=CLASS] [--gtk-debug=FLAGS]
        [--gtk-no-debug=FLAGS] [--g-fatal-warnings] [--gtk-module=MODULE]
        [--oaf-ior-fd=FD] [--oaf-activate-iid=IID] [--oaf-private]
        [--disable-sound] [--enable-sound] [--espeaker=HOSTNAME:PORT]
        [--version] [--sm-client-id=ID] [--sm-config-prefix=PREFIX]
        [--sm-disable] [--disable-crash-dialog]
        [--load-modules=MODULE1,MODULE2,...]
wparker@gecko:/usr/share/pixmaps $ man nm-applet
No manual entry for nm-applet
See 'man 7 undocumented' for help when manual pages are not available.
wparker@gecko:/usr/share/pixmaps $ nm-applet --version
Gnome nm-applet 0.4.1

```

It is in /usr/bin but I don't know where else to look for configuration.

Will

---

### Post by stardotstar on 2006-01-07
Funny thing about this is that when the network drops I am prompted for the keyring password - which must be nm needing it to reestablish connection - in my normal interface configuration I have the wep key inserted.  So I do know the applet is running and making coherent negotiations with my wlan, but I cannot get it's interface.

 BTW I also switched back to the default human theme which made no diff, so it is not a theme/icon etc related thing.

Further thoughts very much appreciated :)
Will

---

### Post by Manuel Siggen on 2006-01-07
It happened two or three times to me that the nm-applet icon disappears, and I found that restarting the network manager daemon solved the problem :

```
sudo /usr/sbin/NetworkManager restart
```

I've read somewhere that the nm-applet is automatically spawned by the network manager daemon, strange behavior IMO...

---

### Post by stardotstar on 2006-01-07
Thank you.  I have restarted it as suggested with no discernable effect.  I was not prompted for the keyring pass and the panel did not respawn any icon.  It shows in TOP as several processes:

```

10781 wparker   16   0 72924  35m 8900 S  0.3  3.5   1:46.45 nm-applet
10839 wparker   16   0 46956  10m 8024 S  0.3  1.0   0:29.01 nm-applet
10843 wparker   16   0 46952  10m 8024 S  0.3  1.0   0:29.94 nm-applet

```

Wierd.

---

### Post by stardotstar on 2006-01-08
OK I'm really casting about for ideas now.

I have done a complete removal, reboot and reinstall of NetworkManager.

After I removed NetworkManager I was unable to connect to the internet at all - even trying to configure eth1 manually via the Network Connection Properties that resides in the panel to no avail.

I then reinstalled Network Manager from Synaptic and it reported it had successfully installed from scratch (even without the Internet link).  

However the system refused to ask for the keyring pass until a subsequent reboot after which it has resumed normal operations

but still no sign of the nm-applet in the panel - despite its being removed (prior to the complete removal) and reinstalled into the session startup routine at timing 12.

I am finding it difficult to know where to persue further troubleshooting.  I am searching widely on this problem

I can find no other abnormalities with my system.

Will

---

### Post by Manuel Siggen on 2006-01-08
Mmmhhh, I haven't got any new idea... 

Or maybe a very dumb one : you said you quite heavily customized your desktop, and I wonder : would it be possible you removed the notification area altogether (I don't know if it's possible, actually) ? 

If so, that would explain why the nm-applet doesn't show up. And the solution would be to re-add that notification area (right-click on top bar -> Add to Panel... ->Utilities -> Notification Area)

Cheers,

    Manuel

---

### Post by stardotstar on 2006-01-09
Manuel!  You are a legend!  That was it ---  I had no idea what the diff was for the notification area vs the bottom panel which shows programs running - I must learn more about this destinction.

That was awesomely spotted - fantastic.

Now I can see my GRIP status and nm-applet is back!

I remember now that there are no such things as dumb questions - just dumb users ;)

Thanks to everyone who helped trouble shoot this one for me - I am totally stoked that I am back on track!

Will

---

### Post by Manuel Siggen on 2006-01-09
Good, I'm glad I could help you :) 

Have a nice day !

Manuel

---

### Post by cytrus001 on 2008-02-12
I had EXACTLY the same problem. It has been driving me crazy for weeks. This too solved my problem: Remember, simple things are not!

Thanks thanks thanks.

At the risk of changing the thread do you know how to initiate VPN connections in Ubuntu using this applet since that requires a sudo command and i want to use the GUI and not terminal to initiate.

Many thanks

---

### Post by shamshe on 2008-03-26
now how do you make sure the nm-applet starts automatically?

---

### Post by qhaz on 2008-05-10
Thanks Manuel . . . I had been struggling with this one too!

---

