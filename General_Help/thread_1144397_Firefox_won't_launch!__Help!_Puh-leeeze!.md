---
title: "Firefox won't launch!  Help! Puh-leeeze!"
date: 2009-04-30
forum: General Help
---

### Post by quixote on 2009-04-30
I get this error message: "Could not launch menu item.  Failed to execute child process "firefox" (Permission denied)."  I've tried purging and reinstalling.  I've tried installing just as a user and running by clicking on it in nautilus from my home directory.  It just doesn't start.  I've tried starting it at the command line, then it tells me "firefox is not currently installed.  You can install it by typing sudo apt-get install firefox-3.0".  

Except I can't.  Nothing helps.  Doing "sudo apt-get install --reinstall firefox" and rebooting, STILL gives me the same messages.

What brought it all on, as far as I can tell, is this:  I had an installed-as-user version of 3.1b3 in my home directory which wasn't working.  I'd installed it by unpacking a .tar.bz2, so I just deleted the directory.

And that's when the problem started.  The regular, system-standard 3.0.10 gave me that error message, and won't stop.  It shouldn't have had anything to do with what I had in my home firefox directory!

So now what??   Life stops without the web!  I hope someone can help!

---

### Post by codeseer on 2009-04-30
Rename /home/username/.mozilla and try again.

Edit:

Run this, post results:

```

ls -al /usr/bin/fire*

ls -al /usr/lib/firefox-3.0.10/fire*

```

Do you have an AppArmor profile for Firefox?

---

### Post by quixote on 2009-04-30
renaming ~/ .mozilla didn't change the error message.

One thing I noticed: gconf-editor doesn't have anything under "apps" for either "browser" or "firefox"  Maybe it never does?  I haven't checked before.  Under desktop > gnome > applications > browser it's pointing to my ~/firefox directory, which is the thing I deleted when all the trouble began.  I've since put another user-installed FF in that same place, but no change to the messages.

