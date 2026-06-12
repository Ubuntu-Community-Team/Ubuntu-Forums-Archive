---
title: "[SOLVED] Emerald is installed but doesn't exist"
date: 2008-12-17
forum: General Help
---

### Post by kian.tern on 2008-12-17
Hi,
I have this weird issue. 
I just updated my 8.10 and after reboot emerald is gone.
It doesn't show in fusion-icon and is not anywhere in my $PATH.
I suppose it should be in /usr/bin, but it's not there.
The weirdest thing is the package is installed. I tried to reinstall it without any result. 
Just in case I switched apt to a different mirror and reinstalled but the problem remains.
Compiz-fusion works well.

Any help will greatly appreciated (gtk-decorator drives me mad :lolflag:)

---

### Post by eternalnewbee on 2008-12-17
Have you tried: Press ALT-F2 and enter ```
compiz --replace
``` and then press ALT-F2 and enter```
emerald --replace
```

---

### Post by kian.tern on 2008-12-17
eternalnewbee, that was the first thing I did.
I just checked on my home system, emerald executable is installed in /usr/bin. On the PC at work emerald isn't there. In addition I took apart the emerald_0.7.2-0ubuntu3_i386.deb and I can't find the executable inside either.

---

### Post by eternalnewbee on 2008-12-17
What message do you get if you enter these commands in the terminal?

---

### Post by kian.tern on 2008-12-17
I don't mean to be rude, but did you read the posts?
In the first post I said file /usr/bin/emerald doesn't exist,
allthough the package is installed. reinstalling doesn't help.

---

### Post by js_fr on 2008-12-17
I just de- and reinstalled emerald on my test machine using the intrepid main server (line in /etc/apt/sources.list: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe )
Works fine, /usr/bin/emerald is there. 

What is the output of: 
```
dpkg -L emerald | grep /usr/bin
```

---

### Post by kian.tern on 2008-12-17
I tried again.

Removed emerald
    > apt-get remove --purge emerald
Changed the repository to Main in System->administration->software sources
Rebuilt APT database
    ```
apt-get update
```
Removed APT cache
    ```
rm -rf /var/cache/apt/archives/*.deb
```
Installed emerald
    ```
apt-get install emerald
```

the problem is still there :confused:

```
dpkg -L emerald
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/emerald
/usr/share/doc/emerald/TODO
/usr/share/doc/emerald/NEWS.gz
/usr/share/doc/emerald/copyright
/usr/share/doc/emerald/changelog.Debian.gz
/usr/share/doc/emerald/AUTHORS
/usr/share/doc/emerald/README
```

---

### Post by kian.tern on 2008-12-17
SOLVED.
For some reason I had a weird entry in sources.list which caused all the troubles. I removed it, reinstalled emerald, now every thing works.

---

### Post by HuaiDan on 2008-12-17
Good, so you're someone I can ask. Do you have to keep an open terminal session running to keep emerald effects up? If I close the terminal or ^C, effects go away and I lose all window functions until I restart emerald. It annoys me. Is it normal or can I fix it?

---

### Post by eternalnewbee on 2008-12-17
Glad to see you solved your problem. Remember to mark the thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

### Post by kian.tern on 2008-12-17
> **HuaiDan said:**
> Good, so you're someone I can ask. Do you have to keep an open terminal session running to keep emerald effects up? If I close the terminal or ^C, effects go away and I lose all window functions until I restart emerald. It annoys me. Is it normal or can I fix it?

You can do several things.
1. Go to System->Preferences->Sessions
   add to startup programs 2 entries.
   "compiz --replace"
   "emerald --replace"
2. Install fusion-icon
   Set your configuration in fusion icon.
   Add fusion-icon to startup programs in Sessions window.
3. Press Alt+F2
   Type "compiz --replace" Enter.
   Press Alt+F2 again
   Type "emerald --replace" Enter.

The first 2 will start compiz and emerald on session start up
The third if you want to start it manually.

My own preference is to start automaticly via fusion-icon.
It provides the option to restart emerald/compiz.
So if compiz or emerald crash you can restart it with one click.

Hope it helps.

---

