---
title: "Firefox issue"
date: 2009-04-04
forum: General Help
---

### Post by magawake on 2009-04-04
I just downloaded firefox 3.0 from the website 
[http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0.8&os=linux&lang=en-US]("http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0.8&os=linux&lang=en-US")

I bunzip and untared it 
```

$ pwd
/tmp/firefox
$ ./firefox
./run-mozilla.sh: 442: ./firefox-bin: not found

```
has anyone seen this before?

---

### Post by ShaunG on 2009-04-04
You can install firefox 3.0 from add/remove, synaptics or command line.

Search in add/remove for firefox, or in Synaptics package manager or
in a command line type:

```
sudo apt-get install firefox-3.0
```

---

### Post by paradigm2 on 2009-04-04
> **magawake said:**
> I just downloaded firefox 3.0 from the website 
[http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0.8&os=linux&lang=en-US]("http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0.8&os=linux&lang=en-US")

I bunzip and untared it 
```

$ pwd
/tmp/firefox
$ ./firefox
./run-mozilla.sh: 442: ./firefox-bin: not found

```
has anyone seen this before?

It's up tp ypu if you have special reasons for wanting to manually download the original firefox version, but Ubuntu has the latest Fx 3.0.8 available in the repositories.

System -> Administration -> Synaptic

Type in firefox where it says quick search.

Hover over the box near where it says Firefox.

Right click

Choose "Mark for installation"

Choose okay if it wants to mark other things.

Once back to the familiar menu, Click Apply.

That's it.  Its done.

Find it in Applications -> Internet.

---

### Post by magawake on 2009-04-04
> **paradigm2 said:**
> It's up tp ypu if you have special reasons for wanting to manually download the original firefox version, but Ubuntu has the latest Fx 3.0.8 available in the repositories.

System -> Administration -> Synaptic

Type in firefox where it says quick search.

Hover over the box near where it says Firefox.

Right click

Choose "Mark for installation"

Choose okay if it wants to mark other things.

Once back to the familiar menu, Click Apply.

That's it.  Its done.

Find it in Applications -> Internet.

Yes. I know I can install it via synaptic but I get "Grand Paridiso" which is very unstable. I prefer I get the actual firefox binary which I did but I keep getting this annoying ```

$ ./firefox
./run-mozilla.sh: 389: ./firefox-bin: not found

```

problem.

---

### Post by taurus on 2009-04-04
What's the output of this command?

```
ls -la /tmp/firefox
```
By the way, it's not a good idea to unpack firefox in /tmp since everything in /tmp will be wiped clean the next time you boot/reboot.  If you want to unpack it, do it in your $HOME.

---

### Post by magawake on 2009-04-05
> **taurus said:**
> What's the output of this command?

```
ls -la /tmp/firefox
```
By the way, it's not a good idea to unpack firefox in /tmp since everything in /tmp will be wiped clean the next time you boot/reboot.  If you want to unpack it, do it in your $HOME.

