---
title: "Compiz stopped working"
date: 2012-07-05
forum: Desktop Environments
---

### Post by qwe2 on 2012-07-05
Compiz had been working fine for a while when all of a sudden it decided not to anymore. I think Ubuntu updates I installed yesterday are to be blamed for this, however I'm fairly new to the system so I don't know exactly what caused it.

I tried "compiz --replace" already with more or less success. First it seemed to have solved the problem but using the desktop cube or any effect related stuff ended up in flickering and after some time my desktop was broken (no borders on windows, annoying flickering when trying to do something with windows).

Output of "compiz --replace":

```
compiz (core) - Warn: Attempted to restack relative to 0x4400090 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4400093 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4400090 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4400099 which is not a child of the root window or a window compiz owns
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing gnomecompat options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing grid options...done
Initializing move options...done
Initializing resize options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing workarounds options...done
Initializing session options...done
Initializing wobbly options...done
Initializing animationaddon options...done
Initializing fade options...done
Initializing cube options...done
Initializing td options...done
Initializing rotate options...done
Initializing scale options...done
Initializing unitymtgrabhandles options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:4096): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
error subscribing to gestures
Initializing unityshell options...done
compiz (core) - Warn: Attempted to restack relative to 0x4400104 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4400108 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x440010b which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x440010f which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4400112 which is not a child of the root window or a window compiz owns
Setting Update "shadow_match"
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "open_effects"
Setting Update "open_durations"
Setting Update "open_matches"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "close_matches"
Setting Update "minimize_effects"
Setting Update "focus_effects"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "active_opacity"
Setting Update "panel_opacity"
Setting Update "autohide_animation"
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
Segmentation fault (core dumped)
```

Another "symptom" is when I log in I get a gray blank image for some seconds which I did not get before. Also the color of the unity Launcher changed, it won't take the color of the wallpaper anymore as it did before.

I have an nVidia GeeForce GT 525M with the latest driver from the nVidia page (if that's related somehow).

Any answers regarding the problem would be appreciated.

---

### Post by nipunshakya on 2012-07-05
> **qwe2 said:**
> Another "symptom" is when I log in I get a gray blank image for some seconds which I did not get before. Also the color of the unity Launcher changed, it won't take the color of the wallpaper anymore as it did before.


Hi and welcome to the forums. I had the same issue too... i had two things done for me....
1. Ran synaptic package manager, from there i searched 'compiz' , selected those installed in my machine and reinstalled them.
2. i had a corrupt library...which after replacement did the job for my machine....(but ur code's output doesnt say any lib error, so there is no need for this step)

The gray screen is no more now...

If you don't have synaptic package manager, install it via software center by searching 'synaptic package manager' on searchbox and run it.


Goodluck

---

### Post by qwe2 on 2012-07-05
Thanks for your reply.

I reinstalled everything related to compiz and the gray screen really did disappear but compiz is still not working. I tried the replace command again but it's just the same as before. Annoying flickering etc...

---

### Post by nipunshakya on 2012-07-05
hmm... so you said you got problem with unity's launcher changing its color too right? might be unity misbehaved in your machine... try ```
unity --reset
``` in your terminal... a reset in unity might do something as well..

---

### Post by qwe2 on 2012-07-05
"unity --reset" gives almost the same behavior as "copiz --replace" just without the effects being enabled ofcourse. (flickering and stuff)

Output of "unity --reset":

```
unity-panel-service: no process found
compiz (core) - Warn: Attempted to restack relative to 0x4a00090 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4a00093 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4a00090 which is not a child of the root window or a window compiz owns
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
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

(compiz:3772): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
error subscribing to gestures
Initializing unityshell options...done
compiz (core) - Warn: Attempted to restack relative to 0x4a00146 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4a00149 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4a0014d which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x4a00150 which is not a child of the root window or a window compiz owns
WARN  2012-07-05 13:09:14 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application311805604

WARN  2012-07-05 13:09:14 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application311805604
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
WARN  2012-07-05 13:09:15 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2012-07-05 13:09:15 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
Starting gtk-window-decorator
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
WARN  2012-07-05 13:18:01 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window41943632
WARN  2012-07-05 13:18:01 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520

```

After the last line it gets stuck and won't go further.

Edit: playing around with some windows ended up in its saying  "Segmentation fault (core dumped)" and "giving me back" the terminal. But at this point I lost the window borders and till the command was running unity launcher got the right colors but now it returned to black.

---

