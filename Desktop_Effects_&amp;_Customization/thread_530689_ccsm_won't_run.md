---
title: "ccsm won't run"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by samkline on 2007-08-20
hi,

I've been running beryl for a while now but decided to switch to compiz-fusion. i installed that, and it works with the default settings, but i can't get CCSM (compiz config) to run.

here's the error i get when attempting to run ccsm:```
sam@SAM-UBUNTU-X64:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 42, in <module>
    context = ccs.Context(screens)
  File "compizconfig.pyx", line 830, in compizconfig.Context.__new__
  File "compizconfig.pyx", line 881, in compizconfig.Context.UpdateProfiles
KeyError: ''

```
note i'm using 64bit ubuntu feisty. i've got all the dependencies installed but can't get this to work. i've searched google and these forums but can't find a solution.

can anyone help me? thanks!

---

### Post by kunjan1029 on 2007-08-20
install "libcompizconfig" and "libcompizconfig-dev" packages and give it a shot. See if that help. Worked for me.

---

### Post by samkline on 2007-08-20
> **kunjan1029 said:**
> install "libcompizconfig" and "libcompizconfig-dev" packages and give it a shot. See if that help. Worked for me.i'd already had libcompizconfig installed, but i just installed libcompizconfig-dev and it didn't help.

any other suggestions?

---

### Post by kabturek on 2007-08-21
yep got the same problem and the solution didnt work for me too :/

after the instalation of this packeges the error changed a little :
```

kabturek@hal-9000:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 42, in <module>
    context = ccs.Context(screens)
  File "compizconfig.pyx", line 830, in compizconfig.Context.__new__
  File "compizconfig.pyx", line 881, in compizconfig.Context.UpdateProfiles
KeyError: '/schemas/apps/metacity/keybinding_commands/command'

