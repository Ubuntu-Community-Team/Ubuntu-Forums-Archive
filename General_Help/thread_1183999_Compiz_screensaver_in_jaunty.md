---
title: "Compiz screensaver in jaunty"
date: 2009-06-10
forum: General Help
---

### Post by xfearxnxloathing on 2009-06-10
hey guys i'm trying to get the compiz screensaver to work under jaunty after seeing it on yourtube.

this is the website i got directions from: [http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/](http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/)

when i get to the make & make install section i get this error:

```
envy@Elemented:~/compizplugins$ cd ~/compizplugins/screensaver/
envy@Elemented:~/compizplugins/screensaver$ make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
```

i do have compiz running and fully functional...  any ideas?

---

### Post by s.fox on 2009-06-10
Hi,

Can you post the output of

```
compiz --version 
```

Also, do you have compiz working normally (without these pluggins)?

Thanks.

-Ash R

---

### Post by BslBryan on 2009-06-10
When you have everything installed, do this:
```
mkdir ~/compiz/
```
then 
```
wget -O /tmp/screensaver.tar 'http://oreaus.googlepages.com/screensaver.tar'

```
then
```
tar -xf '/tmp/screensaver.tar' -C ~/compiz/
```
then
```
cd ~/compiz/screensaver
make clean
make
make install
```

Then restart compiz, and all should be well. :-)

---

### Post by internalkernel on 2009-06-10
I just got this installed... via that page you posted. Check what compiz packages you have installed - go through Synaptic and make sure everything listed is installed. The web page listed is for 8.04 some of the packages may be different. In my case, it was a different version of Compiz-Bcop...

---

### Post by xfearxnxloathing on 2009-06-10
> **Ash R said:**
> Hi,

Can you post the output of

```
compiz --version 
```

Also, do you have compiz working normally (without these pluggins)?

Thanks.

-Ash R

i do have compiz running everything from wobbly windows to snow i would love to have the screen saver, this is what i got from your code: ```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
compiz 0.8.2
```

---

### Post by xfearxnxloathing on 2009-06-10
> **BslBryan said:**
> When you have everything installed, do this:
```
mkdir ~/compiz/
```
then 
```
wget -O /tmp/screensaver.tar 'http://oreaus.googlepages.com/screensaver.tar'

```
then
```
tar -xf '/tmp/screensaver.tar' -C ~/compiz/
```
then
```
cd ~/compiz/screensaver
make clean
make
make install
```

Then restart compiz, and all should be well. :-)

> **internalkernel said:**
> I just got this installed... via that page you posted. Check what compiz packages you have installed - go through Synaptic and make sure everything listed is installed. The web page listed is for 8.04 some of the packages may be different. In my case, it was a different version of Compiz-Bcop...

ok im trying both you guys advice, thnx so much everyone!

---

### Post by fcuk112 on 2009-06-10
i am getting this when i compile the thing, this is with compiz turned off as suggested in another thread:

```

convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : vector.cpp -> build/vector.lo
compiling : flyingwindows.cpp -> build/flyingwindows.lo
compiling : rotatingcube.cpp -> build/rotatingcube.lo
compiling : effect.cpp -> build/effect.lo
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function ‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:
screensaver.cpp:223: error: cannot convert ‘CompDisplay*’ to ‘const char*’ for argument ‘1’ to ‘void compLogMessage(const char*, CompLogLevel, const char*, ...)’
make: *** [build/screensaver.lo] Error 1

```

---

### Post by xfearxnxloathing on 2009-06-10
> **internalkernel said:**
> I just got this installed... via that page you posted. Check what compiz packages you have installed - go through Synaptic and make sure everything listed is installed. The web page listed is for 8.04 some of the packages may be different. In my case, it was a different version of Compiz-Bcop...


i went to synamptic and check marked bcop to install the others are dev and then a bunch that haver nothing to do with compiz..  then i went back and tried the make again and same error..

---

