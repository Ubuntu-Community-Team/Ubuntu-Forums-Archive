---
title: "chrome doesn't start"
date: 2014-04-09
forum: Desktop Environments
---

### Post by evagelos on 2014-04-09
ekriezis@ekriezis-VGN-SR19VN:~$ **google-chrome**

[0409/192808:ERROR:nss_util.cc(90)] Failed to create /home/ekriezis/.pki/nssdb directory.
[0409/192808:ERROR:nss_util.cc(90)] Failed to create /home/ekriezis/.pki/nssdb directory.
[5851:5883:0409/192809:ERROR:nss_util.cc(90)] Failed to create /home/ekriezis/.pki/nssdb directory.
[5851:5851:0409/192809:ERROR:process_singleton_linux.cc(394)] readlink failed: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
[5851:5851:0409/192809:ERROR:process_singleton_linux.cc(240)] readlink(/home/ekriezis/.config/google-chrome/SingletonLock) failed: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
[5851:5851:0409/192809:ERROR:process_singleton_linux.cc(240)] readlink(/home/ekriezis/.config/google-chrome/SingletonLock) failed: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
[5851:5851:0409/192809:ERROR:process_singleton_linux.cc(264)] Failed to create /home/ekriezis/.config/google-chrome/SingletonLock: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
[5851:5851:0409/192809:ERROR:process_singleton_linux.cc(394)] readlink failed: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
[5851:5851:0409/192809:ERROR:process_singleton_linux.cc(240)] readlink(/home/ekriezis/.config/google-chrome/SingletonLock) failed: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
[5851:5851:0409/192809:ERROR:chrome_browser_main.cc(1198)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

---

### Post by bof2 on 2014-05-22
I have had the same problems! Change the permission of the .config/google-chrome directory to read/write users. That solved my problems.

---

### Post by Frogs Hair on 2014-05-22
Removing .config/google-chrome often helps and a new profile is created at startup ,  The downside is the loss of bookmarks and extensions ,but is an easy fix if the Google  sync features is used . Many media plug-ins have been removed in version 35 as Google tries to make the browser more secure and will affect all  OS platforms .

---

