---
title: "Quake Live plugin problem with Firefox 4"
date: 2011-03-22
forum: Gaming &amp; Leisure
---

### Post by Virus666 on 2011-03-22
Hi all,

As all of you know that **Firefox 4** final was released yesterday. That is a brilliant version of Firefox with a small problem: **Quake Live** linux plugin compability...

Short after the release of Firefox 4, **Mozilla Team** announced Firefox 4 Stable PPA.

[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

However, when I tried to login [http://www.quakelive.com/](http://www.quakelive.com/) with Firefox 4, the site directs me to the plugin installation screen and at the end of the process Firefox 4 fails to install the plugin...

After my short research I found the easiest fix in Quake Live forums:

[http://www.quakelive.com/forum/showthread.php?7195-Problem-with-firefox-4-on-Linux&p=112626&viewfull=1#post112626](http://www.quakelive.com/forum/showthread.php?7195-Problem-with-firefox-4-on-Linux&p=112626&viewfull=1#post112626)

Quake Live plugin fix for Firefox 4:


[LIST]
[*]Login Quake Live with Firefox 4.
[*]Accept the license agreement.
[*]Ignore the plugin installation; right click the "[click here]("http://cdn.quakelive.com/assets/2011031503/QuakeLivePlugin_433.xpi?v=0,1,0,433")" text and save as the plugin into your desktop.
[*]Close Firefox.
[*]Open the **.xpi** file with **File Roller** and reach plugins folder.
[*]Drag and drop the suitable **.so** file for your operating system to the **~/.mozilla/plugins** folder. (If there is no **plugins** folder; create it) (i386 for 32 bit, x64 for 64 bit)
[/LIST]
That's all... Now you can enter the game without a plugin issue... The plugin that has issue with Firefox 4 is "**QuakeLivePlugin_433.xpi**". I hope they will update it soon...

Have fun... :guitar:

---

### Post by rajeev1204 on 2011-03-29
oops sorry,

same method.


Quakelive as of now does not support firefox 4 which seems to be the issue.But yes this method is easiest and works fine.

---

