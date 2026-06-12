---
title: "Unity &amp; Gnome not loading properly"
date: 2012-01-25
forum: Desktop Environments
---

### Post by ColdSyphon on 2012-01-25
Hi guys

Having a problem with my Ubuntu installation. I'm finding that when I log on, the Unity bar doesn't load and the top menu doesn't load at all either. The only way I can access any applications is because I set Cairo to start on log-in.

I think my problem is kind of similar to what's being describe in this thread [http://ubuntuforums.org/showthread.php?t=1875218]("http://ubuntuforums.org/showthread.php?t=1875218") except I'm running a single monitor which is running off the grahpics card adapter on the motherboard.

Another thing (if I'm allowed to include this) is that I've noticed that the "Shutdown" option doesn't work at all, whether I'm logged in or not. So I've had to resort to shutting down using the Terminal which isn't ideal really. Any ideas?

---

### Post by typhoon_tip on 2012-01-25
> **ColdSyphon said:**
> Another thing (if I'm allowed to include this) is that I've noticed that the "Shutdown" option doesn't work at all, whether I'm logged in or not. So I've had to resort to shutting down using the Terminal which isn't ideal really. Any ideas?

Do you mean by any chance that instead of Shutdown the system just logs you off ? If yes, it is 99% due to graphic card driver (I have had the same problem before with a broken installation of ATI/FGLRX driver out of AMD website, due to me anyway).

---

### Post by ColdSyphon on 2012-01-25
> **typhoon_tip said:**
> Do you mean by any chance that instead of Shutdown the system just logs you off ? If yes, it is 99% due to graphic card driver (I have had the same problem before with a broken installation of ATI/FGLRX driver out of AMD website, due to me anyway).

Really? It's just that the thing has been working fine for over a week or so, and at no point have I ever been prompted to install proprietary drivers for the graphics card. The system seemed to work fine straight out of the box. The only other upgrades I've done have been to the base Linux kernel and playing around with package installation.

It sounds plausible to me that this issue with the graphics card drivers is also causing the Unity/menu bar problem?

---

### Post by typhoon_tip on 2012-01-25
Try and run:
```
unity --reset
```

And do not close the terminal afterwards. Instead, logoff and login after a 1 or 2 minutes.

---

### Post by ColdSyphon on 2012-01-26
> **typhoon_tip said:**
> Try and run:
```
unity --reset
```

And do not close the terminal afterwards. Instead, logoff and login after a 1 or 2 minutes.

I got really fed up with it in the end and re-installed the OS, It sort of started working again after I input the command you suggested, but I wasn't too sure what the output in terminal meant. On top of that it still had the problem where I couldn't shut the computer down from the GUI. Sorry if this sounds really thick but I literally have pretty much 0 experience of Linux as I've used Windows all my life:

```
daveh@daveh-HP-Compaq-dx2400-Microtower-PC:~$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done

Screen geometry changed:
   0x0x1680x1050

unity-panel-service: no process found
Initializing unityshell options...done
WARN  2012-01-25 20:38:07 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
DEBUG 2012-01-25 20:38:07 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1680 h=1050
Initializing staticswitcher options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a00028

WARN  2012-01-25 20:39:08 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-25 20:39:08 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-25 20:39:08 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-01-25 20:39:08 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-01-25 20:39:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-25 20:39:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-25 20:39:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-01-25 20:39:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-01-25 20:39:27 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-01-25 20:39:27 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2012-01-25 20:39:27 glib.dee <unknown>:0 Transaction from com.canonical.Unity.Lens.commands.T1327523967.Categories is in the past. Ignoring transaction.
WARN  2012-01-25 21:02:18 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



```

---