```

---

### Post by 1900 on 2007-10-23
I was able to correct the problem after my upgrade to Gusty by removing old files from precious beryl and compiz installs.  (I had installed and built compiz - or failed to remove beryl and compiz as 'instructed', or installed from 'other' repos in order to get the latest and greater etc)

These files existed in/under /usr/local 

I moved them to another dir (in case I screwed anything else up)

Below is a listing of the files/dir I moved out of /usr/loca (/usr/local/bin, /usr/local/applications, etc)

I think the ccsm issues stem from the /usr/local/lib files

applications:
total 24
drwxr-xr-x 2 root root 4096 2007-10-22 21:53 .
drwxr-xr-x 8 root root 4096 2007-10-23 08:18 ..
-rw-r--r-- 1 root root  194 2007-06-06 22:21 ccs-settings.desktop
-rw-r--r-- 1 root root  394 2007-07-31 23:22 emerald-theme-manager.desktop
-rw-r--r-- 1 root root  154 2007-10-22 21:53 mimeinfo.cache
-rw-r--r-- 1 root root 1246 2007-07-21 14:16 opera.desktop

bin:
total 1484
drwxr-xr-x 2 root root   4096 2007-10-22 23:33 .
drwxr-xr-x 8 root root   4096 2007-10-23 08:18 ..
lrwxrwxrwx 1 root root     53 2007-08-01 22:46 ccsm.mm -> /i386_704/home/matthew/source/compiz-fusion/ccsm/ccsm
-rwxr-xr-x 1 root root 148118 2007-06-06 22:21 ccs-settings
-rwxr-xr-x 1 root root 978900 2007-07-31 23:20 compiz.00
-rwxr-xr-x 1 root root 237083 2007-07-31 23:22 emerald
-rwxr-xr-x 1 root root 123479 2007-07-31 23:22 emerald-theme-manager

etc:
total 12
drwxr-xr-x 3 root root 4096 2007-10-23 00:13 .
drwxr-xr-x 8 root root 4096 2007-10-23 08:18 ..
drwxr-xr-x 3 root root 4096 2007-06-06 21:32 gconf

include:
total 24
drwxr-xr-x 6 root root 4096 2007-10-23 00:12 .
drwxr-xr-x 8 root root 4096 2007-10-23 08:18 ..
drwxr-xr-x 2 root root 4096 2007-06-06 22:27 ccs
drwxr-xr-x 2 root root 4096 2007-07-31 23:24 compiz
drwxr-xr-x 2 root root 4096 2007-07-31 23:21 compizconfig
drwxr-xr-x 2 root root 4096 2007-07-31 23:22 emerald

lib:
total 2304
drwxr-xr-x 9 root root    4096 2007-10-23 00:15 .
drwxr-xr-x 8 root root    4096 2007-10-23 08:18 ..
drwxr-xr-x 3 root root    4096 2007-06-06 21:34 ccs
drwxr-xr-x 2 root root   12288 2007-07-31 23:26 compiz
drwxr-xr-x 3 root root    4096 2007-07-31 22:31 compizconfig
drwxr-xr-x 3 root root    4096 2007-06-06 21:34 emerald
-rw-r--r-- 1 root root  533272 2007-06-06 22:27 libccs.a
-rwxr-xr-x 1 root root     821 2007-06-06 22:27 libccs.la
lrwxrwxrwx 1 root root      15 2007-06-06 22:27 libccs.so -> libccs.so.0.0.0
lrwxrwxrwx 1 root root      15 2007-06-06 22:27 libccs.so.0 -> libccs.so.0.0.0
-rwxr-xr-x 1 root root  335102 2007-06-06 22:27 libccs.so.0.0.0
-rw-r--r-- 1 root root  551990 2007-07-31 23:21 libcompizconfig.a
-rwxr-xr-x 1 root root     884 2007-07-31 23:21 libcompizconfig.la
lrwxrwxrwx 1 root root      24 2007-07-31 23:21 libcompizconfig.so -> libcompizconfig.so.0.0.0
lrwxrwxrwx 1 root root      24 2007-07-31 23:21 libcompizconfig.so.0 -> libcompizconfig.so.0.0.0
-rwxr-xr-x 1 root root  347043 2007-07-31 23:21 libcompizconfig.so.0.0.0
-rw-r--r-- 1 root root  123676 2007-07-31 23:20 libdecoration.a
-rwxr-xr-x 1 root root     850 2007-07-31 23:20 libdecoration.la
lrwxrwxrwx 1 root root      22 2007-07-31 23:20 libdecoration.so -> libdecoration.so.0.0.0
lrwxrwxrwx 1 root root      22 2007-07-31 23:20 libdecoration.so.0 -> libdecoration.so.0.0.0
-rwxr-xr-x 1 root root   93766 2007-07-31 23:20 libdecoration.so.0.0.0
-rw-r--r-- 1 root root  155358 2007-07-31 23:22 libemeraldengine.a
-rwxr-xr-x 1 root root    1536 2007-07-31 23:22 libemeraldengine.la
lrwxrwxrwx 1 root root      25 2007-07-31 23:22 libemeraldengine.so -> libemeraldengine.so.0.0.0
lrwxrwxrwx 1 root root      25 2007-07-31 23:22 libemeraldengine.so.0 -> libemeraldengine.so.0.0.0
-rwxr-xr-x 1 root root  114304 2007-07-31 23:22 libemeraldengine.so.0.0.0
drwxr-xr-x 2 root root    4096 2007-07-31 23:24 pkgconfig
drwxrwsr-x 3 root staff   4096 2007-10-22 21:01 python2.4
drwxrwsr-x 3 root staff   4096 2007-05-28 09:36 python2.5

share:
total 24
drwxr-xr-x 6 root root 4096 2007-10-22 23:34 .
drwxr-xr-x 8 root root 4096 2007-10-23 08:18 ..
drwxr-xr-x 2 root root 4096 2007-06-06 22:27 ccs
drwxr-xr-x 2 root root 4096 2007-07-31 23:26 compiz
drwxr-xr-x 2 root root 4096 2007-07-31 23:21 compizconfig
drwxr-xr-x 4 root root 4096 2007-07-31 23:22 emerald

---

