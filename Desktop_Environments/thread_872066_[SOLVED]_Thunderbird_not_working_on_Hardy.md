---
title: "[SOLVED] Thunderbird not working on Hardy"
date: 2008-07-27
forum: Desktop Environments
---

### Post by r11_kaede on 2008-07-27
Hi guys,

I'm currently running Hardy, kernel 2.6.24-19-generic on my HP mini-note.

In a nutshell, Mozilla Thunderbird refuses to start up. When i click on the icon, it displays at the taskbar for a few seconds, and then disappears, nothing happens.

I've removed it via synaptic AND update manager, and reinstalled it via apt-get install thunderbird, but no effect.

Could anyone kindly help me with this?

thanks :)

---

### Post by tamoneya on 2008-07-27
can you try running thunderbird from terminal so we can see any errors it produces.  just type "thunderbird" into terminal(applications -> accessories -> terminal) and post any output you get.

---

### Post by r11_kaede on 2008-07-28
when i type "thunderbird" into the terminal,

xxx@NCC-1701-E:~$ thunderbird
xxx@NCC-1701-E:~$ 

this is exactly what i get.

but strangely enough, it opens when i type "sudo thunderbird"

why is this so?

---

### Post by tamoneya on 2008-07-28
calling a graphical program with sudo can mess up the permissions.  What is the output of:```
ls -la /home/tamoneya/.mozilla-thunderbird/

```

---

### Post by r11_kaede on 2008-07-28
drwx------  3 raymond raymond 4096 2008-07-28 03:25 .
drwxr-xr-x 37 raymond raymond 4096 2008-07-28 13:53 ..
drwx------  3 root    root    4096 2008-03-24 17:28 Profiles
-rwx------  1 root    root     111 2008-03-24 17:28 profiles.ini
-rwx------  1 root    root     335 2008-03-24 17:28 registry.dat

i have a feeling that the registry.dat might be a leftover from when i copied from windows -.-

is it possible for me to delete that file without screwing up thunderbird?

thanks :)

---

### Post by chunchengch on 2008-07-28
If you have SCIM installed, try this

[COLOR="Red"]$ sudo gedit /usr/lib/thunderbird/thunderbird[/COLOR]

add this line [COLOR="Green"]export GTK_IM_MODULE=xim[/COLOR] just after the [COLOR="Green"]#!/bin/sh[/COLOR] ,then save and exit, now you should be able to open Thunderbird.

---

### Post by tamoneya on 2008-07-28
> **r11_kaede said:**
> drwx------  3 raymond raymond 4096 2008-07-28 03:25 .
drwxr-xr-x 37 raymond raymond 4096 2008-07-28 13:53 ..
drwx------  3 root    root    4096 2008-03-24 17:28 Profiles
-rwx------  1 root    root     111 2008-03-24 17:28 profiles.ini
-rwx------  1 root    root     335 2008-03-24 17:28 registry.dat

i have a feeling that the registry.dat might be a leftover from when i copied from windows -.-

is it possible for me to delete that file without screwing up thunderbird?

thanks :)

profiles and everything in there should be owned by raymond.  So execute this in terminal then try thunderbird again:```
sudo chown -R raymond:raymond /home/raymond/.mozilla-thunderbird/
```

---

### Post by r11_kaede on 2008-07-29
To tamoneya: it worked! gave me a few heart-stopping seconds, before the friendly screen popped up. :D

to chunchengch: although yours didnt, but thank you so much for your assistance :) maybe its because i didnt have scim installed, which i will soon -.-

thanks guys for your help :)

---

### Post by tamoneya on 2008-07-29
> **r11_kaede said:**
> To tamoneya: it worked! gave me a few heart-stopping seconds, before the friendly screen popped up. :D

to chunchengch: although yours didnt, but thank you so much for your assistance :) maybe its because i didnt have scim installed, which i will soon -.-

thanks guys for your help :)

In order to try and prevent this from happening again you should never call thunderbird via sudo.  Because thunderbird is a graphical program sudo will mess up some of its permissions instead you should use gksudo if you for some reason need it to have root permissions (no clue why you would want that).

