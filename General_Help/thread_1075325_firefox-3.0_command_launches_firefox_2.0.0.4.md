---
title: "firefox-3.0 command launches firefox 2.0.0.4"
date: 2009-02-20
forum: General Help
---

### Post by janne_oksanen on 2009-02-20
I rebooted my computer last night and since then I've been unable to launch ff3. Running command "firefox-3.0" gives me ff2 every time. I've tried removing ff2 and deleting my profile, but nothing seems to work. Additionally I checked my path and everything seems to be in order.

```

janne@Dominator:~$ which firefox-3.0 
/usr/bin/firefox-3.0
janne@Dominator:~$ ls -l /usr/bin/firefox-3.0
lrwxrwxrwx 1 root root 31 2009-02-11 10:46 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.6/firefox.sh

```

Any ideas?

Thanks in advance.

---

### Post by Dave_Connor on 2009-02-20
```
 sudo apt-get autoclean && sudo apt-get autoremove 
```
Might get rid of ff2 and just have Firefox 3 on your system.

---

### Post by janne_oksanen on 2009-02-20
I just tried that and it didn't do the trick.

---

### Post by taurus on 2009-02-20
What happens if you run it with

```
/usr/lib/firefox-3.0.6/firefox.sh
```

---

### Post by janne_oksanen on 2009-02-20
100% CPU load happens and not really anything else. I waited for a few minutes before killing it, but I got nothing, not even ff2.

---

### Post by taurus on 2009-02-20
What's the output of this command?

```
ls -la /usr/lib/firefox-3.0.6
```

---

### Post by janne_oksanen on 2009-02-20
```
janne@Dominator:~$ ls -la /usr/lib/firefox-3.0.6
yhteensä 192
drwxr-xr-x   8 root root  4096 2009-02-11 10:46 .
drwxr-xr-x 282 root root 86016 2009-02-20 10:48 ..
lrwxrwxrwx   1 root root     7 2009-02-11 10:46 abrowser -> firefox
lrwxrwxrwx   1 root root     7 2009-02-11 10:46 abrowser-3.0 -> firefox
-rw-r--r--   1 root root  2025 2009-02-09 13:23 application.ini
-rw-r--r--   1 root root     0 2009-02-11 10:47 .autoreg
-rw-r--r--   1 root root  1953 2009-02-09 13:22 blocklist.xml
-rw-r--r--   1 root root    49 2009-02-09 13:22 browserconfig.properties
drwxr-xr-x   3 root root  4096 2009-02-11 10:46 chrome
drwxr-xr-x   2 root root  4096 2009-02-11 10:46 components
drwxr-xr-x   3 root root  4096 2009-02-11 10:46 defaults
lrwxrwxrwx   1 root root    25 2009-02-11 10:46 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x   2 root root  4096 2009-02-11 10:46 distribution
lrwxrwxrwx   1 root root    28 2009-02-11 10:46 extensions -> ../firefox-addons/extensions
-rwxr-xr-x   1 root root  9544 2009-02-09 13:23 ffox-3-beta-profile-migration-dialog
-rwxr-xr-x   1 root root 30164 2009-02-09 13:23 firefox
lrwxrwxrwx   1 root root     7 2009-02-11 10:46 firefox-3.0 -> firefox
-rw-r--r--   1 root root   456 2009-02-09 13:21 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x   1 root root  4005 2009-02-09 13:21 firefox.sh
drwxr-xr-x   2 root root  4096 2009-02-11 10:46 icons
drwxr-xr-x   2 root root  4096 2009-02-11 10:46 modules
lrwxrwxrwx   1 root root    25 2009-02-11 10:46 plugins -> ../firefox-addons/plugins
-rwxr-xr-x   1 root root 11410 2009-02-09 13:22 run-mozilla.sh
lrwxrwxrwx   1 root root    31 2009-02-11 10:46 searchplugins -> ../firefox-addons/searchplugins
janne@Dominator:~$ 

```

But it doesn't matter anymore. 'sudo aptitude reinstall firefox' fixed the problem.

---

