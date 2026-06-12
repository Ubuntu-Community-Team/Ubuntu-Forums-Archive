---
title: "compiz &amp; unity problem, desktop gone"
date: 2012-12-20
forum: Desktop Environments
---

### Post by linux.girl on 2012-12-20
Hi dear community,


 I hope you can help me...I made a  stupid mistake, I disabled the unity plugin on compiz and now my  desktop is missing. I already followed a few tutorials online, but none  of them helped. I have ubuntu 12.04 64 bit.


 If I do ctrl+alt+t I get a terminal, and from there I can launch  compiz and also do unity --reset. I restored the unity plugin, but to no  avail. When I run unity --reset, I get a desktop (not mine, probably a  default), but after reboot, desktop is gone again. This is what I get  when I run unity --reset:
 unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004
 compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a00004
 compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4000293
 Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
 (compiz:2786): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
ERROR 2012-12-20 23:29:33 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri: Operation not supported
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
WARN  2012-12-20 23:29:34 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-20 23:29:34 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-20 23:29:34 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-12-20 23:30:08 unity.iconloader IconLoader.cpp:438 Unable to load icon . GThemedIcon application-x-sharedlib gnome-mime-application-x-sharedlib application-x-generic at size 64
 Can you please help me?
 Thanks in advance,


 linux.girl

---

### Post by ajgreeny on 2012-12-20
Try
```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```which should first reset compiz then unity to the default settings.

---

### Post by monkeybrain2012 on 2012-12-20
Right click on your blank desktop to create an empty folder, then open it and on the side panel choose File system. Go to /usr/share/applications, find the icon for the compiz confi settings manager (ccsm) click it open and check the box Unity plugin.

---

### Post by linux.girl on 2012-12-21
Thanks to both, I had already that those options, but neither helped. After restart the desktop is still gone. And if I run unity --reset, I still get stuck here:

 unity --reset
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a00003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2c00167

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2478): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
WARN  2012-12-21 11:26:13 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
ERROR 2012-12-21 11:26:14 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri: Operation not supported
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-12-21 11:26:14 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x23bd050

WARN  2012-12-21 11:26:14 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x23bd050
WARN  2012-12-21 11:26:14 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x23bd050

WARN  2012-12-21 11:26:14 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window46137703
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
WARN  2012-12-21 11:26:15 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-21 11:26:15 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-21 11:26:15 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
Setting Update "main_menu_key"
Setting Update "run_key"


Any more ideas? What if I completely remove compiz, would that help? What other options are available to me? Complete re-install of the system?

:-(

Thanks in advance for any new suggestions.

linux.girl

---

### Post by linux.girl on 2012-12-21
Problem solved: I loged in using the recovery mode instead of regular boot. With recovery mode, I got my correct desktop back - from there, I went to compiz plugin and re-enabled the unity plugin and problem solved.

As I mentioned before, I had already tried to reenable the plugin in other ways and nothing helped, only from inside recovery mode did.

Hope this helps others with ths problem.

linux.girl

---

### Post by ajgreeny on 2012-12-21
Great!

Can you please go to thread tools at the top of the thread and mark as "Solved".

---

### Post by linux.girl on 2012-12-22
Done, and thanks for everything!

---

