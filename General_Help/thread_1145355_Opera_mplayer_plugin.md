---
title: "Opera mplayer plugin"
date: 2009-05-01
forum: General Help
---

### Post by fillintheblanks on 2009-05-01
OK I know it works because I got it working in ubuntu 7.10

now after upgrading to 9.04 I forgot how to do it :(


I remember having to copy some plugin files to the /lib/opera/plugins folder.. thats about it

if anyone out there has some tips it would be much appreciated.

---

### Post by fillintheblanks on 2009-05-01
ok NEVERMIND I got it working again! :)

what I did.. 


1. sudo apt-get build-dep mplayer-plugin

2. download mplayer-plugin source (I used daily build)

3. build the plugin using -> **./configure --with-x**

4. this will produce bunch of .so & .xpt files

5. move those files to your /usr/lib/opera/plugins folder

6. in Opera goto Tools/Preferences/Content/Plugin Options

7. under "plugins path" make sure to disable /usr/lib/mozilla/plugins and enable /usr/lib/opera/plugins

8. thats it!

---

