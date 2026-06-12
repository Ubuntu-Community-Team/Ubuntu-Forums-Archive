---
title: "[SOLVED] firefox only starts with sudo &lt;searched&gt;"
date: 2009-06-04
forum: General Help
---

### Post by CapnBoost on 2009-06-04
So I recently partitioned my drive and freshly installed ubuntu 9.04 and winxp pro.

For a day it was perfect, 

Then my firefox started having issues with javascript in speed-dial, so I tried to fix that ultimately executing a command that reset my firefox (somehow?) and stopped me from starting it via the shortcut in the panel.  So I went to terminal and sudo firefox.  Brand spanking new firefox, so I reloaded all of my addons via FEBE on my shared partition and started to try to figure out why I can only open with sudo.  I've tried permissions with chmod, permissions in sudo nautilus, etc.

Have some code:
```
capn@capn-lappy:~$ which firefox
/usr/bin/firefox
capn@capn-lappy:~$ ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 11 2009-06-03 08:09 /usr/bin/firefox -> firefox-3.0
```

When I navigate to /usr/bin/firefox I get a script that directs me to /usr/lib/firefox-3.0.10/firefox-3.0 so I go there, double click that script and firefox starts.  So I relink the short cut in panel to this script (like I would in windows).

click- nothing.  Figures- I was in sudo nautilus when I clicked and it came up.  So, I ls -al the directory to see what permissions are:

```
capn@capn-lappy:~$ ls -al /usr/lib/firefox-3.0.10
total 172
drwxr-xr-x   9 root users  4096 2009-06-04 01:01 .
drwxr-xr-x 184 root root  61440 2009-06-03 21:21 ..
lrwxrwxrwx   1 root root      7 2009-06-03 08:09 abrowser -> firefox
lrwxrwxrwx   1 root root      7 2009-06-03 08:09 abrowser-3.0 -> firefox
-rw-r--r--   1 root root   2026 2009-04-25 18:36 application.ini
-rw-r--r--   1 root root      0 2009-06-03 08:09 .autoreg
-rw-r--r--   1 root root   2067 2009-04-25 18:34 blocklist.xml
-rw-r--r--   1 root root     49 2009-04-25 18:34 browserconfig.properties
drwxr-xr-x   3 root root   4096 2009-06-03 08:09 chrome
drwxr-xr-x   2 root root   4096 2009-06-04 00:19 components
drwxr-xr-x   3 root root   4096 2009-06-03 08:09 defaults
lrwxrwxrwx   1 root root     25 2009-06-03 08:09 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x   2 root root   4096 2009-06-03 08:09 distribution
lrwxrwxrwx   1 root root     28 2009-06-03 08:09 extensions -> ../firefox-addons/extensions
-rwxr-xr-x   1 root root   9644 2009-04-25 18:36 ffox-3-beta-profile-migration-dialog
-rwxrwxrwx   1 root users 30232 2009-04-25 18:36 firefox
lrwxrwxrwx   1 root root      7 2009-06-03 08:09 firefox-3.0 -> firefox
-rw-r--r--   1 root root    456 2009-04-25 18:33 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x   1 root users  4006 2009-04-25 18:33 firefox.sh
drwxr-xr-x   2 root root   4096 2009-06-03 08:09 icons
drwxr-xr-x   2 root root   4096 2009-06-03 08:09 modules
lrwxrwxrwx   1 root root     25 2009-06-03 08:09 plugins -> ../firefox-addons/plugins
-rwxr-xr-x   1 root root  11410 2009-04-25 18:34 run-mozilla.sh
lrwxrwxrwx   1 root root     31 2009-06-03 08:09 searchplugins -> ../firefox-addons/searchplugins
drwxr-xr-x   3 root root   4096 2009-06-02 23:51 updates
```

It appears that the permissions on those files (the executable ones anyway) are just fine too.  I've also tried [this]("https://answers.launchpad.net/ubuntu/+source/firefox/+question/62652").  Does anyone else have ideas?

---

### Post by CapnBoost on 2009-06-09
bump?

---

### Post by Legace on 2009-06-09
Type in **firefox** in Terminal. Does it work?

If not, try to rename **~/.mozilla** to something like ~/.mozillaold and try starting Firefox with the **firefox** command.

---

### Post by Soul-Sing on 2009-06-09
if root is "master" of your mozilla profile...

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```

---

### Post by aysiu on 2009-06-09
> **leoquant said:**
> if root is "master" of your mozilla profile...

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```
And once you've done that, **never** run the command *sudo firefox* again. That was probably what changed ownership to root in the first place.

If you must run Firefox as root again, use the command ```
gksudo firefox
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by CapnBoost on 2009-06-10
> **leoquant said:**
> if root is "master" of your mozilla profile...

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```

I believe this solved the problem.  Thank you.

> **aysiu said:**
> And once you've done that, **never** run the command *sudo firefox* again. That was probably what changed ownership to root in the first place.

If you must run Firefox as root again, use the command ```
gksudo firefox
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I will keep that in mind, thanks for the pointer.

---

### Post by l-x-l on 2009-06-10
Yes.. running "sudo firefox" caused me all types of problems, including a corrupt profile, broken bookmarks, etc. When trouble-shooting I read that is a common problem. I suggest never running it.

---

### Post by Soul-Sing on 2009-06-10
> **l-x-l said:**
> Yes.. running "sudo firefox" caused me all types of problems, including a corrupt profile, broken bookmarks, etc. When trouble-shooting I read that is a common problem. I suggest never running it.

never +1 (or never again :))

---

