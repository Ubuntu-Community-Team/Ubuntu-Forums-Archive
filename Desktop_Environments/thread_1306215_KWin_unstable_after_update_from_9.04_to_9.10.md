---
title: "KWin unstable after update from 9.04 to 9.10"
date: 2009-10-30
forum: Desktop Environments
---

### Post by tomarctus on 2009-10-30
Hello!
Could someone help me with my problem? I haven't found any solutions.... >_>
Also my problem:
I have upgraded my Kubuntu 9.04 to 9.10, everything was fine, but after restart (using kernel 2.6.31-14, the newest one) and the login, I see a window, that tells me that KWin is unstable, it has frozen often, and I should chose another windowing system... what I, of course don't have. ^^"
I'm now using kernel 2.6.28-16, and it works...... although I don't  have any sound....
My system is completely updated, I'm using my laptop, with ATI Mobility Radeon HD 3470 video card, and the Catalyst driver (9.10).
Any help please?

---

### Post by MarcoPau on 2009-10-30
I'm having the same problem with older 2.6.28.

kwin: ../../src/xcb_io.c:542: _XRead: Assertion 'dpy->xcb->reply_data != ((void *)0)' failed.

---

### Post by tomarctus on 2009-10-30
Yeah. I have the same thing, except that I have some Hungarian in it. ^^
/ "kijelentés meghiúsult" == "failed" /
It was quite hard to get this output without having keyboard input on my terminal. :D

> tomarctus@Stray-Wolf:~$ kwin
kwin: ../../src/xcb_io.c:542: _XRead: A(z) „dpy->xcb->reply_data != ((void *)0)” kijelentés meghiúsult.
Application::crashHandler() called with signal 6; recent crashes: 1
KCrash: Application 'kwin' crashing...
Félbeszakítva (memória kiírás)
tomarctus@Stray-Wolf:~$ kwin: ../../src/xcb_io.c:542: _XRead: A(z) „dpy->xcb->reply_data != ((void *)0)” kijelentés meghiúsult.
Application::crashHandler() called with signal 6; recent crashes: 2
KCrash: Application 'kwin' crashing...
kwin: ../../src/xcb_io.c:542: _XRead: A(z) „dpy->xcb->reply_data != ((void *)0)” kijelentés meghiúsult.
Application::crashHandler() called with signal 6; recent crashes: 3
KCrash: Application 'kwin' crashing...
kwin: ../../src/xcb_io.c:542: _XRead: A(z) „dpy->xcb->reply_data != ((void *)0)” kijelentés meghiúsult.
Application::crashHandler() called with signal 6; recent crashes: 4
KCrash: Application 'kwin' crashing...
Any ideas how I could change this? >.>

---

### Post by MarcoPau on 2009-10-30
Hey I got it! Erase your Ati drivers (sudo sh /usr/share/ati/fglrx-uninstall.sh) then reinstall with sudo sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic. Then install all deb packages and do /usr/bin/aticonfig --initial. Reboot.

Let me know.

---

### Post by tomarctus on 2009-10-30
Wooww......
I don't know how... but it's working..... :D
10/10. :)
Thanks. =D> It was a great help.

---

### Post by sgk111 on 2009-10-30
[size=5][color=blue]w
[/color][/size]

---

### Post by MarcoPau on 2009-10-30
You're welcome tomarctus. It's been a pain in the *** for me too, but luckily a little tweaking has helped.

---

### Post by lophiomys on 2009-11-01
Same here on a Thinkpad T42p with ATI FireGL T2
I went trhough all betas of Karmic Koala 9.10 without major problems (except for the Wireless not working).
Graphics performance was poor, so I decided to install the fglrx - ATI drivers via the KPackageKit.

On reboot, KWin was reported to be unstable. 
The KDE crash report did not accecpt the available backtrace data. 
I could not remove the fglrx-packages via KPackagekit or via
Konsole-Terminal because the keyboard would not function anymore. The whole system is rendered unsuable now, because in crucial places keyboard input is not working and the title bar of al GUI windows has disappeard. 

I managed to install the debug symbols for KDELibs5-dbg (did not find any for KWin), but 
even then I could not get sufficient backtracing information for
the KDE crash handler. 

:(

---

### Post by keyser.kovacs on 2009-11-02
Hi, I think this could solve my issue with Ubuntu 9.10 becuase I have issues with screen in my ATI Radeon. But I don't understand completely your third step. When you say ..."Then install all deb packages ..." Where I have to do that? Could you provide me more details.

Sorry but I am very new with Linux.

Thanks in advance!!


> **MarcoPau said:**
> Hey I got it! Erase your Ati drivers (sudo sh /usr/share/ati/fglrx-uninstall.sh) then reinstall with sudo sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic. Then install all deb packages and do /usr/bin/aticonfig --initial. Reboot.

Let me know.

---

### Post by fireman300 on 2009-11-09
OK so I waited a bit to install the FGLRX driver because of issues in the past and it seems I've missed the boat. If you have an older ATI card specifically the ATI Radeon Series you MUST use a legacy driver from ATI. 

From the ATI site: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English")> The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Any customers using a combination of a ATI Radeon™ HD 2000 Series, ATI Radeon™ HD 3000 Series, or ATI Radeon™ HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst™ releases made available past the ATI Catalyst™ 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

This means that the version currently in the Karmic Repository is NG no good for folks like myself and a few of the other posters. My only inclination is to try compiling with Jaunty and seeing if it will work.

---

### Post by a_flj_ on 2010-01-07
> **keyser.kovacs said:**
> "Then install all deb packages ..."

I had the same problem, am a complete newbie, and the solution worked for me - with a small difference: I used the .run file from ati's web site, instead of installing the driver via package manager.

You can't imagine how happy I am now. I only found this thread after damaging my installation four times, and reinstalling from scratch.

One more difference: I did no upgrade, I installed kubuntu 9.10 from scratch.

I did no reinstall of any other package whatsoever, and it worked. Did I miss something? Is this install of .deb packages related to the upgrade which I didn't perform? Should I do something more for some reason I don't get yet? Or is it safe and reliable to just use it if it works?

---

### Post by spot-da-haze on 2010-02-03
yeah i did a reinstall in the end i lost all keybored control ... so how should i install the ATI stuff with out killing Kwin??

---

