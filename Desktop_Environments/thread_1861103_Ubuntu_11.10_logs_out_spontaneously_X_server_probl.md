---
title: "Ubuntu 11.10 logs out spontaneously X server problem?"
date: 2011-10-15
forum: Desktop Environments
---

### Post by lucacerone on 2011-10-15
Dear all,
after upgrading to Ubuntu 11.10 sometimes it happens a spontaneous log out.
Unfortunately I'm not an expert but reading I found out it might depend on the X server... looking at the file /var/log/Xorg.1.log I found out this:
> Fatal server error:
[    60.640] xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call
in Xorgo.0.org I don't see anything wrong, but I don't know what to look
for so there might be some issue that I don't know.

I really need a stable system for my work,
can some of you guys please help me?
Thanks a lot in advance,
Luca

---

### Post by oroles on 2011-10-16
> **lucacerone said:**
> Dear all,
after upgrading to Ubuntu 11.10 sometimes it happens a spontaneous log out.
Unfortunately I'm not an expert but reading I found out it might depend on the X server... looking at the file /var/log/Xorg.1.log I found out this:

in Xorgo.0.org I don't see anything wrong, but I don't know what to look
for so there might be some issue that I don't know.

I really need a stable system for my work,
can some of you guys please help me?
Thanks a lot in advance,
Luca

I have the same problem! I don't know which is the cause. I hope the future updates will solve the issue.

---

### Post by lucacerone on 2011-10-16
After the upgrades happens to me again...
It seems to me to log out when I leave my computer unattended for a while,
like if I leave it on for lunch or something like this....
Unfortunately I can't reproduce the issue.. and don't know where
to look to understand where the problem is...
Did you have any success in figuring out what is not working?
Thanks for the help...
it's always like that after an upgrade I always regret a bit to have done it :)

---

### Post by oroles on 2011-10-16
> **lucacerone said:**
> After the upgrades happens to me again...
It seems to me to log out when I leave my computer unattended for a while,
like if I leave it on for lunch or something like this....
Unfortunately I can't reproduce the issue.. and don't know where
to look to understand where the problem is...
Did you have any success in figuring out what is not working?
Thanks for the help...
it's always like that after an upgrade I always regret a bit to have done it :)
I've tried to make a fresh install to saw if the issue persist. My OS crash like before :((

---

### Post by Chonnawonga on 2011-10-16
I'm having this problem too. Has anyone filed a bug report yet?

---

### Post by NModern on 2011-10-16
I was having this issue when my SATA cable of HDD was broken, so I changed it and now everything works well. And after upgrade I have not faced this problem.

You can probe to turn off screen saver.

---

### Post by haifeng_chicago on 2011-10-16
I ran into almost the same problem after the 11.10 'upgrade' - this is terriable.  The problem occurs only if I leave the current user logon, and switch the user through the logon screen.  The there's no response from the 2nd logon attempt, the password box become grey out completely.  I can still use the ALT-F7 key to return to the previous user session.  But when I tried logout from it, the shell exits (the top panel disappears), but the other applications remains.  I had to use ALT-F1 to a text terminal and halt the machine.

---

### Post by Chonnawonga on 2011-10-16
NModern:
I can't imagine this is a SATA cable problem, since so many of us are suddenly having the problem at once. Good to think about, though!

What do you mean by "probe to turn off screen saver"? How does one do that? Unity doesn't seem to have any screensaver controls at all. :(

---

### Post by lucacerone on 2011-10-17
Dear all,
I don't think is a cable issue since I have the same problem on two different computers (one desktop and one laptop). Maybe we should file a bug report?

---

