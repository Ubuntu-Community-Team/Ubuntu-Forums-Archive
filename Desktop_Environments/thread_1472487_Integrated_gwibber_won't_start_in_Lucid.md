---
title: "Integrated gwibber won't start in Lucid"
date: 2010-05-04
forum: Desktop Environments
---

### Post by qrwe on 2010-05-04
Hi!

I've just upgraded to Lucid Lynx on my Asus Eee Netbook, with Notebook Remix installed. I wqs glad to see that Canonical integrated the gwibber client into the desktop environment, as this gives me better opportunities to use my Twitter account properly. Unfortunately, i can't run "Set up broadcast account" when clicking the "letter-applet" icon. When running gwibber from terminal, I get this:

```

#/$ gwibber

** (gwibber:3611): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3611): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3611): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 50, in <module>
    from gwibber import client
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 3, in <module>
    import gtk, gobject, gwui, util, resources, actions, json, gconf
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 2, in <module>
    import os, json, urlparse, resources, util
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 2, in <module>
    from microblog.util.couch import RecordMonitor
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 10, in <module>
    OAUTH_DATA = desktopcouch.local_files.get_oauth_tokens()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 323, in get_oauth_tokens
    oauth_token_secrets = cf.items_in_section("oauth_token_secrets")[0]
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 189, in items_in_section
    raise ValueError("Section %r not present." % (section_name,))
ValueError: Section 'oauth_token_secrets' not present.

```

Has anyone of you who read this seen that before, or/and (even better) knows what to do? Please drop a post, it would really help me and hopefully somebody else who has the same problem.
Kind regards!

---