```

total 25952
drwxr-xr-x 14 appgtk appgtk     4096 2009-04-04 11:32 .
drwxrwxrwt 18 root   root       4096 2009-04-05 07:35 ..
-rw-r--r--  1 appgtk appgtk     2025 2008-05-29 16:21 application.ini
-rw-r--r--  1 appgtk appgtk        0 2008-05-29 16:19 .autoreg
-rwxr-xr-x  1 appgtk appgtk      981 2008-05-29 16:21 blocklist.xml
-rw-r--r--  1 appgtk appgtk      232 2008-05-29 16:19 browserconfig.properties
drwxr-xr-x  3 appgtk appgtk     4096 2008-05-29 16:21 chrome
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:21 components
-rwxr-xr-x  1 appgtk appgtk    45096 2008-05-29 16:21 crashreporter
-rw-r--r--  1 appgtk appgtk     3558 2008-05-29 16:21 crashreporter.ini
-rw-r--r--  1 appgtk appgtk      583 2008-05-29 16:21 crashreporter-override.ini
drwxr-xr-x  5 appgtk appgtk     4096 2008-05-29 16:21 defaults
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:21 dictionaries
drwxr-xr-x  3 appgtk appgtk     4096 2008-05-29 16:21 extensions
drwxr-xr-x 13 appgtk appgtk     4096 2009-04-04 11:32 firefox
-rw-r--r--  1 appgtk appgtk  9763335 2009-04-04 11:31 firefox-3.1b3.tar.bz2
-rwxr-xr-x  1 appgtk appgtk     7476 2008-05-29 16:21 firefox-bin
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:21 greprefs
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:21 icons
-rw-r--r--  1 appgtk appgtk      476 2008-05-29 16:21 libfreebl3.chk
-rwxr-xr-x  1 appgtk appgtk   292340 2008-05-29 16:21 libfreebl3.so
-rwxr-xr-x  1 appgtk appgtk    30724 2008-05-29 16:21 libjemalloc.so
-rwxr-xr-x  1 appgtk appgtk   602680 2008-05-29 16:21 libmozjs.so
-rwxr-xr-x  1 appgtk appgtk   200736 2008-05-29 16:21 libnspr4.so
-rwxr-xr-x  1 appgtk appgtk   913844 2008-05-29 16:21 libnss3.so
-rwxr-xr-x  1 appgtk appgtk   304640 2008-05-29 16:21 libnssckbi.so
-rwxr-xr-x  1 appgtk appgtk   119588 2008-05-29 16:21 libnssdbm3.so
-rwxr-xr-x  1 appgtk appgtk    77564 2008-05-29 16:21 libnssutil3.so
-rwxr-xr-x  1 appgtk appgtk    13224 2008-05-29 16:21 libplc4.so
-rwxr-xr-x  1 appgtk appgtk     8684 2008-05-29 16:21 libplds4.so
-rwxr-xr-x  1 appgtk appgtk   125676 2008-05-29 16:21 libsmime3.so
-rw-r--r--  1 appgtk appgtk      476 2008-05-29 16:21 libsoftokn3.chk
-rwxr-xr-x  1 appgtk appgtk   181776 2008-05-29 16:21 libsoftokn3.so
-rwxr-xr-x  1 appgtk appgtk   397668 2008-05-29 16:21 libsqlite3.so
-rwxr-xr-x  1 appgtk appgtk   160036 2008-05-29 16:21 libssl3.so
-rwxr-xr-x  1 appgtk appgtk    11816 2008-05-29 16:21 libxpcom.so
-rwxr-xr-x  1 appgtk appgtk 12962304 2008-05-29 16:21 libxul.so
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:21 modules
-rwxr-xr-x  1 appgtk appgtk    10772 2008-05-29 16:21 mozilla-xremote-client
-rw-r--r--  1 appgtk appgtk      112 2008-05-29 16:19 old-homepage-default.properties
-rw-r--r--  1 appgtk appgtk       41 2008-05-29 16:21 platform.ini
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:21 plugins
-rw-r--r--  1 appgtk appgtk      177 2008-05-29 16:21 README.txt
-rwxr-xr-x  1 appgtk appgtk    15767 2008-05-29 16:19 removed-files
drwxr-xr-x  6 appgtk appgtk     4096 2008-05-29 16:21 res
-rwxr-xr-x  1 appgtk appgtk    11410 2008-05-29 16:21 run-mozilla.sh
drwxr-xr-x  2 appgtk appgtk     4096 2008-05-29 16:19 searchplugins
-rw-r--r--  1 appgtk appgtk      825 2008-05-29 16:21 Throbber-small.gif
-rwxr-xr-x  1 appgtk appgtk    69672 2008-05-29 16:21 updater
-rw-r--r--  1 appgtk appgtk      144 2008-05-29 16:19 updater.ini

```

---

### Post by taurus on 2009-04-05
How about

```
ls -la /tmp/firefox/firefox
```

---

