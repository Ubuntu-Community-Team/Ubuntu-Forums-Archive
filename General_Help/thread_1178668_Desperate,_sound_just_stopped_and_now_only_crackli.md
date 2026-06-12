---
title: "Desperate, sound just stopped and now only crackling noise"
date: 2009-06-04
forum: General Help
---

### Post by blackSP on 2009-06-04
This morning I was happily playing MP3's on my Asus f8p Ubuntu 9.04 laptop through the Alsa mixer, tonight all sound is gone except for a crackling sound.

Searching the forum did not get me any further.
Anybody knows what this might be?

---

### Post by owainsutton on 2009-06-04
Same problem - I think it's only been since an update earlier today of various packages, although none of them were audio-related.  I can now choose OSS rather than ALSA in Sound Preferences, and get a working test tone, whereas before it was the other way around - so is ALSA broken?

---

### Post by blackSP on 2009-06-04
killall pulseaudio
sudo alsa force-reload

Doesn't help, also the OSS device, or any other one for that matter anly gives the crackles!

Also reinstalling Alsa and all related libs and packages, no go! BTW, I also accepted some updates, this clearly messed up the sound...

The test tone in the sound prefs does play when I choose OSS. WTF!!!

---

### Post by owainsutton on 2009-06-04
Here's my /var/log/apt/term.log for the past three days, if it's any help:

