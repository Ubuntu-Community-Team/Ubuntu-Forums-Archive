---
title: "New user experience / problems"
date: 2006-01-15
forum: General Help
---

### Post by Fallen Guru on 2006-01-15
I'm not a total linux newbie, my home servers have been running Debian for years. For a variety of (mostly ideological) reasons I'd like my family's desktops to run linux as well. After all, 99% of what we run on top of Windows is FOSS anyway. (OpenOffice, Firefox, VLC, Wesnoth, ...)

Every few months I'll thus evaluate linux for use on our desktops, this time using Ubuntu. I like Gnome, Debian, and fast release cycles, go figure :)

The install on the tested machine (Tyan K8W, 2x Opteron 240, ATI X800 Pro) went smoothly, aside from a few glitches.

- the desktop ran at 60 Hz and couldn't be changed via the Gnome preferences item. The xorg.conf had some fictional ranges for vsync and hsync, when even auto-detection setting would have given 85 Hz - why not leave it on auto?

- the kernel loaded my onboard sound card first, resulting in it being the default card. That can't be helped, however changing the setting in the preferences does only set card 1 to default for Gnome apps. All others are unaffected and if you can't set the soundcard number from within the app, you're screwed. The Gnome prefs dialog should instead change the cards' load order.

- sound in general is heavily distorted or becomes so over time. Seems to have to do with ESD, need to investigate further.

- totem-gstreamer does not play 95% of my many video files, not even with all gstreamer0.8-plugins in universe installed. Either it plays slow motion, shows only the first frame, botches audio sync, gives cryptic errors or just crashes ... VLC and mplayer are fine. Which brings me to my biggest problem:

- gnome-vfs. Having a daemon that maps special URLs to files for apps that support it is great. So I can browse our file server's samba exports just fine using Natilus, however I cannot open  or edit any files there because most software can't handle the strange URLs. IMHO it isn't reasonable to recompile everything that opens files to use gnome-vfs, especially when mounting stuff works just fine. Browsing to a network share in Nautilus should create a directory under ~/Desktop where the share is then mounted.

Summary: The first few issues are easily corrected, but gnome-vfs is a design flaw in itself, how do you cope with that?

Since this isn't Ubuntu's fault my verdict is "positively impressed" :)

---

### Post by TheForumTroll on 2006-01-15
pass

---

### Post by johnnymo87 on 2006-01-15
[QUOTE=Fallen Guru]
- the desktop ran at 60 Hz and couldn't be changed via the Gnome preferences item. The xorg.conf had some fictional ranges for vsync and hsync, when even auto-detection setting would have given 85 Hz - why not leave it on auto?[/QUOTE]

This thread should help: [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973). Editing the xorg.conf file is probably the best solution.

---

### Post by cblanquer on 2006-01-15
Hi,

I am Kubuntu user, but installed as well Edubuntu (based on Gnome) so that basically I access to both front-ends applications.
Regarding video, I cannot make Kaffeine (KDE) nor Totem (Gnome) work properly. Instead "Noatun" does the job pretty well so that by now it is my favourite video app.
It can be a little anoying that the default apps do not provide (always) the service expected but it is great to have alternative that give the opportuny to perform whatever we need.
So my remark would be : try the other options and choose the one that is working, to save your time and effort, in next Dapper release we can re-evaluate what is working with little additional work and what reuqires to invest time.

---

### Post by GeneralZod on 2006-01-15
I think a lot of the media issues should be sorted come Dapper - I haven't really followed it very closely, but I think there was a fairly large discussion about the fact that even though gstreamer will soon be the de facto Linux media framework, gstreamer-0.8 should *not* have been the default in Breezy because it simply wasn't ready for widespread use.  gstreamer-0.10 is apparently much improved, though and it, or a later version, will be the default in Dapper.

---

### Post by Fallen Guru on 2006-01-16
Status:

- 60 Hz refresh: workaround by editing xorg.conf, hopefully fixed in Dapper

- gstreamer issues: let's see dapper

- gnome-vfs: ugly, really ugly, and by design ... oh well. KDE is not much better, Konqueror actually copies files on samba shares when I access them in non-KDE apps :( Still don't get why all these file managers don't just mount network / removable storage regularly.   

- distorted sound: still there, and not an ESD issue either. Even when I use alsa directly with no sound daemons running I get at most a few seconds of clean sound. Debian unstable has it too, at least with the current unstable kernel. Earlier kernels <= 2.6.10 were fine IIRC.
I reported the issue to alsa-user, no takers so far. Any ideas what to check?

---

