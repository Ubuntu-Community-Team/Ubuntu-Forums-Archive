---
title: "Evolution Error messages"
date: 2008-01-10
forum: Desktop Environments
---

### Post by billo38 on 2008-01-10
My installation was working just fine until about 1 week ago.  I believe that my troubles started after downloading and installing several patches, although I cannot pinpoint the offender.  I receive the following error messages each time my system chaecks for new mail: "Error while storing folder 'inbox'  Summary and folder mismatch even after a sync" - I also receive an additional error message: "Error while fetching Mail" folloowed by the same "Summary" message as above.  One of the problems that occurs is that messages that have been downloaded are not removed from my mail server, so I get the same messages over and over.  I have not marked any options that indicate messages should be retained on the server.  I appreciate any help.

---

### Post by metalheart on 2008-01-10
Start Evolution with

```
evolution --offline
```

to give it time to index the message store. Then receive new messages.

---

### Post by billo38 on 2008-01-10
Followed your suggestion - start evolution as "evolution --offline" - received the following response:

bill@bill-desktop:~$ evolution --offline
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:7576): DEBUG: mailto URL command: evolution %s
** (evolution:7576): DEBUG: mailto URL program: evolution

(evolution:7576): camel-WARNING **: Could not find key entry for word 'znaglqa2xtbm9ic3r1dnd4exp7fh': Success


(evolution:7576): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7576): camel-CRITICAL **: camel_index_add_name: assertion `CAMEL_IS_INDEX (idx)' failed

(evolution:7576): camel-local-provider-WARNING **: Didn't get the next message where I expected (13876336) got 29066097 instead
creating

(evolution:7576): camel-local-provider-WARNING **: Didn't get the next message where I expected (13876336) got 29066097 instead
fff

(evolution:7576): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
camel-Message: --

(evolution:7576): camel-local-provider-WARNING **: Didn't get the next message where I expected (13876336) got 29066097 instead

(evolution:7576): camel-local-provider-WARNING **: Didn't get the next message where I expected (13876336) got 29066097 instead

report junk?? Let us get you cash for your timeshare! Thu, 10 Jan 2008 21:28:26 -0200
camel-Message: --

(evolution:7576): camel-local-provider-WARNING **: Didn't get the next message where I expected (13876336) got 29066097 instead

(evolution:7576): camel-local-provider-WARNING **: Didn't get the next message where I expected (13876336) got 29066097 instead


billo38

---

### Post by billo38 on 2008-01-10
Metalheart,

Tried your suggestion a second time and received different responses from the system.  All seems to be OK now.  I appreciate your help.

billo38 :)

---

### Post by romunov on 2008-03-06
> evolution --offline worked for me!

---

