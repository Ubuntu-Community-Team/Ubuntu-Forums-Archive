---
title: "help with firefox in kubuntu"
date: 2009-03-10
forum: General Help
---

### Post by luke0927 on 2009-03-10
OK so i have been using ubuntu for a couple months on my desktop and love it just installed kubuntu on a laptop just to check it out...not a big fan of konquror and want run firefox....i downloaded firefox and it was a .bz2 file i extract that but i don't see an install file or anything to install the program where i can launch it from the menu?  can someone tell me what i need to do im still a newbie..

I can run ./firefox and it will launch the browser but its not really installed to my applications


Here is everything in the directory


-rw-r--r-- 1 luke luke     2035 2009-02-19 11:04 application.ini                
-rwxr-xr-x 1 luke luke     1953 2009-02-19 11:04 blocklist.xml                  
-rw-r--r-- 1 luke luke      232 2009-02-19 11:04 browserconfig.properties       
drwxr-xr-x 3 luke luke     4096 2009-02-19 11:05 chrome                         
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:05 components                     
-rwxr-xr-x 1 luke luke    45096 2009-02-19 11:05 crashreporter                  
-rw-r--r-- 1 luke luke     3558 2009-02-19 11:05 crashreporter.ini              
-rw-r--r-- 1 luke luke      583 2009-02-19 11:05 crashreporter-override.ini     
drwxr-xr-x 5 luke luke     4096 2009-02-19 11:05 defaults                       
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:05 dictionaries                   
drwxr-xr-x 3 luke luke     4096 2009-02-19 11:05 extensions                     
-rwxr-xr-x 1 luke luke     3951 2009-02-19 11:04 firefox
-rwxr-xr-x 1 luke luke     7476 2009-02-19 11:05 firefox-bin
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:05 greprefs
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:05 icons
-rw-r--r-- 1 luke luke      478 2009-02-19 11:05 libfreebl3.chk
-rwxr-xr-x 1 luke luke   292320 2009-02-19 11:05 libfreebl3.so
-rwxr-xr-x 1 luke luke    30920 2009-02-19 11:05 libjemalloc.so
-rwxr-xr-x 1 luke luke   603416 2009-02-19 11:05 libmozjs.so
-rwxr-xr-x 1 luke luke   200736 2009-02-19 11:05 libnspr4.so
-rwxr-xr-x 1 luke luke   960176 2009-02-19 11:05 libnss3.so
-rwxr-xr-x 1 luke luke   313676 2009-02-19 11:05 libnssckbi.so
-rwxr-xr-x 1 luke luke   119844 2009-02-19 11:05 libnssdbm3.so
-rwxr-xr-x 1 luke luke    77564 2009-02-19 11:05 libnssutil3.so
-rwxr-xr-x 1 luke luke    13180 2009-02-19 11:05 libplc4.so
-rwxr-xr-x 1 luke luke     8748 2009-02-19 11:05 libplds4.so
-rwxr-xr-x 1 luke luke   125644 2009-02-19 11:05 libsmime3.so
-rw-r--r-- 1 luke luke      478 2009-02-19 11:05 libsoftokn3.chk
-rwxr-xr-x 1 luke luke   181776 2009-02-19 11:05 libsoftokn3.so
-rwxr-xr-x 1 luke luke   406596 2009-02-19 11:05 libsqlite3.so
-rwxr-xr-x 1 luke luke   160036 2009-02-19 11:05 libssl3.so
-rwxr-xr-x 1 luke luke    11816 2009-02-19 11:05 libxpcom.so
-rwxr-xr-x 1 luke luke 13018048 2009-02-19 11:05 libxul.so
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:05 modules
-rwxr-xr-x 1 luke luke    10772 2009-02-19 11:05 mozilla-xremote-client
-rw-r--r-- 1 luke luke      112 2009-02-19 11:04 old-homepage-default.properties
-rw-r--r-- 1 luke luke       45 2009-02-19 11:04 platform.ini
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:05 plugins
-rw-r--r-- 1 luke luke      177 2009-02-19 11:04 README.txt
-rwxr-xr-x 1 luke luke    15767 2009-02-19 11:04 removed-files
drwxr-xr-x 6 luke luke     4096 2009-02-19 11:05 res
-rwxr-xr-x 1 luke luke    11410 2009-02-19 11:04 run-mozilla.sh
drwxr-xr-x 2 luke luke     4096 2009-02-19 11:04 searchplugins
-rw-r--r-- 1 luke luke      825 2009-02-19 11:05 Throbber-small.gif
-rwxr-xr-x 1 luke luke    69672 2009-02-19 11:05 updater
-rw-r--r-- 1 luke luke      300 2009-02-19 11:04 updater.ini

---

### Post by yther on 2009-03-10
You don't need to go through all of that stuff.  :)

You can run Adept from the K menu, search for Firefox and install it from there.  Other ways include, open a Konsole and type "sudo apt-get install firefox" or (install and) run Synaptic, which is another package manager.  It's based on Gnome's toolkit so it looks different, but try it out... I find it much better than Adept.

After you install it by one of those methods, it should be in your Internet menu along with Konqueror.  With a right-click you can add it to the Favorites section.

Also see "Adding & Removing Software" at the [Ubuntu help site]("https://help.ubuntu.com/8.10/index.html").  It's not Kubuntu-specific, but it should give you a good idea of your choices.  :)

---

### Post by luke0927 on 2009-03-10
Thanks i finally found adept and its installing from there....i thing i like the gnome package manger better I'll try and figure out how to install it....i tried the sudo apt-get install firefox and got a problem....maybe i just fat fingered it....

thanks

---

