---
title: "Constant GConf server messages?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by gilgongo on 2005-12-10
Hi - why is it I get lots and lots of the following in /var/log/messages?

What do they mean?

Dec 10 10:50:44 localhost gconfd (root-27061): Resolved address  xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Dec 10 10:50:44 localhost gconfd (root-27061): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Dec 10 10:51:14 localhost gconfd (root-27061): GConf server is not in use, shutting down.
Dec 10 10:51:14 localhost gconfd (root-27061): Exiting

Thanks for any tips.

---

### Post by AAUU on 2006-01-13
I get the same thing.  When I receive this message X resets and I go back to the login screen.  All running apps are killed in the process.

What gives?  I've been searching for answers on this gconf issue. I had thought it was a problem with my video not being able to go into sleep mode.  But these crashes often happen while it's in use.  

I did comment out the DPMS section in the xorg.conf file thinking this was the cause earlier.  But that hasn't fixed the problem.

I have turned off all power saving features.

I still get these errors:```

Jan 13 17:14:37 localhost gconfd (root-9821): starting (version 2.12.0), pid 9821 user 'root'
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan 13 17:14:37 localhost gconfd (root-9821): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan 13 17:15:37 localhost gconfd (root-9821): GConf server is not in use, shutting down.
Jan 13 17:15:37 localhost gconfd (root-9821): Exiting
Jan 13 17:19:59 localhost gconfd (user-7976): Received signal 15, shutting down cleanly
Jan 13 17:19:59 localhost gconfd (user-7976): Exiting
Jan 13 17:20:12 localhost gconfd (user-9998): starting (version 2.12.0), pid 9998 user 'user'
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readwrite:/home/user/.gconf" to a writable configuration source at position 2
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan 13 17:20:12 localhost gconfd (user-9998): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan 13 17:20:16 localhost gconfd (user-9998): Resolved address "xml:readwrite:/home/user/.gconf" to a writable configuration source at position 0
Jan 13 17:22:44 localhost gconfd (user-9998): Resolved address "xml::/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
Jan 13 17:22:44 localhost gconfd (user-9998): None of the resolved addresses are writable; saving configuration settings will not be possible
Jan 13 17:22:44 localhost gconfd (user-9998): Resolved address "xml::/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 13 17:22:44 localhost gconfd (user-9998): None of the resolved addresses are writable; saving configuration settings will not be possible

```
The last PID (I didn't look before hand, but I imagine the root pid is the same) is for /usr/lib/gconf2/gconfd-2 5.

I assume, therefore, that my issue is with gconfd-2.5.  Since this is my first go around with a gnome based distribution I'm not clear on what gconfd does.  I'm going to continue reading up on it, but it's a little disheartening to see someone who has the same issues that I am, and hasn't recieved an answer to their question in 4 weeks.  

My install is a fresh install of ubuntu 5.10 and an upgrade to all packages via the synaptic tool.

Any help or insight would be appreciated.  I'm going to continue searching the board to see if there are any answers hidden here.  So far I have not been able to locate them.  But there are still a ton of pages to get through from my search results.  

I also find it interesting that the initial gconfd is a root pid, and after the crash the gconfd is a user pid.  

TIA,
AlmostAnotherUbuntuUser

---

### Post by AAUU on 2006-01-13
I just looked at another thread where a user ask a question about why his box was frozen in the morning.  A helpful user then responded with questions about power configuration, screen saver configuration, and firefox extensions.  

Now, the latter has me curious.  I've installed the newer version of firefox (1.5) via the unsupported automatix script along with all of the extensions.  Now, I'd rule this as the culprit, but for two reasons.  

1.  I played this game in Kubuntu and had the same gconfd errors in the logs.  For that installation I installed firefox 1.5 via the method described in one of the wiki pages (URL escapes me now) and I didn't install any of the plugins at all.

2.  Firefox isn't always open when the gconfd dies and restarts the X server session leaving me at the login prompt.

AlmostAntherUbuntuUser

---

### Post by AAUU on 2006-01-14
Ok, so I've reinstalled Ubuntu from scratch.  Then, without altering anything in the sources.list, I used the synaptec tool to upgrade any packages that needed upgrading. 

I haven't installed any new software at all.  The only thing I've done is surfed the web a bit with firefox 1.07 and turned off all power saver features for the monitor and the screensaver.

Then, while using firefox it crashes and I look in the user.log and I've got the same messages about GConf server not in use and shutting down.  I didn't get kicked out to the user login screen.  Just firefox died.

ps -elf | grep gconf shows me that the GConf Server, if I'm correct, is now running as my userid:

/usr/lib/gconf2/gconfd-2 5

Whereas before it was running as root.  I'm not sure if there's a privelage issue or what.

I love the fact that there's no man page for gconf, gconfd nor gconfd-2.

I guess this will become my own personal blog until someone with a greater understanding of gconf and probably gnome in general can shed some light on this issue.

For now, I'm off to research gconfd more thoroughly on the web as search results of these forums didn't produce any useful results in the first 4 pages returned.

AlmostAnotherUbuntuUser

[EDIT: Ah, information!  [http://developer.gnome.org/feature/archive/gconf/gconf.html](http://developer.gnome.org/feature/archive/gconf/gconf.html)
Perhaps I can just switch to Enlightenment or something and get rid of gnome entirely.  I know that Kubuntu still uses gconf, because I had the same issues there.]

[EDIT: So, I've come to understand that gconf2 is the gnome version of the windows registry.  Lovely.  I hated that on windows, and I'm sure I'm going to hate it here.  :(  I'm all for the config files for each app.  I like that.  Anyway, I have gone ahead and compiled my own firefox firefox 1.5rc3.  I'll see if I have more issues now.  This will for sure tell me if it's a firefox related problem or not.  I have left in the default 1.07 firefox for compatibility reasons.  But anytime I start firefox I'll be using the 1.5rc3 version.]

---

### Post by Titan1958 on 2006-01-20
I got the same thing in my logs but my pc still works perfecly . No reboot, nothing!

Still looking.....:cool:

---

