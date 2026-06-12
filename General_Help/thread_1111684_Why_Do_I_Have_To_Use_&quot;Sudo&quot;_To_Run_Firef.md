---
title: "Why Do I Have To Use &quot;Sudo&quot; To Run Firefox?"
date: 2009-03-30
forum: General Help
---

### Post by umechanism on 2009-03-30
Specs:

OS = Ubuntu 8.10 32 Bit
Firefox 3.07
Dell Studio Desktop

Firefox will no longer launch just by clicking on the desktop icon.  Doing so simply gets that "spinning symbol" around the icon then it stops after about five seconds.  FF never launches.  The only way I can make it run is by typing "sudo firefox" then it runs.  I have uninstalled and reinstalled FF numerous times via Synaptic.  I've deleted all the .mozilla folders.  I'm really at my wits end.

Does anyone know what is going on?  Is there a permission set somewhere that is causing this problem?

Thanks.

---

### Post by Ericyzfr1 on 2009-03-30
You wrote "No longer", which implies that it did, right? Did you modify anything?

---

### Post by kanikilu on 2009-03-30
> **umechanism said:**
> Specs:

OS = Ubuntu 8.10 32 Bit
Firefox 3.07
Dell Studio Desktop

Firefox will no longer launch just by clicking on the desktop icon.  Doing so simply gets that "spinning symbol" around the icon then it stops after about five seconds.  FF never launches.  The only way I can make it run is by typing "sudo firefox" then it runs.  I have uninstalled and reinstalled FF numerous times via Synaptic.  I've deleted all the .mozilla folders.  I'm really at my wits end.

Does anyone know what is going on?  Is there a permission set somewhere that is causing this problem?

Thanks. What happens if you run it from the terminal? ```
firefox &
``` Do you get a permission error? If so, check the permissions of the firefox folder. For 3.0.7, try: ```
ls -l /usr/lib/firefox-3.0.7
```

Wait...you said you're using a desktop icon. Can you try just running it from the menu? Applications > Internet > Firefox Web Browser

---

### Post by umechanism on 2009-03-30
> **kanikilu said:**
> What happens if you run it from the terminal? ```
firefox &
``` Do you get a permission error? If so, check the permissions of the firefox folder. For 3.0.7, try: ```
ls -l /usr/lib/firefox-3.0.7
```

Wait...you said you're using a desktop icon. Can you try just running it from the menu? Applications > Internet > Firefox Web Browser

Here's what I get:

```
firefox &
[1] 31304
```
Nothing happened here - firefox did not launch.

```
ls -l /usr/lib/firefox-3.0.7
total 8
drwxr-xr-x 2 root root 4096 2009-03-28 **components**
drwxr-xr-x 3 root root 4096 2009-03-27 **updates**
```
Yes, FF used to work correctly but I think I may have accidentally changed some permissions but I'm not sure where or how.

---

### Post by kanikilu on 2009-03-30
> **umechanism said:**
> Here's what I get:
```
ls -l /usr/lib/firefox-3.0.7
total 8
drwxr-xr-x 2 root root 4096 2009-03-28 **components**
drwxr-xr-x 3 root root 4096 2009-03-27 **updates**
```
Yes, FF used to work correctly but I think I may have accidentally changed some permissions but I'm not sure where or how. Judging by the contents of that directory, it seems like firefox has been updated. Did you update to 3.0.8? If so, check the permissions on that directory as well.

If you do have 3.0.8, you can also try running it directly from that directory: ```
/usr/lib/firefox-3.0.8/firefox &
``` If that doesn't work, maybe try adding "-ProfileManager" as an option to firefox and see if that does anything...

---

### Post by ibuclaw on 2009-03-30
We are now running on (or at least should be running on) firefox-3.0.8
```
readlink $(which firefox-3.0)
```

```
ls -l /usr/lib/firefox-3.0.8/
```

Regards
Iain

---

### Post by ibuclaw on 2009-03-30
> **kanikilu said:**
> Judging by the contents of that directory, it seems like firefox has been updated. Did you update to 3.0.8? If so, check the permissions on that directory as well.

If you do have 3.0.8, you can also try running it directly from that directory: ```
/usr/lib/firefox-3.0.8/firefox &
``` If that doesn't work, maybe try adding "-ProfileManager" as an option to firefox and see if that does anything...

Ney, you are wrong, but close though...