```

Log started: 2009-06-02  20:22:16
Selecting previously deselected package libawn0.

(Reading database ... 224156 files and directories currently installed.)

Unpacking libawn0 (from .../libawn0_0.3.2-0ubuntu2_i386.deb) ...

Selecting previously deselected package avant-window-navigator-data.

Unpacking avant-window-navigator-data (from .../avant-window-navigator-data_0.3.2-0ubuntu2_all.deb) ...

Selecting previously deselected package python-awn.

Unpacking python-awn (from .../python-awn_0.3.2-0ubuntu2_i386.deb) ...

Selecting previously deselected package awn-manager.

Unpacking awn-manager (from .../awn-manager_0.3.2-0ubuntu2_all.deb) ...

Selecting previously deselected package avant-window-navigator.

Unpacking avant-window-navigator (from .../avant-window-navigator_0.3.2-0ubuntu2_i386.deb) ...

Selecting previously deselected package libawn-extras0.

Unpacking libawn-extras0 (from .../libawn-extras0_0.3.2.1-0ubuntu3_i386.deb) ...

Selecting previously deselected package awn-applets-c-core.

Unpacking awn-applets-c-core (from .../awn-applets-c-core_0.3.2.1-0ubuntu3_i386.deb) ...

Selecting previously deselected package python-awn-extras.

Unpacking python-awn-extras (from .../python-awn-extras_0.3.2.1-0ubuntu3_i386.deb) ...

Selecting previously deselected package python-awnlib.

Unpacking python-awnlib (from .../python-awnlib_0.3.2.1-0ubuntu3_i386.deb) ...

Selecting previously deselected package awn-applets-python-core.

Unpacking awn-applets-python-core (from .../awn-applets-python-core_0.3.2.1-0ubuntu3_all.deb) ...

Selecting previously deselected package python-alsaaudio.

Unpacking python-alsaaudio (from .../python-alsaaudio_0.2-1ubuntu2_i386.deb) ...

Selecting previously deselected package python-dateutil.

Unpacking python-dateutil (from .../python-dateutil_1.4.1-2_all.deb) ...

Selecting previously deselected package python-feedparser.

Unpacking python-feedparser (from .../python-feedparser_4.1-12_all.deb) ...

Selecting previously deselected package python-sqlalchemy.

Unpacking python-sqlalchemy (from .../python-sqlalchemy_0.4.8-1_all.deb) ...

Selecting previously deselected package python-utidylib.

Unpacking python-utidylib (from .../python-utidylib_0.2-3.2ubuntu1_all.deb) ...

Selecting previously deselected package sqlite3.

Unpacking sqlite3 (from .../sqlite3_3.6.10-1_i386.deb) ...

Selecting previously deselected package python-xlib.

Unpacking python-xlib (from .../python-xlib_0.14-2_all.deb) ...

Processing triggers for man-db ...

Setting up libawn0 (0.3.2-0ubuntu2) ...



Setting up avant-window-navigator-data (0.3.2-0ubuntu2) ...



Setting up python-awn (0.3.2-0ubuntu2) ...



Setting up libawn-extras0 (0.3.2.1-0ubuntu3) ...



Setting up python-awn-extras (0.3.2.1-0ubuntu3) ...



Setting up python-awnlib (0.3.2.1-0ubuntu3) ...



Setting up python-alsaaudio (0.2-1ubuntu2) ...



Setting up python-dateutil (1.4.1-2) ...



Setting up python-feedparser (4.1-12) ...



Setting up python-sqlalchemy (0.4.8-1) ...



Setting up python-utidylib (0.2-3.2ubuntu1) ...



Setting up sqlite3 (3.6.10-1) ...

Setting up python-xlib (0.14-2) ...



Setting up avant-window-navigator (0.3.2-0ubuntu2) ...



Setting up awn-manager (0.3.2-0ubuntu2) ...



Setting up awn-applets-c-core (0.3.2.1-0ubuntu3) ...



Setting up awn-applets-python-core (0.3.2.1-0ubuntu3) ...



Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Processing triggers for python-support ...

/var/lib/python-support/python2.6/sqlalchemy/ext/activemapper.py:262: SyntaxWarning: assertion is always true, perhaps remove parentheses?

  assert(version_id_col_object is not None, "version_id_col (%s) does not exist." % version_id_col)

Log ended: 2009-06-02  20:23:14

Log started: 2009-06-02  20:33:31
(Reading database ... 225250 files and directories currently installed.)

Removing awn-applets-python-core ...

Removing awn-applets-c-core ...

Removing awn-manager ...

Removing avant-window-navigator ...

Processing triggers for man-db ...

Log ended: 2009-06-02  20:33:58

Log started: 2009-06-02  20:35:22
(Reading database ... 224722 files and directories currently installed.)

Removing avant-window-navigator-data ...

Selecting previously deselected package python-compizconfig.

(Reading database ... 224623 files and directories currently installed.)

Unpacking python-compizconfig (from .../python-compizconfig_0.8.2-0ubuntu1_i386.deb) ...

Selecting previously deselected package compizconfig-settings-manager.

Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb) ...

Setting up python-compizconfig (0.8.2-0ubuntu1) ...

Setting up compizconfig-settings-manager (0.8.2-0ubuntu1) ...



Log ended: 2009-06-02  20:35:45

Log started: 2009-06-02  20:36:42
Selecting previously deselected package simple-ccsm.

(Reading database ... 224816 files and directories currently installed.)

Unpacking simple-ccsm (from .../simple-ccsm_0.8.2-0ubuntu1_all.deb) ...

Setting up simple-ccsm (0.8.2-0ubuntu1) ...



Log ended: 2009-06-02  20:36:58

Log started: 2009-06-03  06:09:05
(Reading database ... 224860 files and directories currently installed.)

Preparing to replace foomatic-db-engine 4.0.0-0ubuntu6 (using .../foomatic-db-engine_4.0.0-0ubuntu6.1_i386.deb) ...

Unpacking replacement foomatic-db-engine ...

Preparing to replace cron 3.0pl1-105ubuntu1 (using .../cron_3.0pl1-105ubuntu1.1_i386.deb) ...

 * Stopping periodic command scheduler crond

   ...done.

Unpacking replacement cron ...

Preparing to replace libsqlite3-0 3.6.10-1 (using .../libsqlite3-0_3.6.10-1ubuntu0.2_i386.deb) ...

Unpacking replacement libsqlite3-0 ...

Preparing to replace evolution 2.26.1-0ubuntu1 (using .../evolution_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement evolution ...

Preparing to replace evolution-common 2.26.1-0ubuntu1 (using .../evolution-common_2.26.1-0ubuntu2_all.deb) ...

Unpacking replacement evolution-common ...

Preparing to replace evolution-plugins 2.26.1-0ubuntu1 (using .../evolution-plugins_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement evolution-plugins ...

Preparing to replace metacity-common 1:2.25.144-0ubuntu2 (using .../metacity-common_1%3a2.25.144-0ubuntu2.1_all.deb) ...

Unpacking replacement metacity-common ...

Preparing to replace libmetacity0 1:2.25.144-0ubuntu2 (using .../libmetacity0_1%3a2.25.144-0ubuntu2.1_i386.deb) ...

Unpacking replacement libmetacity0 ...

Preparing to replace mysql-common 5.1.30really5.0.75-0ubuntu10 (using .../mysql-common_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...

Unpacking replacement mysql-common ...

Preparing to replace libmysqlclient15off 5.1.30really5.0.75-0ubuntu10 (using .../libmysqlclient15off_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...

Unpacking replacement libmysqlclient15off ...

Preparing to replace metacity 1:2.25.144-0ubuntu2 (using .../metacity_1%3a2.25.144-0ubuntu2.1_i386.deb) ...

Unpacking replacement metacity ...

Preparing to replace sqlite3 3.6.10-1 (using .../sqlite3_3.6.10-1ubuntu0.2_i386.deb) ...

Unpacking replacement sqlite3 ...

Preparing to replace evolution-documentation-en 2.26.1-0ubuntu1 (using .../evolution-documentation-en_2.26.1-0ubuntu2_all.deb) ...

Unpacking replacement evolution-documentation-en ...

Preparing to replace gnome-settings-daemon 2.26.1-0ubuntu1 (using .../gnome-settings-daemon_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement gnome-settings-daemon ...

Processing triggers for man-db ...

Setting up foomatic-db-engine (4.0.0-0ubuntu6.1) ...



Setting up cron (3.0pl1-105ubuntu1.1) ...

 * Starting periodic command scheduler crond

   ...done.



Setting up libsqlite3-0 (3.6.10-1ubuntu0.2) ...



Setting up evolution-common (2.26.1-0ubuntu2) ...



Setting up evolution (2.26.1-0ubuntu2) ...



Setting up evolution-plugins (2.26.1-0ubuntu2) ...

Setting up metacity-common (1:2.25.144-0ubuntu2.1) ...



Setting up libmetacity0 (1:2.25.144-0ubuntu2.1) ...



Setting up mysql-common (5.1.30really5.0.75-0ubuntu10.2) ...

Setting up libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2) ...



Setting up metacity (1:2.25.144-0ubuntu2.1) ...



Setting up sqlite3 (3.6.10-1ubuntu0.2) ...

Setting up evolution-documentation-en (2.26.1-0ubuntu2) ...



Setting up gnome-settings-daemon (2.26.1-0ubuntu2) ...



Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Log ended: 2009-06-03  06:10:08

Log started: 2009-06-04  12:29:21
Selecting previously deselected package icoutils.

(Reading database ... 224860 files and directories currently installed.)

Unpacking icoutils (from .../icoutils_0.26.0-2ubuntu1_i386.deb) ...

Processing triggers for man-db ...

Setting up icoutils (0.26.0-2ubuntu1) ...

Log ended: 2009-06-04  12:30:05

Log started: 2009-06-04  13:14:57
(Reading database ... 224875 files and directories currently installed.)

Preparing to replace libcups2-dev 1.3.9-17ubuntu3 (using .../libcups2-dev_1.3.9-17ubuntu3.1_i386.deb) ...

Unpacking replacement libcups2-dev ...

Preparing to replace libcups2 1.3.9-17ubuntu3 (using .../libcups2_1.3.9-17ubuntu3.1_i386.deb) ...

Unpacking replacement libcups2 ...

Preparing to replace libcupsimage2 1.3.9-17ubuntu3 (using .../libcupsimage2_1.3.9-17ubuntu3.1_i386.deb) ...

Unpacking replacement libcupsimage2 ...

Preparing to replace cups-common 1.3.9-17ubuntu3 (using .../cups-common_1.3.9-17ubuntu3.1_all.deb) ...

Unpacking replacement cups-common ...

Preparing to replace cups 1.3.9-17ubuntu3 (using .../cups_1.3.9-17ubuntu3.1_i386.deb) ...

 * Stopping Common Unix Printing System: cupsd

   ...done.

Unpacking replacement cups ...

Preparing to replace cups-bsd 1.3.9-17ubuntu3 (using .../cups-bsd_1.3.9-17ubuntu3.1_i386.deb) ...

Unpacking replacement cups-bsd ...

Preparing to replace cups-client 1.3.9-17ubuntu3 (using .../cups-client_1.3.9-17ubuntu3.1_i386.deb) ...

Unpacking replacement cups-client ...

Preparing to replace libedataserver1.2-11 2.26.1-0ubuntu1 (using .../libedataserver1.2-11_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libedataserver1.2-11 ...

Preparing to replace libcamel1.2-14 2.26.1-0ubuntu1 (using .../libcamel1.2-14_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libcamel1.2-14 ...

Preparing to replace libebackend1.2-0 2.26.1-0ubuntu1 (using .../libebackend1.2-0_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libebackend1.2-0 ...

Preparing to replace libebook1.2-9 2.26.1-0ubuntu1 (using .../libebook1.2-9_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libebook1.2-9 ...

Preparing to replace libecal1.2-7 2.26.1-0ubuntu1 (using .../libecal1.2-7_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libecal1.2-7 ...

Preparing to replace libedata-book1.2-2 2.26.1-0ubuntu1 (using .../libedata-book1.2-2_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libedata-book1.2-2 ...

Preparing to replace libedata-cal1.2-6 2.26.1-0ubuntu1 (using .../libedata-cal1.2-6_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libedata-cal1.2-6 ...

Preparing to replace libegroupwise1.2-13 2.26.1-0ubuntu1 (using .../libegroupwise1.2-13_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libegroupwise1.2-13 ...

Preparing to replace libgdata1.2-1 2.26.1-0ubuntu1 (using .../libgdata1.2-1_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libgdata1.2-1 ...

Preparing to replace libgdata-google1.2-1 2.26.1-0ubuntu1 (using .../libgdata-google1.2-1_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libgdata-google1.2-1 ...

Preparing to replace evolution-data-server 2.26.1-0ubuntu1 (using .../evolution-data-server_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement evolution-data-server ...

Preparing to replace evolution-data-server-common 2.26.1-0ubuntu1 (using .../evolution-data-server-common_2.26.1-0ubuntu2_all.deb) ...

Unpacking replacement evolution-data-server-common ...

Preparing to replace libedataserverui1.2-8 2.26.1-0ubuntu1 (using .../libedataserverui1.2-8_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libedataserverui1.2-8 ...

Preparing to replace libexchange-storage1.2-3 2.26.1-0ubuntu1 (using .../libexchange-storage1.2-3_2.26.1-0ubuntu2_i386.deb) ...

Unpacking replacement libexchange-storage1.2-3 ...

Preparing to replace libpurple-bin 1:2.5.5-1ubuntu8 (using .../libpurple-bin_1%3a2.5.5-1ubuntu8.1_all.deb) ...

Unpacking replacement libpurple-bin ...

Preparing to replace pidgin-data 1:2.5.5-1ubuntu8 (using .../pidgin-data_1%3a2.5.5-1ubuntu8.1_all.deb) ...

Unpacking replacement pidgin-data ...

Preparing to replace libpurple0 1:2.5.5-1ubuntu8 (using .../libpurple0_1%3a2.5.5-1ubuntu8.1_i386.deb) ...

Unpacking replacement libpurple0 ...

Preparing to replace pidgin 1:2.5.5-1ubuntu8 (using .../pidgin_1%3a2.5.5-1ubuntu8.1_i386.deb) ...

Unpacking replacement pidgin ...

Processing triggers for man-db ...

Processing triggers for doc-base ...

Processing 1 changed doc-base file(s)...

Registering documents with scrollkeeper...

Processing triggers for ufw ...

Setting up libcups2 (1.3.9-17ubuntu3.1) ...



Setting up libcups2-dev (1.3.9-17ubuntu3.1) ...

Setting up libcupsimage2 (1.3.9-17ubuntu3.1) ...



Setting up cups-common (1.3.9-17ubuntu3.1) ...

Setting up cups (1.3.9-17ubuntu3.1) ...

 * Reloading AppArmor profiles ...

   ...done.

 * Starting Common Unix Printing System: cupsd

   ...done.



Setting up cups-client (1.3.9-17ubuntu3.1) ...



Setting up cups-bsd (1.3.9-17ubuntu3.1) ...



Setting up libedataserver1.2-11 (2.26.1-0ubuntu2) ...



Setting up libcamel1.2-14 (2.26.1-0ubuntu2) ...



Setting up libebackend1.2-0 (2.26.1-0ubuntu2) ...



Setting up libebook1.2-9 (2.26.1-0ubuntu2) ...



Setting up libecal1.2-7 (2.26.1-0ubuntu2) ...



Setting up libedata-book1.2-2 (2.26.1-0ubuntu2) ...



Setting up libedata-cal1.2-6 (2.26.1-0ubuntu2) ...



Setting up libegroupwise1.2-13 (2.26.1-0ubuntu2) ...



Setting up libgdata1.2-1 (2.26.1-0ubuntu2) ...



Setting up libgdata-google1.2-1 (2.26.1-0ubuntu2) ...



Setting up evolution-data-server-common (2.26.1-0ubuntu2) ...

Setting up evolution-data-server (2.26.1-0ubuntu2) ...

Setting up libedataserverui1.2-8 (2.26.1-0ubuntu2) ...



Setting up libexchange-storage1.2-3 (2.26.1-0ubuntu2) ...



Setting up libpurple-bin (1:2.5.5-1ubuntu8.1) ...

Setting up pidgin-data (1:2.5.5-1ubuntu8.1) ...



Setting up libpurple0 (1:2.5.5-1ubuntu8.1) ...



Setting up pidgin (1:2.5.5-1ubuntu8.1) ...



Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Log ended: 2009-06-04  13:16:02

Log started: 2009-06-04  13:31:55
Selecting previously deselected package lynx-cur.

(Reading database ... 224875 files and directories currently installed.)

Unpacking lynx-cur (from .../lynx-cur_2.8.7dev11-2_i386.deb) ...

Selecting previously deselected package lynx.

Unpacking lynx (from .../lynx_2.8.7dev11-2_all.deb) ...

Processing triggers for man-db ...

Processing triggers for doc-base ...

Processing 1 added doc-base file(s)...

Registering documents with scrollkeeper...

Setting up lynx-cur (2.8.7dev11-2) ...



Setting up lynx (2.8.7dev11-2) ...

Log ended: 2009-06-04  13:31:58

Log started: 2009-06-04  16:01:43
Selecting previously deselected package dkms.

(Reading database ... 224949 files and directories currently installed.)

Unpacking dkms (from .../dkms_2.0.21.1-0ubuntu3_all.deb) ...

Selecting previously deselected package fakeroot.

Unpacking fakeroot (from .../fakeroot_1.12.1ubuntu1_i386.deb) ...

Selecting previously deselected package patch.

Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...

Processing triggers for man-db ...

Setting up dkms (2.0.21.1-0ubuntu3) ...

 * Running DKMS auto installation service for kernel 2.6.28-11-generic       [80G 
[74G[ OK ]



Setting up fakeroot (1.12.1ubuntu1) ...



Setting up patch (2.5.9-5) ...

Log ended: 2009-06-04  16:02:07

Log started: 2009-06-04  16:24:26
Selecting previously deselected package gwget.

(Reading database ... 225035 files and directories currently installed.)

Unpacking gwget (from .../gwget_1.0.1-0ubuntu1_i386.deb) ...

Processing triggers for man-db ...

Setting up gwget (1.0.1-0ubuntu1) ...

You must have at least one <locale> entry in a <schema>

You must have at least one <locale> entry in a <schema>

You must have at least one <locale> entry in a <schema>

You must have at least one <locale> entry in a <schema>

You must have at least one <locale> entry in a <schema>



Log ended: 2009-06-04  16:24:29

Log started: 2009-06-04  17:01:19
Selecting previously deselected package libssl-dev.

(Reading database ... 225102 files and directories currently installed.)

Unpacking libssl-dev (from .../libssl-dev_0.9.8g-15ubuntu3_i386.deb) ...

Processing triggers for man-db ...

Setting up libssl-dev (0.9.8g-15ubuntu3) ...

Log ended: 2009-06-04  17:01:45
```

