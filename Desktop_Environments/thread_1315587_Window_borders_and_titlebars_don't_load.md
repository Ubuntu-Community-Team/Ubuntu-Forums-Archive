---
title: "Window borders and titlebars don't load"
date: 2009-11-05
forum: Desktop Environments
---

### Post by Jive Turkey on 2009-11-05
I kept my home partition intact when installing karmic and then reverting to jaunty.  I've deleted my .compiz folder since then but compiz/desktop effects arent loading correctly after logging in.  I have to reload compiz 2-3 times before I get my window borders back and am able to move windows away from the upper left corner of the screen.

Any ideas how to fix?

---

### Post by Jive Turkey on 2009-11-05
If its any help I found these log messages:
```
~$ cat /var/log/messages | grep segfault
Nov  4 01:21:50 plug1 kernel: [  870.511130] nautilus[4372]: segfault at 7f6cc30e5960 ip 00007f6cc30e5960 sp 00007fffd4dcacb8 error 14 in libpixbufloader-png.so[7f6cc950b000+4000]
Nov  4 08:48:54 plug1 kernel: [26760.182310] nautilus[4725]: segfault at 7f0e6d721960 ip 00007f0e6d721960 sp 00007fff298763b8 error 14 in icon-theme.cache[7f0e727ab000+9855000]
Nov  4 16:40:55 plug1 kernel: [55080.483191] compiz.real[18381]: segfault at 7fc8ac3d3170 ip 00007fc8ac3d3170 sp 00007fffc25732e8 error 14 in libresizeinfo.so[7fc8ac5d8000+6000]
Nov  4 17:48:23 plug1 kernel: [59128.529524] nautilus[15739]: segfault at 7f7a15d20960 ip 00007f7a15d20960 sp 00007fff1f355638 error 14 in libpixbufloader-png.so[7f7a1c146000+4000]
Nov  4 18:18:40 plug1 kernel: [ 1275.557000] nautilus[4645]: segfault at 7f45a49fc960 ip 00007f45a49fc960 sp 00007fffba649f68 error 14 in icon-theme.cache[7f45aa7ab000+9855000]
Nov  5 14:59:56 plug1 kernel: [  717.098593] nautilus[4884]: segfault at 7f466ec6b960 ip 00007f466ec6b960 sp 00007fffffd3add8 error 14 in icon-theme.cache[7f46727ab000+9855000]
Nov  5 15:02:08 plug1 kernel: [  848.927631] nautilus[7078]: segfault at 7f454b4f2960 ip 00007f454b4f2960 sp 00007fff3a28cba8 error 14 in icon-theme.cache[7f454e7ab000+9855000]
Nov  5 15:15:06 plug1 kernel: [ 1627.471808] nautilus[8816]: segfault at 7f3e8584d960 ip 00007f3e8584d960 sp 00007fff6d2b40d8 error 14
Nov  5 15:16:41 plug1 kernel: [ 1722.026040] nautilus[10306]: segfault at 7f6c099a0960 ip 00007f6c099a0960 sp 00007fff131f3238 error 14 in libpixbufloader-png.so[7f6c0fdc6000+4000]
Nov  5 15:39:55 plug1 kernel: [ 3116.719316] nautilus[12441]: segfault at 7f9601fdf960 ip 00007f9601fdf960 sp 00007fff56d9a5f8 error 14 in libpixbufloader-png.so[7f9608405000+4000]

```
So maybe its not compiz after all, if I change the setting in "appearance" under system>preferences>appearance to no effects there is still no window borders (and no keyboard) after logging in.

---

### Post by Claus7 on 2009-11-20
Hello,

9 out of 10, there were no windows borders after loading in Karmic 9.10. In order to avoid that I had to log out and log in back again.
 
Searching a little I found that this was a known bug:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1771891.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1771891.html)

and searching even more, I think that this is the solution (I tried it and booted and my windows' borders are ok):
[http://ubuntuforums.org/showthread.php?t=1220164](http://ubuntuforums.org/showthread.php?t=1220164)

So I edited this file as root:
sudo vi /etc/xdg/openbox/autostart.sh

and placed a & in the line:
/usr/lib/openbox/xdg-autostart $DESKTOP_ENV &

which is the one, just before the last line.

Regards!

---

### Post by Claus7 on 2010-04-21
Hello,

the thing with the upgrading of the kernels remained as a problem so a solution I tried was to modify my xorg.conf file. Since then, and now in lucid I have not faced such a thing.

What I did was to add the lines:
Section "DRI"
Mode 0666
EndSection

and
Option "RenderAccel" "true"

under
Section "Device"

I had found somewhere that this had to do with compiz (I have it enabled) so this seems to work. I had made at least ten log out and log ons along with restarts without any problem so far.

Regards!

PS: These lines were there in previous xorg.conf files, yet somehow during upgrade or tampering they might have disappeared.

EDIT: Option      "AddARGBGLXVisuals" "true"
adding this line as well under the section Device

---

### Post by Claus7 on 2011-10-11
Hello,

for maverick I had to follow the solution of creating a new start up application as stated here: [http://ubuntuforums.org/showpost.php?p=9480918&postcount=40](http://ubuntuforums.org/showpost.php?p=9480918&postcount=40)

Really annoying that this bug resulted in ~30% of the time the borders not to load!

Regards!

---