(I've also installed a 3.5b4 because I'm kinda flailing around :oops: .  (After I tried the rename above.)  But it just loads and crashes, even in safe mode with a new profile, so there's some other problems there. :rolleyes: )

output of  ls -al /usr/bin/fire*

```
 lrwxrwxrwx  1 root root      32 2009-04-30 15:07 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.10/firefox.sh
lrwxrwxrwx  1 root root      34 2009-04-30 15:28 /usr/bin/firefox-3.5 -> ../lib/firefox-3.5b4pre/firefox.sh
-rw-r--r--  1 root root 9811581 2009-04-30 14:36 /usr/bin/firefox-3.5b4.tar.bz2

/usr/bin/firefox:
total 17812
drwxr-xr-x 13 root root     4096 2009-04-23 20:09 .
drwxr-xr-x  3 root root    36864 2009-04-30 15:28 ..
-rw-r--r--  1 root root     2126 2009-04-23 20:08 application.ini
-rw-r--r--  1 root root        0 2009-04-23 20:08 .autoreg
-rw-r--r--  1 root root     2067 2009-04-23 20:08 blocklist.xml
-rw-r--r--  1 root root      232 2009-04-23 20:08 browserconfig.properties
drwxr-xr-x  3 root root     4096 2009-04-23 20:08 chrome
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 components
-rwxr-xr-x  1 root root    45760 2009-04-23 20:09 crashreporter
-rw-r--r--  1 root root     3801 2009-04-23 20:08 crashreporter.ini
-rw-r--r--  1 root root      583 2009-04-23 20:08 crashreporter-override.ini
drwxr-xr-x  5 root root     4096 2009-04-23 20:08 defaults
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 dictionaries
drwxr-xr-x  3 root root     4096 2009-04-23 20:08 extensions
-rwxr-xr-x  1 root root     3883 2009-04-23 20:08 firefox
-rwxr-xr-x  1 root root    58052 2009-04-23 20:09 firefox-bin
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 greprefs
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 icons
-rw-r--r--  1 root root      478 2009-04-23 20:09 libfreebl3.chk
-rwxr-xr-x  1 root root   317036 2009-04-23 20:09 libfreebl3.so
-rwxr-xr-x  1 root root   823500 2009-04-23 20:09 libmozjs.so
-rwxr-xr-x  1 root root   200736 2009-04-23 20:08 libnspr4.so
-rwxr-xr-x  1 root root   858792 2009-04-23 20:08 libnss3.so
-rwxr-xr-x  1 root root   313676 2009-04-23 20:08 libnssckbi.so
-rwxr-xr-x  1 root root   122896 2009-04-23 20:08 libnssdbm3.so
-rwxr-xr-x  1 root root    77608 2009-04-23 20:08 libnssutil3.so
-rwxr-xr-x  1 root root    13180 2009-04-23 20:09 libplc4.so
-rwxr-xr-x  1 root root     8748 2009-04-23 20:08 libplds4.so
-rwxr-xr-x  1 root root   125644 2009-04-23 20:09 libsmime3.so
-rw-r--r--  1 root root      478 2009-04-23 20:09 libsoftokn3.chk
-rwxr-xr-x  1 root root   190032 2009-04-23 20:08 libsoftokn3.so
-rwxr-xr-x  1 root root   442840 2009-04-23 20:08 libsqlite3.so
-rwxr-xr-x  1 root root   160140 2009-04-23 20:08 libssl3.so
-rwxr-xr-x  1 root root    11824 2009-04-23 20:08 libxpcom.so
-rwxr-xr-x  1 root root 14095832 2009-04-23 20:09 libxul.so
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 modules
-rwxr-xr-x  1 root root    10804 2009-04-23 20:09 mozilla-xremote-client
-rw-r--r--  1 root root      112 2009-04-23 20:08 old-homepage-default.properties
-rw-r--r--  1 root root      136 2009-04-23 20:08 platform.ini
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 plugins
-rw-r--r--  1 root root      177 2009-04-23 20:08 README.txt
-rw-r--r--  1 root root    15861 2009-04-23 20:08 removed-files
drwxr-xr-x  6 root root     4096 2009-04-23 20:08 res
-rwxr-xr-x  1 root root    10450 2009-04-23 20:08 run-mozilla.sh
drwxr-xr-x  2 root root     4096 2009-04-23 20:08 searchplugins
-rw-r--r--  1 root root      825 2009-04-23 20:08 Throbber-small.gif
-rwxr-xr-x  1 root root    70472 2009-04-23 20:08 updater
-rw-r--r--  1 root root      299 2009-04-23 20:08 updater.ini 
```


and output of ls -al /usr/lib/firefox-3.0.10/fire*

```
-rwxr-xr-x 1 root root 39376 2009-04-25 16:35 /usr/lib/firefox-3.0.10/firefox
lrwxrwxrwx 1 root root     7 2009-04-30 15:07 /usr/lib/firefox-3.0.10/firefox-3.0 -> firefox
-rw-r--r-- 1 root root   456 2009-04-25 16:34 /usr/lib/firefox-3.0.10/firefox-3.0-restart-required.update-notifier
-rwxr-xr-x 1 root root  4006 2009-04-25 16:34 /usr/lib/firefox-3.0.10/firefox.sh  
```

I've messed something up big time, but I don't understand why reinstalling doesn't do the trick!  Thanks for your superfast reply!

---

### Post by codeseer on 2009-04-30
You're missing your main firefox link in /usr/bin. It should be like so:

```
lrwxrwxrwx 1 root root 11 2009-04-29 10:42 /usr/bin/firefox -> firefox-3.0
```

What happens when you type firefox-3.0 in the terminal?

---

### Post by quixote on 2009-05-01
> You're missing your main firefox link in /usr/bin
Gaaa! The obvious thing I didn't think to look at.  

When I typed "firefox" in a terminal, nothing happened, even when I was in the directory with one of my new Firefoxes.  Now that the link points from /usr/bin to an actual installed firefox, it works.  Surprising, I know.  :lolflag:

---

### Post by howardf42 on 2009-05-04
I don't mean to hijack this thread, but I think the original poster has solved his problem.  Mine is similar, but I haven't been successful so I hope someone can help me.

I have been getting the Firefox process running error since I upgraded to Ubuntu 9.04 yesterday. 

Here is the results  for "ls -al /usr/bin/fire*"

```
lrwxrwxrwx 1 root root 11 2009-05-04 14:44 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 32 2009-05-04 14:44 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.10/firefox.sh
```

The results for "ls -al /usr/lib/firefox-3.10/fire*"

```
ls: cannot access /usr/lib/firefox-3.10/fire*: No such file or directory
```

Running "ls -al /usr/lib/fire*" instead returns

```
/usr/lib/firefox:
total 80
drwxr-xr-x   3 root root  4096 2009-05-04 14:35 .
drwxr-xr-x 185 root root 69632 2009-05-04 14:44 ..
drwxr-xr-x   2 root root  4096 2009-05-04 14:35 plugins

/usr/lib/firefox-3.0.10:
total 176
drwxr-xr-x   8 root root  4096 2009-05-04 14:44 .
drwxr-xr-x 185 root root 69632 2009-05-04 14:44 ..
lrwxrwxrwx   1 root root     7 2009-05-04 14:44 abrowser -> firefox
lrwxrwxrwx   1 root root     7 2009-05-04 14:44 abrowser-3.0 -> firefox
-rw-r--r--   1 root root  2026 2009-04-25 18:36 application.ini
-rw-r--r--   1 root root     0 2009-05-04 14:44 .autoreg
-rw-r--r--   1 root root  2067 2009-04-25 18:34 blocklist.xml
-rw-r--r--   1 root root    49 2009-04-25 18:34 browserconfig.properties
drwxr-xr-x   3 root root  4096 2009-05-04 14:44 chrome
drwxr-xr-x   2 root root  4096 2009-05-04 14:44 components
drwxr-xr-x   3 root root  4096 2009-05-04 14:44 defaults
lrwxrwxrwx   1 root root    25 2009-05-04 14:44 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x   2 root root  4096 2009-05-04 14:44 distribution
lrwxrwxrwx   1 root root    28 2009-05-04 14:44 extensions -> ../firefox-addons/extensions
-rwxr-xr-x   1 root root  9644 2009-04-25 18:36 ffox-3-beta-profile-migration-dialog
-rwxr-xr-x   1 root root 30232 2009-04-25 18:36 firefox
lrwxrwxrwx   1 root root     7 2009-05-04 14:44 firefox-3.0 -> firefox
-rw-r--r--   1 root root   456 2009-04-25 18:33 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x   1 root root  4006 2009-04-25 18:33 firefox.sh
drwxr-xr-x   2 root root  4096 2009-05-04 14:44 icons
drwxr-xr-x   2 root root  4096 2009-05-04 14:44 modules
lrwxrwxrwx   1 root root    25 2009-05-04 14:44 plugins -> ../firefox-addons/plugins
-rwxr-xr-x   1 root root 11410 2009-04-25 18:34 run-mozilla.sh
lrwxrwxrwx   1 root root    31 2009-05-04 14:44 searchplugins -> ../firefox-addons/searchplugins

/usr/lib/firefox-addons:
total 88
drwxr-xr-x   5 root root  4096 2009-05-04 14:44 .
drwxr-xr-x 185 root root 69632 2009-05-04 14:44 ..
drwxr-xr-x   3 root root  4096 2009-05-04 11:33 extensions
drwxr-xr-x   2 root root  4096 2009-04-25 18:34 plugins
drwxr-xr-x   2 root root  4096 2009-05-04 14:44 searchplugins
howard@howard-laptop:~$ ls -al /usr/bin/fire*
lrwxrwxrwx 1 root root 11 2009-05-04 14:44 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 32 2009-05-04 14:44 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.10/firefox.sh
```

Running "firefox-3.0" returns

```
(firefox:26385): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(firefox:26385): atk-bridge-WARNING **: IOR not set.

(firefox:26385): atk-bridge-WARNING **: Could not locate registry

(firefox:26385): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(firefox:26385): atk-bridge-WARNING **: IOR not set.

(firefox:26385): atk-bridge-WARNING **: Could not locate registry
```

Any and all help is welcome.

Howard

---

### Post by codeseer on 2009-05-04
Try:

```

gconftool-2 -s --type=bool /desktop/gnome/interface/accessibility false 

```

---

### Post by howardf42 on 2009-05-04
> **codeseer said:**
> Try:

```

gconftool-2 -s --type=bool /desktop/gnome/interface/accessibility false 

```

Sorry, no joy.  What was that supposed to do?

---

### Post by codeseer on 2009-05-04
> **howardf42 said:**
> Sorry, no joy.  What was that supposed to do?

It was a shot at fixing the issue, from my experiences with past occurrences of this error message.

Go ahead and rename the ~/.mozilla directory and see if that fixes the issue. If it does, then we can narrow it down to a configuration issue.

Edit:

If that doesn't work, put it back and try running firefox with 'sudo' (as root), just for testing only.

---

### Post by howardf42 on 2009-05-04
> **codeseer said:**
> It was a shot at fixing the issue, from my experiences with past occurrences of this error message.

Go ahead and rename the ~/.mozilla directory and see if that fixes the issue. If it does, then we can narrow it down to a configuration issue.

Edit:

If that doesn't work, put it back and try running firefox with 'sudo' (as root), just for testing only.

Hey, the rename worked.  What does that mean and what else do I need to do?

---

### Post by codeseer on 2009-05-04
> **howardf42 said:**
> Hey, the rename worked.  What does that mean and what else do I need to do?

It means there was a corruption in your firefox configuration somewhere. I recommend just transitioning your bookmarks from the old configuration to the new configuration and using the newly created .mozilla directory. You may have to reinstall some of your plugins, but it's easier than trying to find out exactly where the corruption is.

Let me know if you need any plugin help.

---

### Post by howardf42 on 2009-05-04
> **codeseer said:**
> It means there was a corruption in your firefox configuration somewhere. I recommend just transitioning your bookmarks from the old configuration to the new configuration and using the newly created .mozilla directory. You may have to reinstall some of your plugins, but it's easier than trying to find out exactly where the corruption is.

Let me know if you need any plugin help.

I had been using a profile that is stored in a path accessible to both Ubuntu and Windows.  Should I give that up?  I don't go back to Winblows very often now so it wouldn't be a great loss.

Thanks for all your help.

---

### Post by codeseer on 2009-05-04
> **howardf42 said:**
> I had been using a profile that is stored in a path accessible to both Ubuntu and Windows.  Should I give that up?  I don't go back to Winblows very often now so it wouldn't be a great loss.

Thanks for all your help.

Well if the use of that profile doesn't result in the error, then you could just copy it over to the new .mozilla directory. Sharing of profiles between operating systems can cause some problems though.

---

### Post by howardf42 on 2009-05-04
> **codeseer said:**
> Well if the use of that profile doesn't result in the error, then you could just copy it over to the new .mozilla directory. Sharing of profiles between operating systems can cause some problems though.

I restored the old profile from the shared folder and all seems well.  I've been using this setup for the last 2 years without a problem.  I guess something in the 9.04 install made it break.  Thanks again for your help.

---

### Post by quixote on 2009-05-05
Actually, after the fix, I started having some weird instability problems after a while.  That is, firefox would crash for no apparent reason.  I'll try the .mozilla rename too.  Configuration issues sounds very plausible.  I had a rather wild and woolly set of extensions in the good old days.

---

