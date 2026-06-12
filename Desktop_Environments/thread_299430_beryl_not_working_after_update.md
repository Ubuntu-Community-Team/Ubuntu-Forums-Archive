---
title: "beryl not working after update"
date: 2006-11-14
forum: Desktop Environments
---

### Post by FuzZy2006 on 2006-11-14
i've just updated beryl from trevino's svn repository and when i try to run it, it doesn't display. the output from the console says: ```
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: '/usr/lib/beryl/libsettings.so' plugin version does not match beryl version.
beryl: '/usr/lib/beryl/libsettings.so' plugin has some sizeof() mismatch.
beryl: Couldn't load plugin 'settings'
beryl: '/usr/lib/beryl/libsettings.so' plugin version does not match beryl version.
beryl: '/usr/lib/beryl/libsettings.so' plugin has some sizeof() mismatch.
beryl: Couldn't load plugin 'settings'
beryl: Couldn't load plugin 'crashhandler'
beryl: Couldn't load plugin 'decoration'
beryl: Couldn't load plugin 'splash'
beryl: Couldn't load plugin 'wobbly'
beryl: Couldn't load plugin 'animation'
beryl: '/usr/lib/beryl/libcube.so' plugin version does not match beryl version.
beryl: '/usr/lib/beryl/libcube.so' plugin has some sizeof() mismatch.
beryl: Couldn't load plugin 'cube'
beryl: Couldn't load plugin 'rotate'
beryl: Couldn't load plugin 'inputzoom'
beryl: Couldn't load plugin 'scale'
beryl: Couldn't load plugin 'move'
beryl: Couldn't load plugin 'resize'
beryl: '/usr/lib/beryl/libplace.so' plugin version does not match beryl version.
beryl: '/usr/lib/beryl/libplace.so' plugin has some sizeof() mismatch.
beryl: Couldn't load plugin 'place'
beryl: Couldn't load plugin 'switcher'
beryl: Couldn't load plugin 'water'
beryl: Couldn't load plugin 'neg'
beryl: Couldn't load plugin 'bs'
beryl: Couldn't load plugin 'put'
beryl: Couldn't load plugin 'fade'
beryl: Couldn't load plugin 'screenshot'
beryl: Couldn't load plugin 'state'

```
I guess that the plugins update without the core to update. pls help me what can i do. when i try to upgrade again, there is no beryl update.

---

### Post by ThrobbingBrain66 on 2006-11-14
I'm having issues too...for now I've just reverted to running Metacity.  If you are using the SVN repos you have to be prepared for breakage.  If you don't want this hassle you should just stick with the official beryl repos.

---

### Post by rancourt on 2006-11-14
Yep. Same problem here. Most distressing. If I fix it, you'll know immediately.

---

### Post by GStubbs43 on 2006-11-14
Same here, I removed beryl and reinstalled 0.1.1 from the beryl-project repos.

---

### Post by whomever21 on 2006-12-13
i was having the same problem so i tried the repo suggested here:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA#Adding_Beryl_repository](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA#Adding_Beryl_repository)

beryl loads, but i don't have any options to choose from under beryl settings manager. the good news is it kept all my original settings, so no biggie =)

---