### Post by lucacerone on 2011-10-17
Dear it seems to me to be really a Compiz issue:
here is what I found in my syslog files, for the time a sudden shutdown happened a few minutes ago:
```
Oct 17 16:09:01 LuCe-UCD postfix/local[11056]: 5B72C640635: to=<root@host>, orig_to=<root>, relay=local, delay=0.19, delays=0.13/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Oct 17 16:09:01 LuCe-UCD postfix/qmgr[1637]: 5B72C640635: removed
Oct 17 16:17:01 LuCe-UCD CRON[11076]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8040) user=luca command=bamfdaemon nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8043) user=luca command=unity-panel-ser nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 2199) user=luca command=gconf-helper nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7951) user=luca command=gvfsd-metadata nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8221) user=luca command=evolution-alarm nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7901) user=luca command=dbus-launch nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 5550) user=luca command=MATLAB nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8482) user=luca command=desktopcouch-se <defunct> nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8120) user=luca command=unity-applicati nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8088) user=luca command=geoclue-master nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8149) user=luca command=gdu-notificatio nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7984) user=luca command=gvfs-afc-volume nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 9070) user=luca command=firefox nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8000) user=luca command=gvfsd-trash nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3035) user=luca command=beam.smp nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8409) user=luca command=update-notifier nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7940) user=luca command=gsd-printer nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7925) user=luca command=gconfd-2 nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7934) user=luca command=gnome-settings- nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7977) user=luca command=gvfs-gdu-volume nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8223) user=luca command=gwibber-service nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8106) user=luca command=goa-daemon nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7858) user=luca command=gnome-session nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8151) user=luca command=zeitgeist-datah nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7955) user=luca command=dconf-service nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8092) user=luca command=telepathy-indic nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7964) user=luca command=bluetooth-apple nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7904) user=luca command=ssh-agent nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8533) user=luca command=maple nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8124) user=luca command=unity-music-dae nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7968) user=luca command=nautilus nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 10953) user=luca command=evince nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 10959) user=luca command=evinced nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7909) user=luca command=dbus-daemon nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8594) user=luca command=mserver nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7916) user=luca command=gvfs-fuse-daemo nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8375) user=luca command=gwibber-service nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8037) user=luca command=unity-window-de nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7987) user=luca command=gvfs-gphoto2-vo nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8368) user=luca command=ubuntuone-syncd nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8057) user=luca command=indicator-sessi nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3026) user=luca command=couchdb nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 2175) user=luca command=pulseaudio nice=-11
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8424) user=luca command=thunderbird-bin nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3058) user=luca command=heart nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7966) user=luca command=nm-applet nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8103) user=luca command=e-addressbook-f nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8467) user=luca command=deja-dup-monito nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8147) user=luca command=zeitgeist-daemo nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 9595) user=luca command=skype nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8601) user=luca command=Wunderlist nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8051) user=luca command=indicator-appli nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 9582) user=luca command=plugin-containe nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7946) user=luca command=gnome-screensav nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8228) user=luca command=e-calendar-fact nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8036) user=luca command=sh nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3104) user=luca command=inet_gethost nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8474) user=luca command=desktopcouch-se nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7941) user=luca command=compiz nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8220) user=luca command=applet.py nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7953) user=luca command=tomboy nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7911) user=luca command=gvfsd nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8123) user=luca command=unity-files-dae nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 5482) user=luca command=MATLAB nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 9575) user=luca command=plugin-containe nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 5616) user=luca command=MATLAB nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3034) user=luca command=couchdb nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8011) user=luca command=obex-data-serve nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7905) user=luca command=dbus-daemon nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3105) user=luca command=couchjs nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7908) user=luca command=dbus-launch nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8095) user=luca command=mission-control nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 9298) user=luca command=gvfsd-http nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8169) user=luca command=unity-musicstor nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8531) user=luca command=xmaple nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8071) user=luca command=indicator-messa nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7965) user=luca command=gnome-fallback- nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8056) user=luca command=indicator-datet nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 3103) user=luca command=inet_gethost nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7961) user=luca command=polkit-gnome-au nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7967) user=luca command=blueman-applet nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8148) user=luca command=cat nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7849) user=luca command=gnome-keyring-d nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 9111) user=luca command=MATLAB nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8060) user=luca command=indicator-sound nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8556) user=luca command=java nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 8017) user=luca command=gvfsd-burn nice=0
Oct 17 16:17:01 LuCe-UCD killer[11079]: kill(15, 7994) user=luca command=notify-osd nice=0
Oct 17 16:17:02 LuCe-UCD gnome-session[7858]: WARNING: Detected that screensaver has left the bus
Oct 17 16:17:02 LuCe-UCD gnome-session[7858]: GConf-WARNING: Got Disconnected from DBus.#012
Oct 17 16:17:04 LuCe-UCD gnome-session[7858]: WARNING: Client '/org/gnome/SessionManager/Client11' failed to reply before timeout
Oct 17 16:17:04 LuCe-UCD gnome-session[7858]: WARNING: Client '/org/gnome/SessionManager/Client6' failed to reply before timeout
Oct 17 16:17:06 LuCe-UCD kernel: [27867.901087] show_signal_msg: 36 callbacks suppressed
Oct 17 16:17:06 LuCe-UCD kernel: [27867.901092] compiz[7941]: segfault at 6b73656c ip b42983d4 sp bfbe6350 error 4 in libunity-core-4.0.so.4.0.0[b425a000+70000]
Oct 17 16:17:06 LuCe-UCD gnome-session[7858]: WARNING: Application 'compiz.desktop' killed by signal
Oct 17 16:17:09 LuCe-UCD acpid: client 7744[0:0] has disconnected
Oct 17 16:17:09 LuCe-UCD acpid: client connected from 11114[0:0]
Oct 17 16:17:09 LuCe-UCD acpid: 1 client rule loaded
Oct 17 15:17:14 LuCe-UCD rtkit-daemon[1746]: Successfully made thread 11182 of process 11182 (n/a) owned by '128' high priority at nice level -11.
```