---

### Post by eberndl on 2008-07-30
Hi,

I'm having the same problem as r11_kaede. I noticed this problem started after the Firefox updated yesterday.  This is my output:
lizz@lizz-desktop:~$ ls -la /media/share/Mozilla/Thunderbird/
total 48
drwxrwxrwx 3 root root 16384 2008-04-30 22:15 .
drwxrwxrwx 4 root root 16384 2008-04-30 22:15 ..
drwxrwxrwx 4 root root 16384 2008-07-30 00:27 feeiwdgl.default

(It's set up like this because I dual boot with Windows)

and then
lizz@lizz-desktop:~$ ls -la /media/share/Mozilla/Thunderbird/feeiwdgl.default/
total 10304
drwxrwxrwx 4 root root   16384 2008-07-30 00:27 .
drwxrwxrwx 3 root root   16384 2008-04-30 22:15 ..
-rwxrwxrwx 1 root root     195 2005-02-27 11:39 90969431.s
-rwxrwxrwx 1 root root   99575 2008-07-25 01:31 abook.mab
-rwxrwxrwx 1 root root     248 2008-07-30 00:27 blocklist.xml
-rwxrwxrwx 1 root root   65536 2008-07-25 01:31 cert8.db
-rwxrwxrwx 1 root root     130 2008-07-27 23:57 compatibility.ini
-rwxrwxrwx 1 root root  151394 2008-07-27 23:57 compreg.dat
-rwxrwxrwx 1 root root     235 2008-05-14 18:23 cookies.txt
-rwxrwxrwx 1 root root    6677 2008-06-09 23:47 downloads.rdf
drwxrwxrwx 2 root root   16384 2008-04-30 22:17 extensions
-rwxrwxrwx 1 root root     212 2008-07-27 23:57 extensions.cache
-rwxrwxrwx 1 root root     196 2008-07-27 23:57 extensions.ini
-rwxrwxrwx 1 root root    2016 2008-07-27 23:57 extensions.rdf
-rwxrwxrwx 1 root root    1423 2004-07-27 19:10 history.mab
-rwxrwxrwx 1 root root   11185 2008-06-17 18:52 impab.mab
-rwxrwxrwx 1 root root  785168 2008-07-30 03:57 junklog.html
-rwxrwxrwx 1 root root   16384 2008-07-25 01:31 key3.db
-rwxrwxrwx 1 root root   40409 2008-07-29 21:57 localstore.rdf
drwxrwxrwx 5 root root   16384 2008-04-30 22:16 Mail
-rwxrwxrwx 1 root root     477 2004-07-08 11:21 mailViews.dat
-rwxrwxrwx 1 root root   10652 2008-05-08 22:37 mimeTypes.rdf
-rwxrwxrwx 1 root root  178976 2008-07-30 18:05 panacea.dat
-rwxrwxrwx 1 root root       0 2008-07-30 20:43 .parentlock
-rwxrwxrwx 1 root root      49 2005-10-01 16:45 persdict.dat
-rwxrwxrwx 1 root root   13282 2008-07-27 23:57 prefs.js
-rwxrwxrwx 1 root root   13479 2008-04-25 07:22 prefs.zal
-rwxrwxrwx 1 root root   16384 2008-04-30 23:02 secmod.db
-rwxrwxrwx 1 root root 4299666 2008-07-28 00:12 training.dat
-rwxrwxrwx 1 root root       0 2008-04-30 17:59 urlclassifier2.sqlite
-rwxrwxrwx 1 root root      10 2008-07-25 01:31 virtualFolders.dat
-rwxrwxrwx 1 root root 1060700 2008-07-27 23:57 XPC.mfasl
-rwxrwxrwx 1 root root 1000626 2008-07-25 01:32 xpc.mfl
-rwxrwxrwx 1 root root  116837 2008-07-27 23:57 xpti.dat
-rwxrwxrwx 1 root root 1162265 2008-07-27 23:57 XUL.mfasl
-rwxrwxrwx 1 root root 1145881 2008-07-25 01:32 xul.mfl


Can I fix this the same way?

Thanks in advance.

---