You run the script which setups up the environment for firefox to run in.
```
/usr/lib/firefox-3.0.8/firefox.sh &
```
but the command **firefox-3.0** should already be linked in with it.

@umechanism

Also, check what, and how many processes are running on your machine.
**System->Administration->System Monitor**

If there are any Sleeping or Zombie firefox processes, kill them. If you see a high CPU usage app, or a high Memory usage app. Post their process names here, and we'll delegate whether or not they should be temporarily killed.

Regards
Iain

---

### Post by Agent ME on 2009-03-30
It's probably because your firefox profile may be corrupt (using sudo uses root's profile instead). To erase your profile (or you can just rename it to test if this is the reason) so you can start with a new one, go to your home folder, click View -> Show Hidden Files, and erase the ".firefox" folder. Then try to start up Firefox.

If that's not it, then maybe something about the actual firefox install is borked. Easiest way to fix that would be to mark the firefox package for reinstallation in synaptic.

---

### Post by umechanism on 2009-03-31
> **kanikilu said:**
> Judging by the contents of that directory, it seems like firefox has been updated. Did you update to 3.0.8? If so, check the permissions on that directory as well.


I get a much different result when running the same command for 3.0.8:
```
 ls -l /usr/lib/firefox-3.0.8
total 104
lrwxrwxrwx 1 root root     7 2009-03-28 09:14 abrowser -> firefox
lrwxrwxrwx 1 root root     7 2009-03-28 09:14 abrowser-3.0 -> firefox
-rw-r--r-- 1 root root  2025 2009-03-27 07:42 application.ini
-rw-r--r-- 1 root root  1953 2009-03-27 07:40 blocklist.xml
-rw-r--r-- 1 root root    49 2009-03-27 07:40 browserconfig.properties
drwxr-xr-x 3 root root  4096 2009-03-28 09:14 chrome
drwxr-xr-x 2 root root  4096 2009-03-30 23:06 components
drwxr-xr-x 3 root root  4096 2009-03-28 09:14 defaults
lrwxrwxrwx 1 root root    25 2009-03-28 09:14 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x 2 root root  4096 2009-03-28 09:14 distribution
lrwxrwxrwx 1 root root    28 2009-03-28 09:14 extensions -> ../firefox-addons/extensions
-rwxr-xr-x 1 root root  9644 2009-03-27 07:42 ffox-3-beta-profile-migration-dialog
-rwxr-xr-x 1 root root 30232 2009-03-27 07:42 firefox
lrwxrwxrwx 1 root root     7 2009-03-28 09:14 firefox-3.0 -> firefox
-rw-r--r-- 1 root root   456 2009-03-27 07:39 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x 1 root root  4005 2009-03-27 07:40 firefox.sh
drwxr-xr-x 2 root root  4096 2009-03-28 09:14 icons
drwxr-xr-x 2 root root  4096 2009-03-28 09:14 modules
lrwxrwxrwx 1 root root    25 2009-03-28 09:14 plugins -> ../firefox-addons/plugins
-rwxr-xr-x 1 root root 11410 2009-03-27 07:40 run-mozilla.sh
lrwxrwxrwx 1 root root    31 2009-03-28 09:14 searchplugins -> ../firefox-addons/searchplugins
drwxr-xr-x 3 root root  4096 2009-03-30 21:06 updates

```
Does all of this look correct?  Could someone post their output for comparison?
Thanks for the help!

---

### Post by umechanism on 2009-03-31
> **tinivole said:**
> 
Also, check what, and how many processes are running on your machine.
**System->Administration->System Monitor**

If there are any Sleeping or Zombie firefox processes, kill them. If you see a high CPU usage app, or a high Memory usage app. Post their process names here, and we'll delegate whether or not they should be temporarily killed.

Regards
Iain
I checked and I do not see any Firefox or Mozilla processes running.  Not any.  Not even for the instance of Firefox that I am using now.  See attached photo which shows the process sorted in ABC order.

---

