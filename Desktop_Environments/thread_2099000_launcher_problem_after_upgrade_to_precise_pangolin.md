---
title: "launcher problem after upgrade to precise pangolin"
date: 2012-12-28
forum: Desktop Environments
---

### Post by paeppi.p on 2012-12-28
Hi,

after upgrading from Ubuntu 10.04 (lucid lynx) to Ubuntu 12.04 (precise pangolin) almost everything works fine, except: launcher and head-up display.

Launcher problem: left-click on an icon in the launcher sometimes works, but frequently does not trigger start of the application in question. Luckily, starting the dash works reliably, so I can always start my applications via the dash. Nevertheless: the launcher should work.
 
Head-up display does not produce any search results.

My hardware: Toshiba Satego X200 laptop.

Prio to upgrading I tested Ubuntu 12.04 from a bootable DVD and it worked fine. Prior to upgrading I de-installed almost all non-Canonical-supported packages, and afterwards re-installed via Ubuntu Software Center and Synaptic whatever I need.

---

### Post by daslinkard on 2012-12-30
Please try the following terminal command and see if this fixes your issue....
```
unity --reset-icons
```Hopefully this helps...

---

### Post by paeppi.p on 2013-01-02
> **daslinkard said:**
> Please try the following terminal command and see if this fixes your issue....
```
unity --reset-icons
```Hopefully this helps...

Unfortunately this didn't help.
 
Upon execution of the proposed command, everything disappeared from the screen shortly. 
When the launcher etc reappeared, the thunderbird icon had been dropped.

In the terminal a lengthy message was displayed. 
Execution of the command seemed to be hanging, so I tried to abort it with ^C.
This caused launcher and panel to disappear from the screen, 
but control still did not return to the shell.
To restore working conditions I stopped the laptop physically,
after reboot panel and launcher are back, but even more icons do not appear in the launcher any more.

Below I am quoting the message, which has beem displayed in the terminal. 

I hope this gives a clue as to what is wrong.

myself@laptop:~$ unity --reset-icons
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

(compiz:2719): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
WARN  2013-01-02 16:13:56 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
Initializing unityshell options...done
WARN  2013-01-02 16:13:57 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-02 16:13:57 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-02 16:13:57 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-02 16:13:57 unity.launcher Launcher.cpp:3088 Object registration failed. Won't get dynamic launcher addition.
ERROR 2013-01-02 16:13:57 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"

WARN  2013-01-02 16:14:52 unity <unknown>:0 Unable to fetch children: Keine derartige Schnittstelle »org.ayatana.bamf.view« des Objekts im Pfad /org/ayatana/bamf/application62801462

ERROR 2013-01-02 16:14:54 unity.glib-gobject <unknown>:0 g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

---

### Post by sandyd on 2013-01-12
Moved to Desktop Environments on request

---

