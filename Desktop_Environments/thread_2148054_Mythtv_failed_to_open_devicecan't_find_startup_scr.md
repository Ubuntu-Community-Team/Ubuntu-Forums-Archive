---
title: "Mythtv failed to open device/can't find startup script"
date: 2013-05-23
forum: Desktop Environments
---

### Post by kr651129 on 2013-05-23
I thought I'd give mythtv one last try.  I installed the DVB drivers and was able to see my card, then I get the following errors

```

2013-05-23 18:58:45.922077 C  mythbackend version: master [v0.27-pre2-1076-gf9c342e] www.mythtv.org
2013-05-23 18:58:45.922097 C  Qt version: compile: 4.8.4, runtime: 4.8.4
2013-05-23 18:58:45.922101 N  Enabled verbose msgs:  general
2013-05-23 18:58:45.922110 N  Setting Log Level to LOG_INFO
2013-05-23 18:58:45.922715 I  Added logging to the console
2013-05-23 18:58:45.923004 I  Setup Interrupt handler
2013-05-23 18:58:45.923014 I  Setup Terminated handler
2013-05-23 18:58:45.923023 I  Setup Segmentation fault handler
2013-05-23 18:58:45.923031 I  Setup Aborted handler
2013-05-23 18:58:45.923038 I  Setup Bus error handler
2013-05-23 18:58:45.923045 I  Setup Floating point exception handler
2013-05-23 18:58:45.923052 I  Setup Illegal instruction handler
2013-05-23 18:58:45.923061 I  Setup Real-time signal 0 handler
2013-05-23 18:58:45.923143 N  Using runtime prefix = /usr/local
2013-05-23 18:58:45.923179 N  Using configuration directory = /home/kclark/.mythtv
2013-05-23 18:58:45.923400 I  Assumed character encoding: en_US.UTF-8
2013-05-23 18:58:45.923749 N  Empty LocalHostName.
2013-05-23 18:58:45.923755 I  Using localhost value of krisbox
2013-05-23 18:58:45.933821 N  Setting QT default locale to en_US
2013-05-23 18:58:45.933915 I  Current locale en_US
2013-05-23 18:58:45.933984 N  Reading locale defaults from /usr/local/share/mythtv//locales/en_us.xml
2013-05-23 18:58:45.941619 I  Current MythTV Schema Version (DBSchemaVer): 1310
2013-05-23 18:58:45.942276 I  Loading en_us translation for module mythfrontend
2013-05-23 18:58:45.943008 N  MythBackend: Starting up as the master server.
2013-05-23 18:58:45.947805 E  TVRec[1]: Problem finding starting channel, setting to default of '3'.
2013-05-23 18:58:46.094878 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-05-23 18:58:46.094953 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2013-05-23 18:58:46.095035 E  Problem with capture cardsCard 1failed init
2013-05-23 18:58:46.096934 E  TVRec[2]: Problem finding starting channel, setting to default of '3'.
2013-05-23 18:58:46.097078 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.147222 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.152375 I  Added logging to mythlogserver at TCP:35327
2013-05-23 18:58:46.197364 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.247569 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.297776 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.347997 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.398205 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.448409 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.498630 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.548855 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.599076 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.649212 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.699419 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.749564 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.799784 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.849988 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.900196 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:46.950403 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:47.000623 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:47.050827 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2013-05-23 18:58:47.050846 E  DVBChan[2](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2013-05-23 18:58:47.050860 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2013-05-23 18:58:47.050906 E  Problem with capture cardsCard 2failed init
2013-05-23 18:58:47.050933 W  MythBackend: No valid capture cards are defined in the database.
2013-05-23 18:58:47.051967 E  Scheduler: No channel sources defined in the database

```

After googling a bit I found [this thread]("http://ubuntuforums.org/showthread.php?t=1345079").  In it they say they had solved this problem by editing the startup script in /etc/init/mythtv-backend.conf

The problem is I can't find this on my system, I even tried

```
sudo find / -name mythtv-backend.conf
```

Without success.  I'm running Ubuntu 13.04 x64, does anyone know how I can solve this?

---

### Post by kr651129 on 2013-05-23
Figured it out, it was in the error log the whole time, I had to bind the card to a broadcast then scan for channels.

---

### Post by lionel.barker on 2014-05-18
I am in pretty much the same situation.   What exactly did you do to "bind the card to a broadcast"

---

