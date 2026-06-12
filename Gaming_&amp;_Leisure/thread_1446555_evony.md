---
title: "evony"
date: 2010-04-04
forum: Gaming &amp; Leisure
---

### Post by jimbean on 2010-04-04
evony i know is browser based it worked for a month but now is locking up all the time cleared my personel data and reset modem ,still the same
anybody else having problems

---

### Post by efikkan on 2010-04-04
Is flash working fine otherwise? (YouTube etc.)

---

### Post by El_Cucuy on 2010-06-19
I play Evony II and also have similar problems.  When ever I start the game It will load to 100% then just go blank and the bottom of the browser will say DONE. The same will occur if I have multiple tabs open in Firefox. If I switch between them and come back the Evony II game will go blank.  Forcing me to reload the game. I know it is a lot to ask of Firefox if I can play more than one game at a time so I won't ask for a solution at this time.   (Envoy tab 1, Mafia Wars tab 2) As for flash working fine other wise it depends on your definition of working. In You Tube I can play all streams, If I want to pause or maximize it's hit or miss there. Sometimes going to the host channel will resolve this issue.  It's just annoying. I didn't have a problem with it until I upgraded from 9.04.  I've read post on purging flash and installing the non-free version of flash here's what I've tried so far.

archie@archie-desktop:~$ sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

[sudo] password for archie: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package adobe-flashplugin

archie@archie-desktop:~$ sudo apt-get install flashplugin-nonfree

Reading package lists... Done

Building dependency tree       

Reading state information... Done

flashplugin-nonfree is already the newest version.

The following packages were automatically installed and are no longer required:

  libkabcommon4 kdepim-kresources ttf-wqy-zenhei binutils-static

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

archie@archie-desktop:~$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Package swfdec-mozilla is not installed, so not removed

Package swfdec-gnome is not installed, so not removed

Package mozilla-plugin-gnash is not installed, so not removed

Package gnash is not installed, so not removed

The following packages were automatically installed and are no longer required:

  libkabcommon4 kdepim-kresources ttf-wqy-zenhei binutils-static

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

archie@archie-desktop:~$ sudo apt-get install flashplugin-nonfree

Reading package lists... Done

Building dependency tree       

Reading state information... Done

flashplugin-nonfree is already the newest version.

The following packages were automatically installed and are no longer required:

  libkabcommon4 kdepim-kresources ttf-wqy-zenhei binutils-static

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

archie@archie-desktop:~$ 


It would be nice if Envoy wasn't browser based and was simply a stand alone game.  It would probably resolve a lot of issues with the game. There's a point when a game is to big to live with it's parents and just simply needs to move out.  

:lolflag:

---

### Post by zandebar on 2011-01-19
I have been having the same problems getting evony to load on Firefox ever since I did the updates on Ubuntu, I decided to try Chromium browser, and evony works awesome now, though, I had to refresh a couple of times to get it to work.  So far no crashes though, I've been browsing other places and can actually go back to evony.

---

### Post by RockStarzInc on 2011-02-18
This is a problem that has no been fixed yet from Ubuntu or Adobe or Evony. Some people it works just fine some people is doesn't and they all seem to have the same version of Adobe Flash but the best way for now is to download Google Chrome Web Broswer for your Ubuntu and it should work just fine until the firefox problem gets fixed :cool:

---