### Post by paradigm2 on 2009-04-01
> **umechanism said:**
> I get a much different result when running the same command for 3.0.8:
```
 ls -l /usr/lib/firefox-3.0.8
total 104
lrwxrwxrwx 1 root root     7 2009-03-28 09:14 abrowser -> firefox
lrwxrwxrwx 1 root root     7 2009-03-28 09:14 abrowser-3.0 -> firefox
-rw-r--r-- 1 root root  2025 2009-03-27 07:42 application.ini
-rw-r--r-- 1 root root  1953 2009-03-27 07:40 blocklist.xml
-rw-r--r-- 1 root root    49 2009-03-27 07:40 browserconfig.properties
drwxr-xr-x 3 root root  4096 2009-03-28 09:14 chrome
drwxr-xr-x 2 root root  4096 2009-03-30 23:06 components
drwxr-xr-x 3 root root  4096 2009-03-28 09:14 defaults
lrwxrwxrwx 1 root root    25 2009-03-28 09:14 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x 2 root root  4096 2009-03-28 09:14 distribution
lrwxrwxrwx 1 root root    28 2009-03-28 09:14 extensions -> ../firefox-addons/extensions
-rwxr-xr-x 1 root root  9644 2009-03-27 07:42 ffox-3-beta-profile-migration-dialog
-rwxr-xr-x 1 root root 30232 2009-03-27 07:42 firefox
lrwxrwxrwx 1 root root     7 2009-03-28 09:14 firefox-3.0 -> firefox
-rw-r--r-- 1 root root   456 2009-03-27 07:39 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x 1 root root  4005 2009-03-27 07:40 firefox.sh
drwxr-xr-x 2 root root  4096 2009-03-28 09:14 icons
drwxr-xr-x 2 root root  4096 2009-03-28 09:14 modules
lrwxrwxrwx 1 root root    25 2009-03-28 09:14 plugins -> ../firefox-addons/plugins
-rwxr-xr-x 1 root root 11410 2009-03-27 07:40 run-mozilla.sh
lrwxrwxrwx 1 root root    31 2009-03-28 09:14 searchplugins -> ../firefox-addons/searchplugins
drwxr-xr-x 3 root root  4096 2009-03-30 21:06 updates

```
Does all of this look correct?  Could someone post their output for comparison?
Thanks for the help!

Looks like what I have as well:

```

name@name-desktop:~$ ls -l /usr/lib/firefox-3.0.8
total 100
lrwxrwxrwx 1 root root     7 2009-03-31 12:04 abrowser -> firefox
lrwxrwxrwx 1 root root     7 2009-03-31 12:04 abrowser-3.0 -> firefox
-rw-r--r-- 1 root root  2025 2009-03-27 09:28 application.ini
-rw-r--r-- 1 root root  1953 2009-03-27 09:26 blocklist.xml
-rw-r--r-- 1 root root    49 2009-03-27 09:26 browserconfig.properties
drwxr-xr-x 3 root root  4096 2009-03-31 12:04 chrome
drwxr-xr-x 2 root root  4096 2009-03-31 12:04 components
drwxr-xr-x 3 root root  4096 2009-03-31 12:04 defaults
lrwxrwxrwx 1 root root    25 2009-03-31 12:04 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x 2 root root  4096 2009-03-31 12:04 distribution
lrwxrwxrwx 1 root root    28 2009-03-31 12:04 extensions -> ../firefox-addons/extensions
-rwxr-xr-x 1 root root  9644 2009-03-27 09:28 ffox-3-beta-profile-migration-dialog
-rwxr-xr-x 1 root root 30232 2009-03-27 09:28 firefox
lrwxrwxrwx 1 root root     7 2009-03-31 12:04 firefox-3.0 -> firefox
-rw-r--r-- 1 root root   456 2009-03-27 09:25 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x 1 root root  4005 2009-03-27 09:25 firefox.sh
drwxr-xr-x 2 root root  4096 2009-03-31 12:04 icons
drwxr-xr-x 2 root root  4096 2009-03-31 12:04 modules
lrwxrwxrwx 1 root root    25 2009-03-31 12:04 plugins -> ../firefox-addons/plugins
-rwxr-xr-x 1 root root 11410 2009-03-27 09:26 run-mozilla.sh
lrwxrwxrwx 1 root root    31 2009-03-31 12:04 searchplugins -> ../firefox-addons/searchplugins
name@name-desktop:~$

```

I'm guessing it has to do with a bad profile as already suggested.  I would use Synaptic and mark it for a "complete uninstallation", then manually delete your user profile in your home directory.  Then for good measure reboot and reinstall it.  It should work.

---

### Post by umechanism on 2009-04-02
That worked!  I uninstalled FF and deleted my profile.  Rebooted.  Then reinstalled FF.  Now it is back to normal.  Thanks for the help!

---