---

### Post by dagrump on 2009-06-04
You could try editing  /etc/pulse/daemon.conf edit the line 
resample-method = src-linear make it
resample-method = speex-float-1
You may need to reboot, but that worked for me on karmic, & it should work w/9.04.

---

### Post by owainsutton on 2009-06-04
> **dagrump said:**
> You could try editing  /etc/pulse/daemon.conf edit the line 
resample-method = src-linear make it
resample-method = speex-float-1
You may need to reboot, but that worked for me on karmic, & it should work w/9.04.

Before I do that, what does this do?  Bearing in mind I had a perfectly functioning system until ca. 24 hours ago!

(Edit: yes, I do have a backup from before the update, I just really can't be arsed to backup everything I've done today, just to restore that...)

---

### Post by dagrump on 2009-06-04
Well from what i understand there are several resampling methods each with various cpu loads. src-linear being very low on the scale, speex-float-1 is using a little more cpu. There is more info in the development (karmic) forum look for a thread about sound distortion, it's down a few pages by now.
I'm not a sound expert so I just stumble along, trying stuff if it doesn't fix it I revert back & look for something else to try.

---

### Post by owainsutton on 2009-06-04
Thanks - however, I'd rather identify what it was that has stopped things working, when previously ALSA was OK.  What we're talking about isn't  distortion, but a complete foul-up of the audio system.  Nothing but crackling (not static), and the crackling isn't in my experience related to what was supposed to be heard, but more-or-less continuous.

