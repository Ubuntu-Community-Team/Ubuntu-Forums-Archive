---
title: "Evolution crash (after the next distro updating)"
date: 2006-08-01
forum: Desktop Environments
---

### Post by gray380 on 2006-08-01
Hi there!

After the next system updating I have the troubles with Evolution. When I try to start it the following messages has appeared:

> CalDAV Eplugin starting up ...

(evolution-2.6:5736): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:5736): e-utils-WARNING **: Plugin '&#1060;&#1110;&#1083;&#1100;&#1090;&#1088;&#1072;&#1094;&#1110;&#1103; &#1089;&#1087;&#1072;&#1084;&#1091; &#1095;&#1077;&#1088;&#1077;&#1079; Spamassassin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
cherpatyuk@Cherpatyuk:~$ CalDAV Eplugin starting up ...

(evolution-2.6:5781): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:5781): e-utils-WARNING **: Plugin '&#1060;&#1110;&#1083;&#1100;&#1090;&#1088;&#1072;&#1094;&#1110;&#1103; &#1089;&#1087;&#1072;&#1084;&#1091; &#1095;&#1077;&#1088;&#1077;&#1079; Spamassassin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:5781): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution-2.6:5781): Gtk-CRITICAL **: gtk_toggle_button_get_active: assertion `GTK_IS_TOGGLE_BUTTON (toggle_button)' failed

(evolution-2.6:5781): e-utils-WARNING **: Cannot resolve symbol 'org_gnome_new_mail_config' in plugin '/usr/lib/evolution/2.6/plugins/liborg-gnome-new-mail-notify.so' (not exported?)

When (after starting) I try to close the Evolution:

> BBDB spinning up...
bbdb: Buddy list has changed since last sync.
bbdb: Synchronizing buddy list to contacts...
bbdb: Done syncing buddy list to contacts.
bbdb: Buddy list has changed since last sync.
bbdb: Synchronizing buddy list to contacts...
bbdb: Done syncing buddy list to contacts.
bbdb: Buddy list has changed since last sync.
bbdb: Synchronizing buddy list to contacts...
bbdb: Done syncing buddy list to contacts.

endless process ;)

Before updating everything (allmost) was ok.

Could you, please, help me to solve this problem.

brg,
Serhiy.

---

### Post by gray380 on 2006-08-01
Hello,

the problem was solved by deleting/creating mail-account (ms exchange).

cu.

---

