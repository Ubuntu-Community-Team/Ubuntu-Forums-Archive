---
title: "How to get MythTV to work?"
date: 2005-09-27
forum: Desktop Environments
---

### Post by veraction on 2005-09-27
I have tvtime program working great, now just need MythTV to work. With MythTV, I cannot watch TV or do anything because the MythTV backend isn't working. For some reason, I cann't get the mythbackend to start because of: ```
$ sudo /etc/init.d/mythtv-backend start
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

```From what I've read, this might be because my version,```
mysql  Ver 12.22 Distrib 4.0.23, for pc-linux-gnu (i386)
```, is too new (according to [this]("http://episteme.arstechnica.com/groupee/forums/a/tpc/f/96509133/m/424009325731/r/786009045731"). In that thread, they say the solution is to force MySQL to use oldstyle passwords by using a command: ```
$ mysqld --old-passwords
```. However, there doesn't seem to be an option for old passwords.

Any ideas? Do I have to remove MySQL and install and old version? (which I'd prefer not to do cause I use it for other things)

[edit] by the way, both MythTV and MySQL are up to date versions, installed via apt-get

---

### Post by veraction on 2005-09-30
bump.

just want to know, if anyone has gotten MythTV to work by just apt-getting it and configuring it?

---

### Post by Joshua on 2005-10-04
Yes, I have been able to get it to work.  I have the pcHDTV 3000 card so I needed to use Breezy.  It comes with 2.6.12 kernel and has the DVB drivers build in so that the pcHDTV card will work out of the box.  I followed this:
[http://www.abarbaccia.com](http://www.abarbaccia.com)
for most of it.

Some notes about my particular case:

- I actually have an AMD64 processor.  The AMD64 version of Breezy is really great but MythTV IS NOT APT-GET-ABLE in the AMD64 version.  It's really annoying me because now I have to use the i386 version and that's just not as cool.

- You need the pcHDTV firmware to get the pcHDTV card card to work.  Maybe this is obvious to everyone else, but no one seems to mention this - even sites specific to the pcHDTV cards.  You download the files from the pcHDTV website and copy them to /usr/lib/hotplug/firmware.  There is a readme somewhere on the pcHDTV website that describes this, but in RedHat and other distros the firmware files go somewhere else.  In Ubuntu they go in /usr/lib/hotplug/firmware (I think ;-))

- During configuration, when you select the card type, use DVB NOT pcHDTV.  When you select DVB it should recognize your card and show you some info about it below.

---

### Post by tktreload on 2005-10-04
I also get that error, but when starting mythtv by doing: sudo mythtv-backend I get tv for some time until i set a segmentation error and the backend terminates.

---

### Post by Az7 on 2005-11-13
I'm also using an HD 3000 card following the directions at [http://www.abarbaccia.com](http://www.abarbaccia.com).  In mytv-setup i chose the dvb card.  However, when i try to watch or record tv i get the following errors for my mythbackend.

```

2005-11-13 22:42:24.570 DVB#0 DVB SI Table Parser Started
2005-11-13 22:42:24.570 DVB#0 Using DVB card 0, with frontend pcHDTV HD3000 HDTV.
2005-11-13 22:42:24.583 New DB connection, total: 3
2005-11-13 22:42:24.583 DVB#0 ERROR - Could not find dvb tuning parameters for transport 0
2005-11-13 22:42:24.584 DVB#0 ERROR - Failed to get channel options for channel 3.
2005-11-13 22:42:26.848 DVB#0 Recorder: Card opened successfully (using PS mode).
2005-11-13 22:42:26.849 DVB#0 ERROR - No PIDS set, please correct your channel setup.
2005-11-13 22:42:27.849 DVB#0 WARNING - No data from card in 1 second.
2005-11-13 22:42:28.850 DVB#0 WARNING - No data from card in 1 second.
2005-11-13 22:42:29.851 DVB#0 WARNING - No data from card in 1 second.

```

When i set up my card i used 'modprobe cx88-dvb' tvtime works perfectly with my current settings.

---

### Post by Joshua on 2005-12-19
[QUOTE=Az7]
```

2005-11-13 22:42:24.584 DVB#0 ERROR - Failed to get channel options for channel 3.

```
[/QUOTE]

I know it's been a while for this thread, but maybe you haven't chosen an actual channel with a strong signal in the MythTV setup?  Sorry to do this, but I'm going to have to be vague here because I haven't been working on my MythTV box in a while.  There should be an option somewhere in the setup (I think it's the initial setup, not the configuration after you start Myth).  It will ask for a starting channel, or something like that.  If your card is set up to get digital signals, the format should be something like 26_1 (for channel 26 and subchannel 1).  The error that you have above looks like this option was left as the default or something.  You must have an actual channel with a strong signal.

Also have you copied the firmware files to the proper directory and reloaded the DVB modules?

---

### Post by Az7 on 2005-12-20
When I scan for channels I am unable to get a lock on any.  Oddly enough, tvtime works great.  I loaded the firmware drivers and rebooted.  Mythtv-Setup now claims my dvb card is busy.

---

### Post by bneuro1 on 2005-12-20
Here work great with twinhan 1030 DVB card. I follow 

[http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)
[http://www.parker1.co.uk/mythtv.php](http://www.parker1.co.uk/mythtv.php)

:)

---

### Post by Az7 on 2005-12-25
I killed the backend, and reran mythtv-setup.  I guess the backend was holding up the card.  However, now I'm unable to add any channels when building the channels list.

```
2005-12-25 11:56:29.723 DVB#0 WARNING - Status: NO LOCK!
2005-12-25 11:56:31.179 DVB#0 DVB signal 7916 | snr f0a3 | ber    0 | unc    0
2005-12-25 11:56:32.643 DVB#0 DVB signal 126d | snr ee69 | ber    0 | unc    0
2005-12-25 11:56:34.283 DVB#0 DVB signal 74fd | snr ef1f | ber    0 | unc    0
2005-12-25 11:56:34.584 DVB#0 WARNING - Status: NO LOCK!
2005-12-25 11:56:35.084 DVB#0 DVB signal 7332 | snr ed7d | ber    0 | unc    0
2005-12-25 11:56:36.087 DVB#0 Signal Locked
2005-12-25 11:56:36.536 DVB#0 DVB signal f8d4 | snr fd41 | ber    0 | unc    0
2005-12-25 11:56:36.536 DVB#0 Status: LOCK.
2005-12-25 11:56:41.989 DVB#0 Signal Lost

```

---

### Post by Az7 on 2006-02-05
Still getting the same error

---

### Post by Rocketeer on 2006-04-11
same problem here.

---