---

### Post by dagrump on 2009-06-04
Well, good luck. Crackling was the issue w/ my machine, & the issue in the thread I suggested you look for. It seems to also depend on hardware as some of my machines continue using src-linear w/o issue & 2 didn't.
Any way sorry I couldn't help.

---

### Post by owainsutton on 2009-06-04
Sorry if I came across more dismissive than I meant to....all that I was concerned with was that I had a functioning system, which has screwed up very recently.  It can't be hardware, because I haven't changed any!

---

### Post by Chronon on 2009-06-04
I get crackling when certain mixer levels get muted.  You could go through and carefully check that neither ALSA nor Pulse have been muted somehow.  I have no idea why your mixer levels would have changed, so it's a long shot.  Still, the best I can come up with.

---

### Post by Lunx on 2009-06-04
> **Chronon said:**
> I get crackling when certain mixer levels get muted.  You could go through and carefully check that neither ALSA nor Pulse have been muted somehow.  I have no idea why your mixer levels would have changed, so it's a long shot.  Still, the best I can come up with.

Yeah, I was thinking exactly that myself. Hasn't happened to me since I've been using Jaunty, but a couple of times with Intrepid I found the PCM setting was muted, even though I'd not been messing with it - weird.

---

### Post by blackSP on 2009-06-05
> **dagrump said:**
> You could try editing  /etc/pulse/daemon.conf edit the line 
resample-method = src-linear make it
resample-method = speex-float-1
You may need to reboot, but that worked for me on karmic, & it should work w/9.04.

Tried this and no result other than more crackling.


Update:
I skipped the PCM setting that was mentioned and it was indeed lowered to zero but not muted through the mute button. Anyway, cranking it up fixed things.
Which brings me to another question: where does the crackling come from and why does it go away when you turn up the slider?

---

### Post by owainsutton on 2009-06-08
> **Lunx said:**
> Yeah, I was thinking exactly that myself. Hasn't happened to me since I've been using Jaunty, but a couple of times with Intrepid I found the PCM setting was muted, even though I'd not been messing with it - weird.

That turned out to be exactly what had happened to mine :-s

---

### Post by Goddard on 2009-06-08
Yeah same thing happened to me...to fix it for me all I did was 

```
alsamixer
```

Then I turned everything up.

---

