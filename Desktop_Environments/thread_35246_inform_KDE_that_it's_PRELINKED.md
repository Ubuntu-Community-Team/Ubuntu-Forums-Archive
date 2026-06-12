---
title: "inform KDE that it's PRELINKED"
date: 2005-05-18
forum: Desktop Environments
---

### Post by suoko on 2005-05-18
Hi,
I read on a gentoo forum that kde can be informed it's been prelinked thus causing a further increase in loading speed.(kdeinit won't be run anymore)
It says to write the line KDE_IS_PRELINKED="true" in etc/envnv.d//99kde-env.
Where can I write it in ubuntu?

---

### Post by lao_V on 2005-05-18
[QUOTE=suoko]Hi,
I read on a gentoo forum that kde can be informed it's been prelinked thus causing a further increase in loading speed.(kdeinit won't be run anymore)
It says to write the line KDE_IS_PRELINKED="true" in etc/envnv.d//99kde-env.
Where can I write it in ubuntu?[/QUOTE]

The way I have this configured at the moment is by adding the following script to the Autostart directory (/home/user/.kde/Autostart) and giving it execute permission

 ```
#!/bin/bash

kde --prelink
``` 

to give write permission:

 ```
chmod u+x scriptname.sh
```

konqueror loads up ligtingly fast after this!

---

### Post by suoko on 2005-05-18
unfortunately I do not have any kde binary installed...

---

### Post by lao_V on 2005-05-18
[QUOTE=suoko]unfortunately I do not have any kde binary installed...[/QUOTE]

Then what do u want to use kde prelink for? Are you not running KDE?

---

### Post by suoko on 2005-05-18
i do have kde but have no /usr/bin/kde executable.
I have kdeinit. do I try "kdeinit --prelink"?

However, I now have a strange error report when trying general prelink.

After having set PRELINKING=yes in /etc/default/prelink
I have tryed three times the command:
"sudo /etc/cron.daily/prelink".
I took a long time to process but each time exited with this error:
*****************
cron.daily/prelink: line 53: 24727 Segmentation fault      /usr/sbin/prelink -av $PRELINK_OPTS >>/var/log/prelink.log 2>&1
******************

I have tried removing /var/log/prelink.log but nothing changes.

I'm using kde on an ubuntu install. When I was using gnome, prelink worked fine, then I disabled it before installing kde. Now that I want prelinking againg it fails.
Any hints?

---

### Post by suoko on 2005-05-18
FORGOT TO POST this results:

sudo tail /var/log/prelink.log
Password:
Prelinking /sbin/nstat
Prelinking /usr/bin/kwrapper
Prelinking /usr/bin/yuvkineco
Prelinking /usr/bin/kstart
Prelinking /usr/bin/ximian-connector-setup-2.2
Prelinking /usr/bin/mppdec
/usr/sbin/prelink.bin: /usr/bin/mppdec: Symbol section index outside of section numbers
free(): invalid pointer 0xb7e81c00!
free(): invalid pointer 0xb7e81c40!
Prelink failed with return value 139

---

### Post by lao_V on 2005-05-18
what happens if you type kde --prelink in terminal?

---

### Post by suoko on 2005-05-18
Here what happens:
kde --prelink
bash: kde:  command not found

I tried doing "apt-get install kde" but it  says everything is already installed

AND here is a kde [TAB] 

xxxxx@ubuntu:/etc $ kde
kdebugdialog       kdeeject           kdekillall         kdeprintfax        kdesu_stub         kdevprj2kdevelop
kde-build          kdeinit            kdelnk2desktop.py  kdesktop           kdevassistant      kdevprofileeditor
kde-config         kdeinit_shutdown   kdemangen.pl       kdesktop_lock      kdevdesigner
kded               kdeinit_wrapper    kde-menu           kdesu              kdevelop3
kdedoc             kdeinstallktheme   kdepasswd          kdesud             kdevelop-htdig

---