Can somebody help???
Thanks in advance,
Luca

---

### Post by johnnybgoode83 on 2011-10-17
My system doesn't even have to be idle before it will randomly log me off.  It's bloody annoying as it is the only bug I've come across.

---

### Post by arazour on 2011-10-19
Same problem here. Couldn't find anything strange in Xorg logs. it really is getting on my nerves

---

### Post by gp2x on 2011-10-21
Yup, this sucks - I need to code this weekend and Ill have to be hitting save every 2 seconds.

---

### Post by oak3 on 2011-10-24
Yeah I have this problem too... I use Kubuntu 11.10 (updated from 11.04) and Dell laptop with Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller. I should have not updated my computer - this last update was terrible time waster for me..... Really sad, time to start thinking about alternatives....

---

### Post by Prosis on 2011-10-28
No news on this? This is the only thing that stops me from keeping my Ubuntu...(I'm on Windows for now because I work with my computer).

Does it still do this to you guys? Has anyone found a solution?

---

### Post by typhoon_tip on 2011-10-29
Hey guys, not sure if is the XOrg Synaptic related bug of 11.04, but sounds terribly similar.

Do you all have Synaptic touchpads ?

Try this: open System Settings/Mouse, go to Touchpad, "Disable Touchpad while typing", remove this option and reboot (better), try to see if at least the autologoff is reduced.

Another possible reason (this worked for me): I have ATI driver. I try to update to the 11.9 version from AMD website, and it started to have this problem with random X crashes and forced autologoff. Restored the stock driver first, then fglrx driver from Ubuntu rep, working like a charm now (albeit I cannot use gnome 3, but I don't want for now).

---

### Post by Prosis on 2011-10-29
For the touchpad you mean to check or uncheck "Disable Touchpad While Typing"

But I wouldn't be surprise if it was ATI! :P

I can't try it so, anyone here did?

---

### Post by typhoon_tip on 2011-10-29
> **Prosis said:**
> For the touchpad you mean to check or uncheck "Disable Touchpad While Typing"

But I wouldn't be surprise if it was ATI! :P

I can't try it so, anyone here did?

Urgh sorry, I meant "disable" it, so uncheck that option. It uses librecord.so module of XOrg, which is the one bugged (I don't know if it was ever fixed...).

ATI 11.9 driver from AMD website is breaking X from time to time, causing the logoff. Everytime you attempt to change anything in Compiz, you get logged off as well, and that's the moment I started to relate the problem. Another linked problem for me was that I could not shutdown anymore, everytime I tried, X would crash and log me off instead of restart/shutdown !

---

### Post by bipco on 2011-10-29
Hi

I've got this too.  Wasn't happening when I first installed - seems to have started today, possibly after an update.  After trying the possible fix above I couldn't even log in to Unity 3-D.  Went into Gnome, but after a bit that logged out too.  Trying Unity 2-D now.

---

### Post by typhoon_tip on 2011-10-29
> **bipco said:**
> Hi

I've got this too.  Wasn't happening when I first installed - seems to have started today, possibly after an update.  After trying the possible fix above I couldn't even log in to Unity 3-D.  Went into Gnome, but after a bit that logged out too.  Trying Unity 2-D now.

You had ATI driver ? If yes, the correct removal procedure known to work to remove the driver is the following:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)
```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo rm -rf /etc/ati
```

Do all the above commands again before attempting to enter 3D again (Gnome or Unity). By doing it again, from first command to last, you will be sure that any piece of fglrx is correctly removed. fglrx is known to leave pieces behind even after uninstall from Jockey.

---

### Post by bipco on 2011-10-30
Actually no, not ATI, nVidia.  Seems to be OK now, so maybe today's updates fixed it - noticed that there was an xorg update in it.

---

### Post by snakeplizzken on 2011-10-30
Interesting.

I am running 10.04 Lucid Lynx and I have notices exactly the same problem although last time was a few month ago.

It seemed like if I let the computer on for a while when I got back I had been logged out.

Never happened then I was working with the computer - always in idle mode for some time.

---

### Post by MadHaxor on 2011-11-03
This is still happening to me. Can anyone think of any other solutions?

---

### Post by Prosis on 2011-11-03
> **MadHaxor said:**
> This is still happening to me. Can anyone think of any other solutions?

Did you remove completely ATI drivers to install the version that came out October 31st?

---

### Post by renderhead on 2011-11-18
This is happening to me too - right from the first session after installing 11.10 a couple of weeks ago. I'm just using the i7 2700K integrated GPU, so I don't think it's related to buggy video drivers (seems to affect ATi/AMD, nVidia and Intel). My system suddenly logs out, generally within the first minute of booting to the desktop.

Not really sure what triggers the problem - seems to frequently happen after I press the 'Windows' key to bring up the Unity Dash for the first time in a session, and start typing. Other times, it seems to happen when I do something that affects the file system through Nautilus (like create a new folder).

Fortunately, it only seems to happen once per boot-up - after the first 'spontaneous logout', it doesn't happen again within the re-logged session, regardless of how many hours I use it.

Next time it happens (already happened tonight), I'll have a look for anything suspicious in the X server logs...

---

### Post by typhoon_tip on 2011-11-18
> **renderhead said:**
> This is happening to me too - right from the first session after installing 11.10 a couple of weeks ago. I'm just using the i7 2700K integrated GPU, so I don't think it's related to buggy video drivers (seems to affect ATi/AMD, nVidia and Intel). My system suddenly logs out, generally within the first minute of booting to the desktop.

Not really sure what triggers the problem - seems to frequently happen after I press the 'Windows' key to bring up the Unity Dash for the first time in a session, and start typing. Other times, it seems to happen when I do something that affects the file system through Nautilus (like create a new folder).

Fortunately, it only seems to happen once per boot-up - after the first 'spontaneous logout', it doesn't happen again within the re-logged session, regardless of how many hours I use it.

Next time it happens (already happened tonight), I'll have a look for anything suspicious in the X server logs...

Try to update your system with all "proposed" updates (pay attention to the Kernel tough, you can skip that): backup everything first, I have read that sometimes the system wit 3.0.13 may not start anymore).

---

### Post by prioritythinking on 2011-11-18
So my new upgrade to Ubuntu 11.10 logs off . Its been about 4 weeks of the session logging off and going to the log in screen !  I found this ( "OK, open a terminal and type the command "gconf-editor". Using the
tree view on the left, navigate to /->apps->gnome-screensaver. Check
that the setting "logout_enabled" on the right is unchecked[Alessandro Menti (alessandro-menti)]("https://launchpad.net/%7Ealessandro-menti").)    and it may have lead me to a solution" instead of going to gnome-screensaver I did this open a terminal and type the command "gconf-editor". Using the
 tree view on the left, navigate to /->apps->desktop>gnome>sessions . Then you will see on the window Name and value idle-delay and a # mine was 23 or some small # I change it to 1000 . I don't know what other effects this will have but my computer has not logged off now and I was able to type this whole post ! ya .

Update it logged me off again after about 4 hours . :(
No this didn't fix the random log out problem . :( what the heck ! I would like to get a cam corder and film the top command to see if it shows something .

---

### Post by MadHaxor on 2011-11-26
Still getting this problem after a month. Surely someone has to know what is going wrong? It's incredibly frustrating.

---

### Post by Copper Bezel on 2011-11-27
Since there are various different related problems listed in this thread, describe your problem a little more specifically. What happens when the system spontaneously logs out (or X crashes, since these are similar events,) and are there any unusual errors in the log? Are there specific circumstances that make it more likely to occur?

I've had similar problems, for instance, on resuming from suspend, and the log ended without any unusual errors (looking the same as if I'd logged out intentionally.)

---

### Post by renderhead on 2011-11-29
It appears my problems run deeper than simply being logged out. My Intel HD3000 GPU seems to be faulty, as I can't get a stable 1920x1080 resolution now. Completely corrupt display under Linux, Windows 7, Linux live CDs (which worked just fine before). Strangely, lesser resolutions work without issue.

I'm putting this here in the thread because my 'forced logout' problem (possibly caused by a crashed X server) may well be due to a defective Intel GPU, rather than Linux itself.

In fact, the most recent two or three times I used this machine (before the display corruption), I don't recall experiencing the log-out problem. This may be since the 3.0.13 kernel update...

Anyway, I'll see if I still get logged-out after I get myself a new CPU under warranty.

---

### Post by Copper Bezel on 2011-11-29
Agreed - I've had other related problems (X crashes, X hangs, total death of the GPU) under other circumstances in both 10.10 and 11.04 on the same hardware. They just manage to look different enough from system to system to look like (and possibly be) new problems.

Incidentally, I haven't had a spontaneous logout in over a week, now, which lends credence to the GPU explanation, and specifically the theory that my GPU simply punishes me for a month whenever I change anything.

---

### Post by cris9288 on 2012-02-05
I am also having this problem. I have an hp dv4 with an intel i915 driver. After the log out i check my x server logs and see that a segmentation fault is causing the logout, but nothing especially useful appears. someone should file a bug report.

---