### Post by Sylvestra on 2010-05-04
I found this thread about 5 times now and as many or more bugs refering to the issue in launchpad. hope this patch is going to fix it:
[https://bugs.edge.launchpad.net/gwibber/+bug/523964](https://bugs.edge.launchpad.net/gwibber/+bug/523964)

---

### Post by magnus0 on 2010-05-04
You could just go to System - Preferences - Startup Applications and drag the Gwibber icon from Applications menu into this window.

---

### Post by jamoncillo on 2010-05-04
yeah, I think it's a common problem. Same thing happens to me, haven't figured out a way to fix it =/

waiting for a patch or something. And I think this just happens when upgrading, not when doing a clean install

---

### Post by TyroneSlothrop on 2010-05-05
I am having the exact problem as the parent poster on one of the computers I upgraded.  I have not gotten the problem solved, but I did create a dummy account and found that my new account - created after the upgrade - can launch Gwibber with no problem.  Following this logic, and trying to debug the errors on my own, I started looking at the logins stored in my keyring.  I noticed that the login section contained two Desktop Couch entries.  In an ill advised feeling of confidence, I deleted both of those keys, all to now avail.

Looking at other keyrings (other machines, other user accounts) and I am thinking that the keyring entries got corrupted or unexpectedly changed during the upgrade.  I am not familiar with how the desktop couch db works, but now I have two problems, the aforementioned gwibber issue, and now I need to figure out a way to generate those two login keys...

Anyone have any insight on the dektop couch db and how it interacts with the keyring, and if there is any hope for recovering/regenerating those logins?

---

### Post by TyroneSlothrop on 2010-05-05
An update:

I issued the command: killall beam
I then removed the couchdb initialization file: rm ~/.config/desktop-couch/desktop-couchdb.ini 
I then issued the following command: dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
I then issued the command: xdg-open file:///home/USERNAME/.local/share/desktop-couch/couchdb.html

I was then presented with the Couch DB debugger, Futon.  I was able to run the oauth, replication, security_validation, and conflicts under the Test Suite option.

After that, I could once again re-sync with Ubuntu One, I had entries for Desktop Couch in keyring.  I was not able to start Gwibber, but when I tried I got a new message about a client not being present, not the original error message.  I then was able to run Broadcast Preferences in Administration, and ticked the 'Start service at login', ran some updates, restarted, and gwibber is now running for me.

Not sure if what I did got it fixed, or if there was a fix in the updates, but hopefully this helps others with this issue.

---

### Post by Mr.Kappa on 2010-05-05
The terminal sputtered out several errors, but after doing that, IT WORKS!!! :guitar:
Thanks for the tip pal!

---

### Post by qrwe on 2010-05-06
> **TyroneSlothrop said:**
> An update:

I issued the command: killall beam
I then removed the couchdb initialization file: rm ~/.config/desktop-couch/desktop-couchdb.ini 
I then issued the following command: dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
I then issued the command: xdg-open file:///home/USERNAME/.local/share/desktop-couch/couchdb.html

I was then presented with the Couch DB debugger, Futon.  I was able to run the oauth, replication, security_validation, and conflicts under the Test Suite option.

After that, I could once again re-sync with Ubuntu One, I had entries for Desktop Couch in keyring.  I was not able to start Gwibber, but when I tried I got a new message about a client not being present, not the original error message.  I then was able to run Broadcast Preferences in Administration, and ticked the 'Start service at login', ran some updates, restarted, and gwibber is now running for me.

Not sure if what I did got it fixed, or if there was a fix in the updates, but hopefully this helps others with this issue.

I can't tell if this is a solution or a workaround, especially when I hear folks say that the get error messages when trying this. I'm scared by default to remove config files as this may trash the whole environment (yep, I have some personal sigh-it's-easier-to-just-reinstall-the-whole-system-agin experiences in my portfolio). 
Nevertheless, TyroneSlothrop: can you propose this solution to the Launchpad. We are many who want to patch this issue once and for all. Thanks for your efforts, pal!

---

### Post by TyroneSlothrop on 2010-05-06
> Nevertheless, TyroneSlothrop: can you propose this solution to the Launchpad. We are many who want to patch this issue once and for all.

I would be happy to.

I totally understand your trepidation.  I probably wouldn't have been so gung-ho had I not already shot myself in the foot so-to-speak by deleting those keys.

Glad to be of help!

---

### Post by rock4christ on 2010-05-06
when i run replicatio, i get ```
Exception raised: {"message":"Cannot read property '_rev' of null","stack":"TypeError: Cannot read property '_rev' of null\n    at [object Object].afterAB1 (eval at patchTest (http://localhost:56759/_utils/script/couch_test_runner.js:36:5))\n    at eval at patchTest (http://localhost:56759/_utils/script/couch_test_runner.js:36:5)\n    at run (http://localhost:56759/_utils/script/couch_test_runner.js:78:7)","type":"non_object_property_load","arguments":["_rev",null]}
```
> **TyroneSlothrop said:**
> An update:

I issued the command: killall beam
I then removed the couchdb initialization file: rm ~/.config/desktop-couch/desktop-couchdb.ini 
I then issued the following command: dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
I then issued the command: xdg-open file:///home/USERNAME/.local/share/desktop-couch/couchdb.html

I was then presented with the Couch DB debugger, Futon.  I was able to run the oauth, replication, security_validation, and conflicts under the Test Suite option.

After that, I could once again re-sync with Ubuntu One, I had entries for Desktop Couch in keyring.  I was not able to start Gwibber, but when I tried I got a new message about a client not being present, not the original error message.  I then was able to run Broadcast Preferences in Administration, and ticked the 'Start service at login', ran some updates, restarted, and gwibber is now running for me.

Not sure if what I did got it fixed, or if there was a fix in the updates, but hopefully this helps others with this issue.

---

### Post by areskz on 2010-05-24
> **TyroneSlothrop said:**
> An update:
I then issued the following command: dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort

```
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
```

:(

---

### Post by areskz on 2010-05-24
Checkout [launchpad link]("https://bugs.launchpad.net/ubuntu/lucid/+source/gwibber/+bug/564741"), there is an updated gwibber in proposed repos.
And it works ;)

---

### Post by qrwe on 2010-05-25
> **areskz said:**
> Checkout [launchpad link]("https://bugs.launchpad.net/ubuntu/lucid/+source/gwibber/+bug/564741"), there is an updated gwibber in proposed repos.
And it works ;)

Yey! How long does it take before it hits the market for all mortals?

---

