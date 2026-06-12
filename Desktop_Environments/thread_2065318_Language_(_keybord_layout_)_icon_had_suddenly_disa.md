---
title: "Language ( keybord layout ) icon had suddenly disappeared"
date: 2012-10-01
forum: Desktop Environments
---

### Post by ahrambc on 2012-10-01
Hi

I'm using Ubuntu 12.04 with Unity and Mate.

My problem is in Unity only.

I have english and arabic keyboard layouts.

The Language ( keybord layout ) icon had suddenly disappeared from the upper panel. I had tried many commands and googled a lot without results.

I can't write in arabic now, only english inspite of the arabic layout is there.

any suggestions.

Thank you in advance.

---

### Post by ahrambc on 2012-10-01
[IMG]http://imageshack.us/a/img809/9224/selection003u.jpg[/IMG]

---

### Post by ahrambc on 2012-10-01
[IMG]http://imageshack.us/a/img40/4846/selection004.jpg[/IMG]

---

### Post by ohmysql on 2012-10-01
I was having a similar problem. Interestingly, the problems seems to have been that upon bootup, the system was creating an error box (I had an error in my monitor settings). It was only when I closed this error box that the rest of the language bar loaded.

Probably not applicable or helpful.

---

### Post by ahrambc on 2012-10-01
> **ohmysql said:**
> I was having a similar problem. Interestingly, the problems seems to have been that upon bootup, the system was creating an error box (I had an error in my monitor settings). It was only when I closed this error box that the rest of the language bar loaded.

Probably not applicable or helpful.

Thanks for your reply but unfortunately this is not my case

---

### Post by ahrambc on 2012-10-01
I tried this command but without an effect

[PHP]unity --reset[/PHP]

also tried 

[PHP]sudo apt-get update[/PHP]

---

### Post by ahrambc on 2012-10-02
Trying this command

[PHP]killall gnome-panel[/PHP]and here is the result

[PHP]gnome-panel: no process found[/PHP]

---

### Post by ahrambc on 2012-10-02
[SIZE=3]Also tried

[PHP]gconftool-2 --recursive-unset /apps/compiz-1 unity --reset[/PHP]and got this[/SIZE] [SIZE=3]

[PHP]Error while parsing options: Unknown option --reset 

Run 'gconftool-2 --help' to see a full list of available command line options  [/PHP][/SIZE]

---

### Post by ahrambc on 2012-10-02
[SIZE=3]And tried

[/SIZE][SIZE=3][PHP]unity --reset-icons[/PHP]

here is part of the output, then it hangs

[PHP]Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x140001f

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x300007a

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

(compiz:4051): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
WARN  2012-09-28 00:47:21 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xa0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xa000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xa000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xa0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xa0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xa0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-09-28 00:47:22 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-09-28 00:47:22 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-09-28 00:47:22 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
Initializing staticswitcher options...done
ERROR 2012-09-28 00:47:23 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key" [/PHP][COLOR=#000000][COLOR=#DD0000] [/COLOR][/COLOR][/SIZE]

---

### Post by ahrambc on 2012-10-03
[SIZE=3]Can I report a bug about this problem[/SIZE]

---

### Post by OzzyFrank on 2012-10-07
I'd definitely think about going to Bugzilla and reporting this as a bug. It's one thing for the icon to be missing or unuseable, but having no access to your Arabic characters as outlined in the pics is pretty messed up.

---

