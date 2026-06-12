---
title: "Firefox and Mozilla Locking Up My Hoary"
date: 2005-04-19
forum: Desktop Environments
---

### Post by ZakZak on 2005-04-19
Everything is working great on my Hoary machine (Dell Inspiron 8200) except for Mozilla and Firefox.  Every time I start browsing with either one, after some period of time (sometimes almost immediately, sometimes it takes 15 or 20 minutes) it will lock up my entire console session.

I can SSH into the machine from somewhere else and reboot it, but there seems to be no way to get my console session working again!

This box was running Warty with Firefox from backports and has been upgraded to Hoary, so there's always the possibility that's causing problems.  But at the moment, all of my mozilla packages appear to be Hoary versions.

Everything else seems to be working great!  Networking and monitors, Tomboy, Gaim, RDesktop, Rhythmbox, Thunderbird - all working.  It's only Firefox and Mozilla that cause the lockups.

Would appreciate any ideas on how I might fix this!

Thanks,
-Zak

---

### Post by TravisNewman on 2005-04-19
what kind of plugins do you have in Firefox? Java, Flash, etc?

---

### Post by ZakZak on 2005-04-19
[QUOTE=panickedthumb]what kind of plugins do you have in Firefox? Java, Flash, etc?[/QUOTE]

Looks like kaffeine-mozilla, libflash-mozplugin, mozilla-bonobo, mozilla-opensc, mozilla-plugin-vlc, mozplugger, acroread-plugin, and mozilla-mplayer.

This doesn't happen when I visit specific sites or anything - it's just very random.  Sometimes immediately when I open Firefox (trying to load /usr/share/ubuntu-artwork/home/index.html) and sometimes not until 30 minutes later when I click on a link.

I've been messing with stuff since I originally reported this problem (I didn't have mozplugger or mozilla-plugin-vlc installed earlier).  And I haven't had a lockup in 30 minutes or so now so maybe it's fixed now...  <shrug>

Anyhow, any ideas what could be (or could have been) causing it would be appreciated!

Thanks,
-Zak

---

### Post by guyforget on 2005-04-19
[QUOTE=ZakZak]Looks like kaffeine-mozilla, libflash-mozplugin, mozilla-bonobo, mozilla-opensc, mozilla-plugin-vlc, mozplugger, acroread-plugin, and mozilla-mplayer.

This doesn't happen when I visit specific sites or anything - it's just very random.  Sometimes immediately when I open Firefox (trying to load /usr/share/ubuntu-artwork/home/index.html) and sometimes not until 30 minutes later when I click on a link.

I've been messing with stuff since I originally reported this problem (I didn't have mozplugger or mozilla-plugin-vlc installed earlier).  And I haven't had a lockup in 30 minutes or so now so maybe it's fixed now...  <shrug>

Anyhow, any ideas what could be (or could have been) causing it would be appreciated!

Thanks,
-Zak[/QUOTE]
 Are you by chance using an nvidia card with the nvidia drivers enabled?

---

### Post by ZakZak on 2005-04-20
[QUOTE=guyforget]Are you by chance using an nvidia card with the nvidia drivers enabled?[/QUOTE]

Yeah, Hoary's latest nvidia drivers and acceleration enabled in xorg.conf.

-Zak

---

### Post by vrunt on 2005-04-20
[QUOTE=ZakZak]Yeah, Hoary's latest nvidia drivers and acceleration enabled in xorg.conf.

-Zak[/QUOTE]

There's a HOWTO somewhere that addresses this issue.
Found it.
[http://ubuntuforums.org/showthread.php?t=26385](http://ubuntuforums.org/showthread.php?t=26385)
My system did the same thing.

---

### Post by guyforget on 2005-04-20
I figured....  start reading?  Really, theres not *that* much help out there for you...

[http://ubuntuforums.org/showthread.php?t=24703](http://ubuntuforums.org/showthread.php?t=24703)

[http://www.nvnews.net/vbulletin/showthread.php?t=31858&page=1](http://www.nvnews.net/vbulletin/showthread.php?t=31858&page=1)

I had the problem as well.  It mostly happened when using firefox, though on rare occasions it happened when firefox wasnt running.  Theres probably nothing in any of your logs, but it wouldnt hurt to sift through the syslog if you can remember the approx. time maybe.  

My problem seems to have cleared up, but Ive yet to mention it anywhere in fear of jinxing myself.  This would be the first mention of it publicly, actually...  

I was running my OS on a SATA drive that was actually mounted on the SATA2 connection on my mobo.  I went and bought a new hdd (best buy had a nice rebate - 120gb/8mb for 50$) and decided to install hoary from disc to it.  Before doing so I moved the SATA drive to the proper SATA1 port on my mobo.  After installing to the new hdd I installed the 686-smp kernel, rebooted, loaded the nvidia drivers, rebooted, and copied the rest of my stuff over from the old installation.  Im still going strong...  

Fingers crossed & Good luck to you...

---

### Post by guyforget on 2005-04-20
[QUOTE=vrunt]There's a HOWTO somewhere that addresses this issue.
Found it.
[http://ubuntuforums.org/showthread.php?t=26385](http://ubuntuforums.org/showthread.php?t=26385)
My system did the same thing.[/QUOTE]

This did not work for me....   But its worth a shot.  FWIW; I needed hdparm too, so uninstalling it wasnt very attractive of a solution...

---

### Post by Gustav on 2005-04-20
For me it worked to simply change the line in /etc/X11/xorg.conf that said:

RenderAccel "true"

to:

RenderAccel "false"

---

### Post by ZakZak on 2005-04-20
Okay, it just happened to me again with Firefox running.  I was just browsing Slashdot.  I hit PgDn to scroll down the page and it locked up (everything but the mouse cursor).

RenderAccel "false" may fix it, but it's not worth it...  I do too much on this laptop (Lots of GUI software development, VMware, etc) to get by with slow X. :)

Is it possible to switch back to xfree under Hoary?  Accelaration worked there... <grin>

-Zak

---

### Post by vtrac on 2005-04-20
[QUOTE=ZakZak]Okay, it just happened to me again with Firefox running.  I was just browsing Slashdot.  I hit PgDn to scroll down the page and it locked up (everything but the mouse cursor).

RenderAccel "false" may fix it, but it's not worth it...  I do too much on this laptop (Lots of GUI software development, VMware, etc) to get by with slow X. :)

Is it possible to switch back to xfree under Hoary?  Accelaration worked there... <grin>

-Zak[/QUOTE]
 Hmm.. Firefox is locking up on me as of yesterday as well.  I don't think I have done anything to firefox either.......  weirdly it locked up on Slashdot as well.

---

### Post by ZakZak on 2005-05-03
From what I can tell from reading these forums and on the Nvidia forums, this seems to be pretty common for users of XOrg, nVidia cards, and Firefox.  I just tried switching to Opera and although I made it 30 minutes without a problem, eventually the very same issue arose.  I could still move my mouse around, but couldn't click anything and the keyboard was completely useless (no VT switching - even caps lock wouldn't work).

I tried switching from the "nvidia" driver to the "nv" driver which means no acceleration.  Pretty much everything was fine (and Firefox ran for over an hour) until I tried to run rdesktop...  It was REALLY SLOW.  I use rdesktop quite a lot, so that just wasn't acceptable to me.

I'm still wondering if there's a way to downgrade the nvidia driver, downgrade the kernel, downgrade to xfree - SOMETHING that would make Hoary perform as well as Warty did for me on this machine...  Can anyone suggest anything at all?

Thanks,
-Zak

---

