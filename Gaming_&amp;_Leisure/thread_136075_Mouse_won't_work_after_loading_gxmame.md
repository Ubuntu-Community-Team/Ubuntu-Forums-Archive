---
title: "Mouse won't work after loading gxmame"
date: 2006-02-25
forum: Gaming &amp; Leisure
---

### Post by 8bit on 2006-02-25
Everytime I load gxmame my mouse dies. I have to restart x. It was working fine.

Any suggestions?

---

### Post by leech on 2006-02-25
That's kind of odd, what video card are you using?  Are you using xmame from Dapper or from Sid (I use the Sid packages because they are much newer (v0.101 as opposed to v0.86 that Dapper i386 has).  Are you using the newest gxmame .deb package?  

What I usually use is the xmame-sdl package from Debian Sid (you just need xmame-common and recommended is xmame-tools), then use CVS to download gxmame and then make a debian package by using 'sudo dpkg-buildpackage' in the gxmame directory.

If you need help with that, I can explain it in depth more.

By the way, I like your Avatar :D  Kind of like my Sig....

Leech

---

### Post by 8bit on 2006-02-25
[QUOTE=leech]That's kind of odd, what video card are you using?  Are you using xmame from Dapper or from Sid (I use the Sid packages because they are much newer (v0.101 as opposed to v0.86 that Dapper i386 has).  Are you using the newest gxmame .deb package?  

What I usually use is the xmame-sdl package from Debian Sid (you just need xmame-common and recommended is xmame-tools), then use CVS to download gxmame and then make a debian package by using 'sudo dpkg-buildpackage' in the gxmame directory.

If you need help with that, I can explain it in depth more.

By the way, I like your Avatar :D  Kind of like my Sig....

Leech[/QUOTE]

Thanks for the quick response.

I've burned many hours on my Intellivision back in the day.

My gxmame problem is strange. The only changes I've been making have been to the rom directories. I may try to manually edit the gxmame config file and remove some of the recent dir's I've added. I've got more roms than I know what to do with and some are unknowns, which may be causing the problem. But as soon as gxmame is displayed, my mouse dies, cursor freezes and I have to restart x. Below is what I'm currently using...

xmame-sdl_0.86-3_i386
gxmame_0.35beta2-1~breezy_i386

I'm using breezy of course.

Should I try the GL version of xmame. Maybe that would solve my problem.

Thanks again

---

### Post by leech on 2006-02-26
What I use is xmame-sdl from []("ftp://ftp.debian.org/debian/pool/non-free/x/xmame/xmame-sdl_0.101-1_i386.deb") along with xmame-tools, [ftp://ftp.debian.org/debian/pool/non-free/x/xmame/xmame-tools_0.101-1_i386.deb]("ftp://ftp.debian.org/debian/pool/non-free/x/xmame/xmame-tools_0.101-1_i386.deb") and gxmame from this package (see attached).  You should be able to just install these over what you currently have, though you may want to rm -r ~/.gxmame before you run gxmame to start with a fresh slate.

I keep my roms in /usr/share/games/xmame/roms, but make sure they are readable by your user (either chown them for you, or maybe even chgrp to games and add your user to the games group.)

You'll need to first extract the attachment then 'sudo dpkg -i' on the .deb of course.  Not sure why I can't attach just a .deb, since it's technically just an tar.gz or tar.bz2 anyhow...  meh.

Leech

---

### Post by 8bit on 2006-03-08
Well Leech,

I uninstalled and reinstalled gxmame, manually edited the gxmame config files and did a few other things as well. Now it's working again. I have a hunch (I need to test this) that the problem might stem from selecting to use my gamepad to control the gxmame interface. I switched it off and now things seem to work properly. I have a Gravis game pad. Which joystick selection should I use? I guess I'm too lazy to go check the kernel settings to see what's compiled in.

BTW: Have you tried to get Daphne working in linux? Any luck?

Thanks again for your help.

---

