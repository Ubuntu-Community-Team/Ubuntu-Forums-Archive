---
title: "Some Considerations AMD64 3DGames"
date: 2005-05-01
forum: Gaming &amp; Leisure
---

### Post by savage on 2005-05-01
Ok so with the help of these forums and some others I was able to finally get my ATI 9600 XT AIW to put out 3d acceleration.
[ATI 3d Guide](http://ubuntuforums.org/showthread.php?t=24557) 

Was able to get Enemy Territory running without having to chroot it.
[Enemy Territory under AMD64](http://ubuntuforums.org/showthread.php?t=19843&page=2&pp=10)

One issue I have had and I believe others as well is that you will be unable to change your Screen Resolution via the System > Preferences interface. I was unable to get the ATI control panel to run under Linux. Not sure if there is more that I can do to fix this. Also I think this will put you in a situation with Enemy Territory where you will be unable to set resolution or change gamma via the in game settings. If someone has a workaround especially for increasing the gamma I would like to know about it.

*Note this is an issue that is related to not using fglrxconfig to create your xorg.conf file. If you were able to successfully do so you probably don't have this issue. However if like me you looked at the XFree86 file that fglrxconfig creates and figured it was a bit to beefy, you will need to modify your xorg.conf file. Go [here](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html) and look for the area on "omit xfree86-dga". Some servers responed to me unkindly after this due to this change.

Was also able to install and run Unreal Tournament 2004. One stumbling block was wiith the libSDL-1.2.so.0 file after patching, to fix this I followed these directions [here](http://www.unrealadmin.org/forums/showthread.php?t=7507).The biggest issue is that after patching the game I was unable to connect to the master server and thus unable to enjoy Multiplayer. The only thing I could find concerning master server timeout was at this [site](http://www.sh.nu/lgfaq/#ut2k4amd64net).

*Note this master server timeout problem went away when I logged in the next day. I don't think it was anything I did.

I wish anyone who is trying to get gaming under Linux to work the best of luck. Keep in mind that laying off any problems you may have and then returning later often yields results better than banging against the monitor for hours/days on end. AMD64 people I just wanted to let you know about the issues I had from above. The games work fine, and UT2004 looks superb, but at this point I have a bit to go before I am happy with my setup.

---

