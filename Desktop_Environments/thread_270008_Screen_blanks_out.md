---
title: "Screen blanks out"
date: 2006-10-02
forum: Desktop Environments
---

### Post by gmhains on 2006-10-02
I am truely a newbie with Ubuntu. I have installed version 6.06 on my Toshiba Portege 3110CT laptop. Installation went smooth and everything works fine EXCEPT my screen goes blank every minute or so.

I have changed the power management to Never but it has no effect.  The system keeps running and as soon as I touch a key, the screen turns on again.  Can any body help


The laptop is a 
PII 300
192K Ram
Integrated Trident graphics
Intel 82440MX Power Management

Any help would be appreciated....
Many thnx

geoff

---

### Post by wpshooter on 2006-10-02
Did you install from a CD that Ubuntu mailed to you or from one that you downloaded & burned ?

Do you know if your version is 6.06 or 6.06.1 ?

Have you went into **UPDATE MANAGER** and installed all available updates ?

---

### Post by orb9220 on 2006-10-02
> I have changed the power management to Never but it has no effect. The system keeps running and as soon as I touch a key, the screen turns on again. Can any body help

This is a well known problem. If you want to see what xserver has set then open a term and enter xset -q and post here.

---

### Post by gmhains on 2006-10-03
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

---

### Post by gmhains on 2006-10-05
Me bad....  I found out that my laptop has a BIOS setting for the screen time out.  Although Windows 2000 would override this default, Ubuntu did not.  I have changed my BIOS and the screen doesn't blank out anymore.  But then again the power managent still does not work but I can live with this.

I still love Ubuntu much better than W2K and I don't regret converting my laptop...

Thanks to everyone who tried to help
geoff

---

### Post by petit_prince on 2007-01-05
I know this is an old thread, but anyways:


To get your power management working, make sure you install the latest BIOS update. Grab a copy of it here:
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=120404&ct=DL](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=120404&ct=DL)
I believe the BIOS my 3110ct was shipped with didn't support only had Support for APM, not for ACPI.

BTW: Recently I haven't been able to bring my 3110ct back from standby (although suspend-to-disk still works) -- even installing the fixed x.org-Server from [https://launchpad.net/ubuntu/+source/xorg-server/+bug/61746](https://launchpad.net/ubuntu/+source/xorg-server/+bug/61746) didn't do the job. Do you happen to have the same problem or even a solution for this? I am running Edgy.

---

### Post by BarakNaveh on 2007-04-06
I have 3110CT without CD nor floppy. Any idea of how to apply the BIOS update for the power management? 

BTW, suspend and hibernate works well in WinXP, but it doesn't work for me on Ubuntu (6.10).

---

