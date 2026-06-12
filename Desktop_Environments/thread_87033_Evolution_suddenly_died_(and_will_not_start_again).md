---
title: "Evolution suddenly died (and will not start again)"
date: 2005-11-07
forum: Desktop Environments
---

### Post by HanZo on 2005-11-07
I have a strange problem with evolution, I did a new install of breezy on my HP-compaq nx7000 laptop and for some time everything worked fine, then, suddenly evolution just stopped working. It began with a sudden crash, I force quit the program, but now when I try to open it it just freezes and I have to force quit again.

this is the console output:
```
adding hook target 'source'

(evolution:10324): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:10324): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

```
unfortunately I am a bit of a linux newby so I don't really know what all of this means.

Usually evolution crashes when showing "fetching mail" in the staus bar.
but starting with evolution --offline did not change anything.
tried to reinstall but this did not solve the problem... dunno what to do...
I think I will go back to thunderbird (at least junk mail filtering works) but I'd really hate to loose my adresses and emails...

thanks in advance for any help!

edit: tried to run it as root... started properly... so I think it's a database problem (or whatever evolution uses to keep track of all the data)

---

### Post by 23meg on 2005-11-07
Try backing up and deleting everything in your ~/.evolution directory and creating a new user and see if it helps with crashes. If it does, try importing mailbox files from the old profile one by one.

---

### Post by HanZo on 2005-11-08
thanks, I'll try it... now I'm back with thunderbird and I think I will not use evil-ution anymore... I always thought spam would not get filtered because spammers got too clever... but now I know it's just evolution that's crap... thnuderbird did not miss one spam-mailin the last 4 days... I will miss some features of evolution... but afer all thunderbird is much better in a lot of things.

---

### Post by JeffreyRatcliffe on 2005-12-07
[QUOTE=HanZo]I have a strange problem with evolution, I did a new install of breezy on my HP-compaq nx7000 laptop and for some time everything worked fine, then, suddenly evolution just stopped working. It began with a sudden crash, I force quit the program, but now when I try to open it it just freezes and I have to force quit again.

this is the console output:
```
adding hook target 'source'

(evolution:10324): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:10324): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

```
[/QUOTE]

I just had this exact problem. I solved it (complete guesswork) by starting with --force-shutdown. Evolution reported shutting down the alarm notifier.

I was then able to start evolution normally and I haven't had the problem since.

Jeff

---

### Post by electedfreedumb on 2008-01-15
I had this same issue in the past on fiesty. I had to uninstall and then install evolution again. Now on Gutsy after a week and a half it is doing it again. I tried force shutdown and it does say:

Shutting down evolution-data-server-1.12 (Evolution Calendar file and webcal backend / Evolution Addressbook file backend)
Shutting down evolution-alarm-notify (Evolution Calendar alarm notification service)

However when I try to start the app again it loads up then just shuts back down. I really don't want to loose all my settings, contacts and calenders I have set-up in evolution? 

Any Ideas would be very helpful and appreciated.

---

### Post by electedfreedumb on 2008-01-15
heres what I get when I try to start it

CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:8219): DEBUG: mailto URL command: evolution %s
** (evolution:8219): DEBUG: mailto URL program: evolution
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
Segmentation fault (core dumped)

Then it starts to connect to Gmail to get IMAP mail then just closes right away.

This is after sudo apt-get remove evolution and then sudo apt-get install evolution also. 

Any help would be great.

---

### Post by electedfreedumb on 2008-01-15
Tried this and it worked. At least it is open now. Retained all accounts and web calenders etc. Not sure what might be missing. 


 If you don't care too much about your configurations you can delete the config directory

#rm -rf .evolution

Worked for me, All accounts still working, all mails kept etc... Only thing I can see missing is the plugins (which were causing Ev to crash)
__________________

[http://ubuntuforums.org/showthread.php?t=508158](http://ubuntuforums.org/showthread.php?t=508158)

---

### Post by ARlyLngUsrNameJustBecause on 2008-01-27
I had a similar problem here is my experience. evolution crashed on me out of the blue and would not start up. running evolution from the console produced this error msg:

```
 LDAP authentication failed (0x51)
evolution-shell-Message: Killing old version of evolution-data-server...
RSS Plugin enabled

(evolution:7729): GLib-CRITICAL **: g_strchug: assertion `string != NULL' failed

(evolution:7729): GLib-CRITICAL **: g_strchomp: assertion `string != NULL' failed

(evolution:7729): GLib-CRITICAL **: g_strchug: assertion `string != NULL' failed

(evolution:7729): GLib-CRITICAL **: g_strchomp: assertion `string != NULL' failed

(evolution:7729): GLib-CRITICAL **: g_strchug: assertion `string != NULL' failed

(evolution:7729): GLib-CRITICAL **: g_strchomp: assertion `string != NULL' failed
Segmentation fault (core dumped)

```

Deleting or renaming the file ~/.evolution/mail/rss/evoltuion-feeds  removes my feeds from the plugin but lets evolution start up w/o causing a seg fault. 

Anyway I hope thats some help.

---

### Post by Lars Skovbo on 2008-03-06
I just solved this problem by removing the .evolution folder from my home. This worked, and the pop/smtp setup was intact, so thats nice.
I also had a segmentation fault (illegal memory access).

---