### Post by BslBryan on 2009-06-10
Open System --> Administration --> Software Sources.  Select the Third-Party Software tab and click Add. 

Paste in the line below and click Add Source.
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

Close Software Sources and when prompted, choose to reload the repositories.

A number of software updates related to Compiz should become available now; install them using Update Manager. Log out and back in to Ubuntu or restart Compiz manually. You should now be up-to-date.

Make sure Compiz is installed, because now in System --> Preferences, it should say Compiz Config Settings Manager (Not Advanced Desktop Display Settings).  If not,

```
sudo apt-get install compizconfig-settings-manager
```

And then follow the instructions I posted before.

---

### Post by xfearxnxloathing on 2009-06-10
> **BslBryan said:**
> When you have everything installed, do this:
```
mkdir ~/compiz/
```
then 
```
wget -O /tmp/screensaver.tar 'http://oreaus.googlepages.com/screensaver.tar'

```
then
```
tar -xf '/tmp/screensaver.tar' -C ~/compiz/
```
then
```
cd ~/compiz/screensaver
make clean
make
make install
```

Then restart compiz, and all should be well. :-)

no go...  the results: ```
envy@Elemented:~$ mkdir ~/compiz/
envy@Elemented:~$ wget -O /tmp/screensaver.tar 'http://oreaus.googlepages.com/screensaver.tar'
--2009-06-10 20:05:39--  http://oreaus.googlepages.com/screensaver.tar
Resolving oreaus.googlepages.com... 209.85.173.118
Connecting to oreaus.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2099200 (2.0M) [application/octet-stream]
Saving to: `/tmp/screensaver.tar'

100%[======================================>] 2,099,200    172K/s   in 14s     

2009-06-10 20:05:54 (149 KB/s) - `/tmp/screensaver.tar' saved [2099200/2099200]

envy@Elemented:~$ tar -xf '/tmp/screensaver.tar' -C ~/compiz/
envy@Elemented:~$ cd ~/compiz/screensaver
envy@Elemented:~/compiz/screensaver$ make clean
Makefile:48: *** [ERROR] Compiz not installed.  Stop.

```

---

### Post by BslBryan on 2009-06-10
And again, I say before you do what you just tried, do this: 
> **BslBryan said:**
> Open System --> Administration --> Software Sources.  Select the Third-Party Software tab and click Add. 

Paste in the line below and click Add Source.
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

Close Software Sources and when prompted, choose to reload the repositories.

A number of software updates related to Compiz should become available now; install them using Update Manager. Log out and back in to Ubuntu or restart Compiz manually. You should now be up-to-date.

Make sure Compiz is installed, because now in System --> Preferences, it should say Compiz Config Settings Manager (Not Advanced Desktop Display Settings).  If not,

```
sudo apt-get install compizconfig-settings-manager
```

And then follow the instructions I posted before.

---

### Post by xfearxnxloathing on 2009-06-10
> **BslBryan said:**
> Open System --> Administration --> Software Sources.  Select the Third-Party Software tab and click Add. 

Paste in the line below and click Add Source.
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

Close Software Sources and when prompted, choose to reload the repositories.

A number of software updates related to Compiz should become available now; install them using Update Manager. Log out and back in to Ubuntu or restart Compiz manually. You should now be up-to-date.

Make sure Compiz is installed, because now in System --> Preferences, it should say Compiz Config Settings Manager (Not Advanced Desktop Display Settings).  If not,

```
sudo apt-get install compizconfig-settings-manager
```

And then follow the instructions I posted before.

i already had compiz-settings-manager installed but i added the software source you provided it said something like 53 updates available but within 3 seconds it ran through and showed up nothing as in i didn't have to click anything but close on the update manager, so idk if it really grabbed any update or not.

---

### Post by xfearxnxloathing on 2009-06-10
**[COLOR="Red"]THREAD SOLVED[/COLOR]**[COLOR="Red"]!!!![/COLOR]

see: [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=1184203]("http://ubuntuforums.org/showthread.php?t=1184203")[/COLOR]

---

