---
title: "problems running &quot;Diablo II&quot;(game) under wine: no cd detected! :("
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by CC_machine on 2007-04-17
ok, so i'm having problems getting Diablo II running under wine. I recently switched to Debian Etch and followed this guide:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Diablo2](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Diablo2)
as it says, i installed the GLIDE3-to-OpenGL wrapper and got it to detect my video output properly:
[http://www.tu-harburg.de/~sisl0020/english/index.html](http://www.tu-harburg.de/~sisl0020/english/index.html)

installed, installed directx. However when i try to run it (by the d2.exe in ./drive_c/Program FIles/Diablo II/, or setup.exe on the cd!) it always complains that it cannot detect the cd! when i run it in a terminal, this happens:

[email]ccmachine@andrew-iii:~/.wine[/email]/drive_c/Program Files/Diablo II$ wine Diablo\ II.exe
Invoking /usr/lib/wine/wine.bin Diablo II.exe ...
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 7\Logical Unit Id 0
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!



i always get the "GLX missing" message when i try to wine the setup and other *.exes, and i have added "AIGLX" "on" in my xorg.conf under the relevant section, but it makes no difference. I've tried googling for many of my problems, nothing :(

Wine version: 0.9.25-2.1 from Synaptic
with libwine-gl, libwine-alsa, wine-utils, xwine packages from synaptic... i know my gfx is configured properly because i have [http://sauerbraten.org](http://sauerbraten.org) working properly with nvidia, opengl and SDL.

any suggestions? :(

---

### Post by molex on 2007-04-17
You might want to try a no-cd EXE. I'm not sure if I can tell you were to get one, but google should be pretty useful.

---

### Post by smutch on 2007-04-23
I am also getting this error:

err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0

Although I'm not running ubuntu on the machine I'm playing diablo on I have come across the can't find cd problem many times for different reasons. The most common one I think is that you need a symbolic link in .wine/dosdevices/ referencing your cdrom device as well as one to your cdrom mount point. 

So when I set my wine up I did a:
cd .wine/dosdevices/
ln -s /mnt/cdrom d:
and:
ln -s /dev/hda d::   (hda is my cdrom device)

Sometimes when I first start up my computer with the cd in I can access the cd but for some reason wine doesn't see it as mounted so I do a sudo umount /mnt/cdrom and then mount /mnt/cdrom

I've experimented with running 2 diablos at the same time, one running as the current user and the other running as a different user with different cd keys. When I run diablo as a different user it couldn't access the cdrom since the current user had control of it. So you could try changing the permissions of the mount point to allow others to read it. I did:

sudo chmod 666 /mnt/cdrom

I don't know anything about the GLX stuff. I have installed diablo on an older machine under ubuntu and had no problem getting diablo to run (although admittedly its runs impossible to play slow).

---

### Post by adza on 2007-04-27
i tried creating those links, however i'm still getting this error....



fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
adza@adza:~$ fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0



?? huh ??

---

### Post by cogadh on 2007-04-27
Not sure if this is relevant, but those instructions you followed say always use the latest Wine version, and you are using 0.9.25 while the latest is 0.9.35.

Additionally, If you have to current nVidia drivers (9755), why are you trying to use GLX? The nVidia driver already has excellent OpenGL support.

Lastly, have you tried running winecfg and having it automatically detect your drives?

---

### Post by adza on 2007-04-28
**bump**

---

### Post by adza on 2007-04-28
sometimes i hate myself for bumping like that.... nevermind.. i've found the solution to that problem spelled out quite clearly on the winehq site...  [http://appdb.winehq.org/appview.php?iVersionId=315&iTestingId=10553](http://appdb.winehq.org/appview.php?iVersionId=315&iTestingId=10553)

simply fixed following the correct setup in winecfg...

---

