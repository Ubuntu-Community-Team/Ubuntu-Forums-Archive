---
title: "server x nolisten"
date: 2010-10-07
forum: Desktop Environments
---

### Post by lain80 on 2010-10-07
$ uname -a
Linux mauri-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
I'm maverik 10.10, and I want to delete " -nolisten tcp " on my x server
Ho la versione 10.10, vorrei togliere l'indicazione -nolisten
root       1719  1716  9 09:43 tty7     00:24:24 /usr/bin/X :0 -br -verbose  -auth /var/run/gdm/auth-for-gdm-IE6iSq/database -nolisten tcp vt7
from this: [http://davesource.com/Solutions/20070912.Ubuntu-xhost.html](http://davesource.com/Solutions/20070912.Ubuntu-xhost.html)
```

   1.   Edit /etc/X11/xinit/xserverrc:
      Remove the "-nolisten tcp"
   2. Edit /etc/gdm/gdm.conf:
      Comment out the "DisallowTCP=true" so that it doesn't add the -nolisten back.
   3. Really restart X
      The easiest way is to probably kill gdm and then restart it from a text login:
      /etc/init.d/gdm stop
      At a text login:
      /etc/init.d/gdm start 


```I can't find step 2... how I can do this?
```

find  /etc/ -type f -exec grep DisallowTCP {} \; -print
      <key>security/DisallowTCP</key>
/etc/gdm/gdm.schemas


```many thanks for any support.
Cheers,
Lain

---

### Post by seewer on 2010-11-24
in /etc/gdm/curtom.conf put in

```

[security]
DisallowTCP=false

```

---

### Post by Errorinspelling on 2010-11-29
Ok don't know about the curtom.conf file but I found that by editing the /etc/gdm/gdm.schemas I went to this particular section and changed the true to false

```

<schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>false</default>
</schema>

```

After that I rebooted. did a ```
ps -ef | grep X
```  and verified that X was no longer being launched with the -nolisten option.

I am presuming the XML for GDM config is in preparation for some really cool app to easily modify your gdm setting. 

Enjoy ya'll!

---

