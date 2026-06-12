---
title: "Dofus"
date: 2007-01-28
forum: Gaming &amp; Leisure
---

### Post by ELD on 2007-01-28
If you havn't seen it on the ubuntu gamers arena then you may want to take a look (stickied post at top of forum).

Just wondering if anyone has tried it yet and wants to let me know what they think?

---

### Post by RomeReactor on 2007-01-28
Yeah, i've played it. The graphics were the first thing that attracted me to it, though i didn't expect the gameplay to be a mixture of strategy/mmorpg. It's fun, though i entered on a french server and *very* few people there speak english, so when i got lost after a while i just didn't know who to ask for help XD. Anyway, i enjoy playing it once in a while. If you like it, also check out [Pox Nora]("http://www.poxnora.com/"); i posted about it on [this]("http://www.ubuntuforums.org/showthread.php?t=324974) thread, though nobody answered (due to the vague title, i guess XD ).

---

### Post by matt_risi on 2007-02-22
I just downloaded it in a 90 meg .zip file for Linux.. HOW DO I INSTALL?! I've been neglecting to learn how to do this, hunting for .deb files for everything.. but now I face the wall. Any help? There's no ./configure to use.

---

### Post by Perfect Storm on 2007-02-22
Check Ubuntu Gaming Arena's howto list, you'll find alot of howtos there (and still growing).

---

### Post by matt_risi on 2007-02-26
Thanks for the link, the install is still botched but at least I'll have some clue in the future.

---

### Post by ELD on 2007-03-02
I played the game and honestly didn't think much of it. It is in flash and so theres no right click as the flash menu comes up, and i just couldn't get into it.

But it is a nice idea, and the graphics are nice!

---

### Post by Tobster on 2007-06-09
I cant seem to install it :(

---

### Post by hikaricore on 2007-06-09
> **Tobster said:**
> I cant seem to install it :(

The problem with Dofus on linux is the lack of a proper flash control panel under linux.

The only way to access the "control panel" is to goto part of the Adobe website with
a flash based interface for the settings on your system.  Sounds a bit assbackwards
doesn't it?  So anyway, you goto this site:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html)

And add the location where you extracted dofus to the trusted locations.  For example
if you have dofus in your home directory, in a folder called dofus, you would add:

*/home/username/dofus*

Then restart your browser and navigate to the location of Dofus:

*file:///home/username/dofus/loader.swf*

And off you go.  ^_^

Personally I use the stand alone flash player released by adobe along with a bash script for starting the game.  It's simple enough so I'll just paste mine here incase you want to use it as a guideline, replacing locations were obviously appropriate.

> #! /bin/bash
cd /media/devistate/linux.bin/dofus &&
gflashplayer /media/devistate/linux.bin/dofus/loader.swf &


If it's not already installed on your system, the stand alone flash player can be downloaded in this archive:
[http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz)

Just place the gflashplayer binary in your /usr/bin or somewhere else easy to find.

---

### Post by nuff on 2007-09-07
Hi,

could you please tell me, how to configure the security settings via the settings manager for the stand alone version. It seems, that the settingsmanager from the homepage of macromedia only changes the settings for the firefox plugin, not for the stand alone flashplayer.

THX

Greetz
nuff

---

### Post by hikaricore on 2007-09-07
Settings should be global.  I use a standalone player while playing Dofus..

---

### Post by mightyzug on 2007-10-01
i bring up the control panel and nothing happens, it won't let me add anything to trusted sites

i click add and it just sits there like nothing happened

---

### Post by Perfect Storm on 2007-10-02
Try this guide; [http://gaming.gwos.org/doku.php/guides:dofus](http://gaming.gwos.org/doku.php/guides:dofus)

---

### Post by glantela on 2007-10-03
Hey, I am trying to run Dofus but it keeps getting stuck on the loading screen, I know a lot of people probably have had this problem, i just couldnt find an answer for it.  I have my adobe flash set up to accept it as well.  Thanks

---

### Post by Perfect Storm on 2007-10-03
Have you tried with the latest version of flash?

---

### Post by glantela on 2007-10-03
Ah cripes, i figured it out, i just had to select the whole folder in the adobe flash settings instead of just the loader.sfx file.  Whoops :) Thanks though

---

