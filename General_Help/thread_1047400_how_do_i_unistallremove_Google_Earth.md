---
title: "how do i unistall/remove Google Earth?"
date: 2009-01-22
forum: General Help
---

### Post by redonwhite on 2009-01-22
How do i remove Google Earth 4.3 from my system.  I used This method to install it. [http://ubuntu.imoka.net/2009/01/how-to-install-google-earth-in-ubuntu.html](http://ubuntu.imoka.net/2009/01/how-to-install-google-earth-in-ubuntu.html)

---

### Post by taurus on 2009-01-22
Did you remember which directory you installed it to?  From a terminal, change to that directory and there should be an uninstall program that you can run to uninstall it.

Applications -> Accessories -> Terminal
```
cd *whatever_directory_you_installed_it*
sudo ./uninstall
```

---

### Post by sandyd on 2009-01-22
pretty easy...
navigate to the directory where you installed google earth (mines in
/opt/google-earth)

and terminal-ize this
```

sudo ./uninstall

```

---

### Post by Irony on 2009-01-22
It actually give the answer further down the list on the link you provide!

Your system may differ, but on my Mepis system it is;

```
/opt/google-earth

/usr/local/bin/googleearth
```

Thus to delete you can type Alt F2 then

```
gksudo nautilus
```

Then delete the folder and link by highlighting the items and clicking delete (this will put them in the root bins or shift delete to permanently delete).

---

### Post by Irony on 2009-01-22
Good point, in;

```
/opt/google-earth
```

I have a shell script called uninstall - I would either double click on that or type sudo in terminal and then drag the script into the terminal.

---

### Post by redonwhite on 2009-01-22
I go into terminal and go into /opt/google-earth.  I then type sudo ./uninstall and it says "could not find a usable uninstall program. Aborting."  When i go List whats in the directory though i see a the word uninstall. any ideas?

---

### Post by taurus on 2009-01-22
What's the output of this command?  Make sure you are in the /opt/google-earth directory.

```
ls -la
```

p.s.  Did you install Google Earth to /opt/google-earth?

---

### Post by snarglesnap on 2009-01-23
I'm having the same issue, here's my output...

total 48372
drwxr-xr-x  11 root root    4096 2009-01-21 01:42 .
drwxr-xr-x   4 root root    4096 2009-01-21 01:42 ..
-rw-r--r--   1 root root   65579 2009-01-21 01:42 drivers.ini
drwxr-xr-x   2 root root    4096 2009-01-21 01:42 Google
-rwxr-xr-x   1 root root    1308 2009-01-21 01:42 googleearth
-rwxr-xr-x   1 root root   48148 2009-01-21 01:42 googleearth-bin
-rw-r--r--   1 root root    4787 2009-01-21 01:42 googleearth-icon.png
-rw-r--r--   1 root root     638 2009-01-21 01:42 googleearth-mimetypes.xml
-rw-r--r--   1 root root   17748 2009-01-21 01:42 googleearth.xpm
-rw-r--r--   1 root root     416 2009-01-21 01:42 Google-googleearth.desktop
-rw-r--r--   1 root root   18011 2009-01-21 01:42 gpl.txt
-rwxr-xr-x   1 root root  245868 2009-01-21 01:42 gpsbabel
-rw-r--r--   1 root root     983 2009-01-21 01:42 ImporterGlobalSettings.ini
-rw-r--r--   1 root root    5054 2009-01-21 01:42 ImporterUISettings.ini
-rw-r--r--   1 root root       0 2009-01-21 01:42 kh20
drwxr-xr-x   2 root root    4096 2009-01-21 01:42 kvw
drwxr-xr-x   2 root root    4096 2009-01-21 01:42 lang
-rwxr-xr-x   1 root root   13376 2009-01-21 01:42 libalchemyext.so
-rwxr-xr-x   1 root root   11192 2009-01-21 01:42 libapiloader.so
-rwxr-xr-x   1 root root  335416 2009-01-21 01:42 libauth.so
-rwxr-xr-x   1 root root  560840 2009-01-21 01:42 libbase.so
-rwxr-xr-x   1 root root  849044 2009-01-21 01:42 libbasicingest.so
-rwxr-xr-x   1 root root 3122472 2009-01-21 01:42 libcollada-1.4.so
-rwxr-xr-x   1 root root  264196 2009-01-21 01:42 libcollada.so
-rwxr-xr-x   1 root root  803496 2009-01-21 01:42 libcommon.so
-rwxr-xr-x   1 root root   21604 2009-01-21 01:42 libcomponentframework.so
-rwxr-xr-x   1 root root 1196036 2009-01-21 01:42 libcrypto.so.0.9.8
-rwxr-xr-x   1 root root  209928 2009-01-21 01:42 libcurl.so.4
-rwxr-xr-x   1 root root 5316840 2009-01-21 01:42 libevll.so
-rwxr-xr-x   1 root root  811712 2009-01-21 01:42 libflightsim.so
-rwxr-xr-x   1 root root  794812 2009-01-21 01:42 libfreeimage.so.3
-rwxr-xr-x   1 root root   13348 2009-01-21 01:42 libfusioncommon.so
-rw-r--r--   1 root root   42272 2009-01-21 01:42 libgcc_s.so.1
-rwxr-xr-x   1 root root 3235956 2009-01-21 01:42 libgdal.so
-rwxr-xr-x   1 root root  210664 2009-01-21 01:42 libge_net.so
-rwxr-xr-x   1 root root 3363068 2009-01-21 01:42 libgeobase.so
-rwxr-xr-x   1 root root  517084 2009-01-21 01:42 libGLU.so.1
-rwxr-xr-x   1 root root  987572 2009-01-21 01:42 libgoogleearth_lib.so
-rwxr-xr-x   1 root root  450816 2009-01-21 01:42 libgooglesearch.so
-rwxr-xr-x   1 root root  516488 2009-01-21 01:42 libgps.so
-rwxr-xr-x   1 root root  415112 2009-01-21 01:42 libicudata.so.38
-rwxr-xr-x   1 root root 1087360 2009-01-21 01:42 libicuuc.so.38
-rwxr-xr-x   1 root root  399636 2009-01-21 01:42 libIGAttrs.so
-rwxr-xr-x   1 root root   62512 2009-01-21 01:42 libIGCollision.so
-rwxr-xr-x   1 root root  977852 2009-01-21 01:42 libIGCore.so
-rwxr-xr-x   1 root root   78392 2009-01-21 01:42 libIGDisplay.so
-rwxr-xr-x   1 root root  546512 2009-01-21 01:42 libIGExportCommon.so
-rwxr-xr-x   1 root root  746016 2009-01-21 01:42 libIGGfx.so
-rwxr-xr-x   1 root root  257464 2009-01-21 01:42 libIGGui.so
-rwxr-xr-x   1 root root  289872 2009-01-21 01:42 libIGMath.so
-rwxr-xr-x   1 root root  871292 2009-01-21 01:42 libIGOpt.so
-rwxr-xr-x   1 root root 1094236 2009-01-21 01:42 libIGSg.so
-rwxr-xr-x   1 root root  156408 2009-01-21 01:42 libIGUtils.so
-rwxr-xr-x   1 root root  140076 2009-01-21 01:42 libinput_plugin.so
-rwxr-xr-x   1 root root  143028 2009-01-21 01:42 libjpeg.so.62
-rwxr-xr-x   1 root root 1599824 2009-01-21 01:42 liblayer.so
-rwxr-xr-x   1 root root  135164 2009-01-21 01:42 libmath.so
-rwxr-xr-x   1 root root  400632 2009-01-21 01:42 libmeasure.so
-rwxr-xr-x   1 root root   23532 2009-01-21 01:42 libminizip.so
-rwxr-xr-x   1 root root  380796 2009-01-21 01:42 libmng.so.1
-rwxr-xr-x   1 root root   39636 2009-01-21 01:42 libmoduleframework.so
-rwxr-xr-x   1 root root 1112968 2009-01-21 01:42 libnavigate.so
-rwxr-xr-x   1 root root  160032 2009-01-21 01:42 libpng12.so.0
-rwxr-xr-x   1 root root   14340 2009-01-21 01:42 libport.so
-rwxr-xr-x   1 root root  208088 2009-01-21 01:42 libproj.so.0
-rwxr-xr-x   1 root root 2324180 2009-01-21 01:42 libQt3Support.so.4
-rwxr-xr-x   1 root root 1823904 2009-01-21 01:42 libQtCore.so.4
-rwxr-xr-x   1 root root 6487056 2009-01-21 01:42 libQtGui.so.4
-rwxr-xr-x   1 root root  541908 2009-01-21 01:42 libQtNetwork.so.4
-rwxr-xr-x   1 root root  165176 2009-01-21 01:42 libQtSql.so.4
-rwxr-xr-x   1 root root  322248 2009-01-21 01:42 libQtXml.so.4
-rwxr-xr-x   1 root root  242008 2009-01-21 01:42 librender.so
-rwxr-xr-x   1 root root  871596 2009-01-21 01:42 libstdc++.so.6
-rwxr-xr-x   1 root root  374644 2009-01-21 01:42 libtiff.so.3
-rwxr-xr-x   1 root root  401640 2009-01-21 01:42 libwmsbase.so
-rwxr-xr-x   1 root root   89476 2009-01-21 01:42 libz.so.1
drwxr-xr-x   3 root root    4096 2009-01-21 01:42 linux
drwxr-xr-x   3 root root    4096 2009-01-21 01:42 .manifest
-rw-r--r--   1 root root     661 2009-01-21 01:42 PCOptimizations.ini
drwxr-xr-x   3 root root    4096 2009-01-21 01:42 plugins
-rw-r--r--   1 root root       7 2009-01-21 01:42 qt.conf
drwxr-xr-x 267 root root   32768 2009-01-21 01:42 resources
drwxr-xr-x   2 root root    4096 2009-01-21 01:42 shaders
-rwxr-xr-x   1 root root    1702 2009-01-21 01:42 uninstall
drwxr-xr-x   2 root root    4096 2009-01-21 01:42 xml

---

### Post by redonwhite on 2009-01-23
> **taurus said:**
> What's the output of this command?  Make sure you are in the /opt/google-earth directory.

```
ls -la
```

p.s.  Did you install Google Earth to /opt/google-earth?

my output is

```
total 48368
drwxr-xr-x  11 root root    4096 2009-01-22 11:48 .
drwxr-xr-x   3 root root    4096 2009-01-22 11:48 ..
-rw-r--r--   1 root root   65579 2009-01-22 11:48 drivers.ini
drwxr-xr-x   2 root root    4096 2009-01-22 11:48 Google
-rwxr-xr-x   1 root root    1308 2009-01-22 11:48 googleearth
-rwxr-xr-x   1 root root   48148 2009-01-22 11:48 googleearth-bin
-rw-r--r--   1 root root    4787 2009-01-22 11:48 googleearth-icon.png
-rw-r--r--   1 root root     638 2009-01-22 11:48 googleearth-mimetypes.xml
-rw-r--r--   1 root root   17748 2009-01-22 11:48 googleearth.xpm
-rw-r--r--   1 root root     416 2009-01-22 11:48 Google-googleearth.desktop
-rw-r--r--   1 root root   18011 2009-01-22 11:48 gpl.txt
-rwxr-xr-x   1 root root  245868 2009-01-22 11:48 gpsbabel
-rw-r--r--   1 root root     983 2009-01-22 11:48 ImporterGlobalSettings.ini
-rw-r--r--   1 root root    5054 2009-01-22 11:48 ImporterUISettings.ini
-rw-r--r--   1 root root       0 2009-01-22 11:48 kh20
drwxr-xr-x   2 root root    4096 2009-01-22 11:48 kvw
drwxr-xr-x   2 root root    4096 2009-01-22 11:48 lang
-rwxr-xr-x   1 root root   13376 2009-01-22 11:48 libalchemyext.so
-rwxr-xr-x   1 root root   11192 2009-01-22 11:48 libapiloader.so
-rwxr-xr-x   1 root root  335416 2009-01-22 11:48 libauth.so
-rwxr-xr-x   1 root root  560840 2009-01-22 11:48 libbase.so
-rwxr-xr-x   1 root root  849044 2009-01-22 11:48 libbasicingest.so
-rwxr-xr-x   1 root root 3122472 2009-01-22 11:48 libcollada-1.4.so
-rwxr-xr-x   1 root root  264196 2009-01-22 11:48 libcollada.so
-rwxr-xr-x   1 root root  803496 2009-01-22 11:48 libcommon.so
-rwxr-xr-x   1 root root   21604 2009-01-22 11:48 libcomponentframework.so
-rwxr-xr-x   1 root root 1196036 2009-01-22 11:48 libcrypto.so.0.9.8
-rwxr-xr-x   1 root root  209928 2009-01-22 11:48 libcurl.so.4
-rwxr-xr-x   1 root root 5316840 2009-01-22 11:48 libevll.so
-rwxr-xr-x   1 root root  811712 2009-01-22 11:48 libflightsim.so
-rwxr-xr-x   1 root root  794812 2009-01-22 11:48 libfreeimage.so.3
-rwxr-xr-x   1 root root   13348 2009-01-22 11:48 libfusioncommon.so
-rw-r--r--   1 root root   42272 2009-01-22 11:48 libgcc_s.so.1
-rwxr-xr-x   1 root root 3235956 2009-01-22 11:48 libgdal.so
-rwxr-xr-x   1 root root  210664 2009-01-22 11:48 libge_net.so
-rwxr-xr-x   1 root root 3363068 2009-01-22 11:48 libgeobase.so
-rwxr-xr-x   1 root root  517084 2009-01-22 11:48 libGLU.so.1
-rwxr-xr-x   1 root root  987572 2009-01-22 11:48 libgoogleearth_lib.so
-rwxr-xr-x   1 root root  450816 2009-01-22 11:48 libgooglesearch.so
-rwxr-xr-x   1 root root  516488 2009-01-22 11:48 libgps.so
-rwxr-xr-x   1 root root  415112 2009-01-22 11:48 libicudata.so.38
-rwxr-xr-x   1 root root 1087360 2009-01-22 11:48 libicuuc.so.38
-rwxr-xr-x   1 root root  399636 2009-01-22 11:48 libIGAttrs.so
-rwxr-xr-x   1 root root   62512 2009-01-22 11:48 libIGCollision.so
-rwxr-xr-x   1 root root  977852 2009-01-22 11:48 libIGCore.so
-rwxr-xr-x   1 root root   78392 2009-01-22 11:48 libIGDisplay.so
-rwxr-xr-x   1 root root  546512 2009-01-22 11:48 libIGExportCommon.so
-rwxr-xr-x   1 root root  746016 2009-01-22 11:48 libIGGfx.so
-rwxr-xr-x   1 root root  257464 2009-01-22 11:48 libIGGui.so
-rwxr-xr-x   1 root root  289872 2009-01-22 11:48 libIGMath.so
-rwxr-xr-x   1 root root  871292 2009-01-22 11:48 libIGOpt.so
-rwxr-xr-x   1 root root 1094236 2009-01-22 11:48 libIGSg.so
-rwxr-xr-x   1 root root  156408 2009-01-22 11:48 libIGUtils.so
-rwxr-xr-x   1 root root  140076 2009-01-22 11:48 libinput_plugin.so
-rwxr-xr-x   1 root root  143028 2009-01-22 11:48 libjpeg.so.62
-rwxr-xr-x   1 root root 1599824 2009-01-22 11:48 liblayer.so
-rwxr-xr-x   1 root root  135164 2009-01-22 11:48 libmath.so
-rwxr-xr-x   1 root root  400632 2009-01-22 11:48 libmeasure.so
-rwxr-xr-x   1 root root   23532 2009-01-22 11:48 libminizip.so
-rwxr-xr-x   1 root root  380796 2009-01-22 11:48 libmng.so.1
-rwxr-xr-x   1 root root   39636 2009-01-22 11:48 libmoduleframework.so
-rwxr-xr-x   1 root root 1112968 2009-01-22 11:48 libnavigate.so
-rwxr-xr-x   1 root root  160032 2009-01-22 11:48 libpng12.so.0
-rwxr-xr-x   1 root root   14340 2009-01-22 11:48 libport.so
-rwxr-xr-x   1 root root  208088 2009-01-22 11:48 libproj.so.0
-rwxr-xr-x   1 root root 2324180 2009-01-22 11:48 libQt3Support.so.4
-rwxr-xr-x   1 root root 1823904 2009-01-22 11:48 libQtCore.so.4
-rwxr-xr-x   1 root root 6487056 2009-01-22 11:48 libQtGui.so.4
-rwxr-xr-x   1 root root  541908 2009-01-22 11:48 libQtNetwork.so.4
-rwxr-xr-x   1 root root  165176 2009-01-22 11:48 libQtSql.so.4
-rwxr-xr-x   1 root root  322248 2009-01-22 11:48 libQtXml.so.4
-rwxr-xr-x   1 root root  242008 2009-01-22 11:48 librender.so
-rwxr-xr-x   1 root root  871596 2009-01-22 11:48 libstdc++.so.6
-rwxr-xr-x   1 root root  374644 2009-01-22 11:48 libtiff.so.3
-rwxr-xr-x   1 root root  401640 2009-01-22 11:48 libwmsbase.so
-rwxr-xr-x   1 root root   89476 2009-01-22 11:48 libz.so.1
drwxr-xr-x   3 root root    4096 2009-01-22 11:48 linux
drwxr-xr-x   3 root root    4096 2009-01-22 11:48 .manifest
-rw-r--r--   1 root root     661 2009-01-22 11:48 PCOptimizations.ini
drwxr-xr-x   3 root root    4096 2009-01-22 11:48 plugins
-rw-r--r--   1 root root       7 2009-01-22 11:48 qt.conf
drwxr-xr-x 267 root root   28672 2009-01-22 11:48 resources
drwxr-xr-x   2 root root    4096 2009-01-22 11:48 shaders
-rwxr-xr-x   1 root root    1702 2009-01-22 11:48 uninstall
drwxr-xr-x   2 root root    4096 2009-01-22 11:48 xml
```

---

### Post by darkhole on 2009-02-18
Hey guys!! I got THE answer!!!

I also install Google Earth 5 using admin account, so my install directory is (was):
/opt/google-earth

So, I used this command:
sudo /opt/google-earth/unistall
and different combination of this, and always got the message:
"Could not find a usable uninstall program. Aborting."

But, this is how uninstall Google Earth 5 in Ubuntu:
In a terminal:

cd /opt/google-earth
sudo su
./uninstall


I got the answer from here:
[http://forum.ubuntu-fr.org/viewtopic.php?id=88007](http://forum.ubuntu-fr.org/viewtopic.php?id=88007)

Thanks Ubuntu-Fr!!!

---

### Post by roach33 on 2009-03-13
we learn new things everyday. thx.

---

### Post by Steve H on 2009-03-14
> **darkhole said:**
> Hey guys!! I got THE answer!!!

I also install Google Earth 5 using admin account, so my install directory is (was):
/opt/google-earth

So, I used this command:
sudo /opt/google-earth/unistall
and different combination of this, and always got the message:
"Could not find a usable uninstall program. Aborting."

But, this is how uninstall Google Earth 5 in Ubuntu:
In a terminal:

cd /opt/google-earth
sudo su
./uninstall


I got the answer from here:
[http://forum.ubuntu-fr.org/viewtopic.php?id=88007](http://forum.ubuntu-fr.org/viewtopic.php?id=88007)

Thanks Ubuntu-Fr!!!

Brilliant stuff, finally got rid of it.

;)

---

### Post by dimitriv on 2009-03-29
yeah finally sorted this too, thanks for sharing darkhole

---

