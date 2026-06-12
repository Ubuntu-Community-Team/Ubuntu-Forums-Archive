---
title: "Evolution Memory Leak"
date: 2011-08-05
forum: Desktop Environments
---

### Post by clegends on 2011-08-05
Hi folks, am at my wits end with Evolution. Firstly, I'm looking at moving to Thunderbird (or moving back to Thunderbird I should say) when Oneiric hits stable, but until then I want to make Evolution work. I'm running it on 11.04 under Unity, with 6 imap accounts (2 from gmail) and 1 pop mail. I have just archived most of my messages so there is about 20 messages or less in each folder. Oh yeah... the archiving process was to manually create a folder under the local file tree in Evolution, named.. wait for it... "archives". There wasn't an automatic way to do this.

I've set the program to copy 4 of the above accounts locally for offline access... and after doing all of the above seem to have speed up evolution considerably... until it starts eating my system Ram. I'm running an eeepc 901 with 2 gb of ram, and within 20 minutes it seems to eat up around 700mb. What the heck is going on?

I also have 5 calendars in use on the local computer (all of them are measured in kb with size, I checked), 1 active web folder (hardly ever used, without much on it), and a couple of disabled google calendars (can't delete them, not sure why.

So does anyone have any ideas as to why evolution is eating so much memory? Currently, it means I need to close it every half hour or so. Cheers.

---

### Post by clegends on 2011-08-07
Bump. Come on folks, is anyone able to help with this? Evolution memory keeps skyrocketing, currently up to 219mb and climbing... time for another restart. Cheers.

---

### Post by pienkvien on 2011-08-07
I have several accounts and it stays around 60mb.

---

### Post by clegends on 2011-08-07
Hmmm. I wonder what's using it in my case. I have just set my phone to check emails every 5 minutes so I can shut down evolution.. surely there's a better solution than this...

Any ideas how to troubleshoot this, and are you using imap+, pop, or imap for your mail accounts? I recently uninstalled evolution (with apt-get purge) and restored it again from backed up settings... it seems likely that some of my settings are triggering a bug. Thanks for replying.

---

### Post by clegends on 2011-08-07
Just ran evolution with this command:
```
evolution --debug-file=evobugs
```
And got this output:
```

(evolution:2239): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:2239): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'

(firefox-bin:8739): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:9247): DEBUG: NP_Initialize
** (<unknown>:9247): DEBUG: NP_Initialize succeeded
** (<unknown>:9247): DEBUG: NP_Shutdown
NOTE: child process received `Goodbye', closing down
NOTE: child process received `Goodbye', closing down
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)

(firefox-bin:8739): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed

(firefox-bin:8739): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed
```

Anyone know what's going on here? I shut it down after reaching 385mb over about 90 minutes. Have filed a bug in launchpad, but am looking for a work around. Cheers.

---

