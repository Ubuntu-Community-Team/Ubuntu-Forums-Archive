---
title: "Stuck in 2D"
date: 2012-04-28
forum: Desktop Environments
---

### Post by colmeweb on 2012-04-28
New LTS new problems. I just upgraded to 12.04 from 10.04 yesterday and everything was going fine. In order to use my duel screen I had to switch over to the 2D side and now I can't get back. I have tried restarting and logging in again but it didn't work. If I log in as a guest I can go to the 3D, but it won't let me under my own account. Please help me. Thanks.

---

### Post by dbombtek on 2012-04-28
Need more info on your setup but best guest is video card drive stuck or reinstall. Does 12 recognize you card?

---

### Post by colmeweb on 2012-04-28
First off, I don't know what happened, this thread should be under [Ubuntu]. I have no idea where that l came from.

I don't know what more information I can give. Unity 3d was working fine all day. I switched to the 2d side so that I could use a second monitor. And now I am stuck in 2d, but only on my username. In the guest session I can go back and forth from 3d and 2d. 

As far as 12.04 detecting my video card, it must because 3d still works on the guest session, but Hardware Lister doesn't seem to work in 12.04 so I cant say for 100%

Is there a way to reset or re-install my drivers or Unity? I have only been using the system for two days so if I have to start over it is no big deal, I just don't want to do another fresh install. 

Thanks.

---

### Post by Krytarik on 2012-04-28
> **colmeweb said:**
> Is there a way to reset or re-install my drivers or Unity? I have only been using the system for two days so if I have to start over it is no big deal, I just don't want to do another fresh install.
Please see here how to reset Unity's settings, and if needed, the rest of Compiz' settings as well:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by sffvba[e0rt on 2012-04-28
*Title changes to **[Ubuntu]***


404

---

### Post by colmeweb on 2012-04-29
So I tried the help that Krytarik gave me, thanks for that, and the result was this.

```
me@me-Satellite:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2600004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1200002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a00081

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

Screen geometry changed:
   0x0x1280x800


(compiz:3546): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00099!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.libindicator <unknown>:0 Desktop file '/usr/share/app-install/desktop/chromium-browser:chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 19:26:51 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 19:26:51 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
Initializing staticswitcher options...done
ERROR 2012-04-28 19:26:52 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
Starting gtk-window-decorator
WARN  2012-04-28 19:44:32 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648

WARN  2012-04-28 19:44:32 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648

WARN  2012-04-28 20:03:55 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window71313715
WARN  2012-04-28 20:05:02 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898d240

WARN  2012-04-28 20:05:02 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898d240

WARN  2012-04-28 20:05:02 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898d240

WARN  2012-04-28 20:05:03 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898d240

WARN  2012-04-28 20:26:40 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462

WARN  2012-04-28 20:26:41 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462

WARN  2012-04-28 20:31:52 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520

compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
WARN  2012-04-28 21:14:10 unity <unknown>:0 Failed to fetch monitor: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window73402387
WARN  2012-04-28 21:14:10 unity <unknown>:0 Failed to fetch maximized state: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window73402387
WARN  2012-04-28 21:14:10 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cdd0: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cdd0
WARN  2012-04-28 21:14:10 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cdd0: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cdd0
WARN  2012-04-28 21:14:59 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cf08

WARN  2012-04-28 21:15:19 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73403630: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window73403630
WARN  2012-04-28 21:15:19 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cc30: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc30
WARN  2012-04-28 21:15:19 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73403630: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window73403630
WARN  2012-04-28 21:15:19 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cc30: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc30
WARN  2012-04-28 21:17:03 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc98

WARN  2012-04-28 21:24:35 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cd00

WARN  2012-04-28 21:31:44 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cd68

WARN  2012-04-28 22:05:25 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cd68

WARN  2012-04-28 22:05:25 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cd68

WARN  2012-04-28 22:06:18 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window71355034
compiz (decor) - Warn: failed to bind pixmap to texture
WARN  2012-04-28 22:06:35 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cd00

WARN  2012-04-28 22:06:36 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cd00

WARN  2012-04-28 22:19:16 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73425595: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window73425595
WARN  2012-04-28 22:19:16 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cc98: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc98
WARN  2012-04-28 22:19:16 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73425595: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window73425595
WARN  2012-04-28 22:19:16 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cc98: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc98
compiz (decor) - Warn: failed to bind pixmap to texture

WARN  2012-04-28 22:30:19 unity <unknown>:0 Failed to fetch xid: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window73436001
WARN  2012-04-28 22:30:19 unity <unknown>:0 Failed to fetch monitor: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window73436001
WARN  2012-04-28 22:30:19 unity <unknown>:0 Failed to fetch maximized state: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window73436001
WARN  2012-04-28 22:30:19 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cc30: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc30
WARN  2012-04-28 22:30:19 unity <unknown>:0 Failed to fetch xid: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window73436001
WARN  2012-04-28 22:30:19 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cc30: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cc30
WARN  2012-04-28 22:39:15 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cf08

WARN  2012-04-28 22:39:15 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cf08

WARN  2012-04-28 22:46:08 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73445029: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window73445029
WARN  2012-04-28 22:46:08 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cdd0: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cdd0
WARN  2012-04-28 22:46:08 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73445029: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window73445029
WARN  2012-04-28 22:46:08 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x898cdd0: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x898cdd0
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
WARN  2012-04-28 22:50:31 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application518553784

WARN  2012-04-28 22:51:06 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462

WARN  2012-04-28 22:51:06 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462

WARN  2012-04-28 22:51:07 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462

compiz (decor) - Warn: failed to bind pixmap to texture
WARN  2012-04-28 22:51:34 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520
```

And after all those hours it didn't work. So I ran this 

```
me@me-Satellite:~$ echo $DESKTOP_SESSION
ubuntu-2d
me@me-Satellite:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS690
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

So ubuntu gurus what ells do you have for me?

---

