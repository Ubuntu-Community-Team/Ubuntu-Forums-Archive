---
title: "Firefox beta 2. Flash installation help."
date: 2005-10-16
forum: Desktop Environments
---

### Post by Kirky_D on 2005-10-16
Just upgraded to the Beta 2 and i am wondering how to install flash player for it? i have tried putting in symbolic links from the original firefox plugins directory to the beta plugins directory but that didn't seem to work. 

I also tried reinstalling flash player itself but it didn't pick up the beta browser.

Any one know how to do this? 

Cheers all

---

### Post by Kirky_D on 2005-10-17
bump?

---

### Post by weblars on 2005-10-17
Symbolic links should work in this case. I installed Firefox 1.5 beta 2 for testing purposes in my home directory: /home/user/fire15. Then I removed the plugins directory fire15/plugins:
```
rm -r -f plugins
```
Finally I created a symbolic link (inside the fire15 directory):
```
sudo ln -s /usr/lib/mozilla-firefox/plugins plugins
```

---

### Post by Kirky_D on 2005-10-17
Tried that but it didn't work.

Here is a list of files and such from my beta directory

```
kirky@ubuntu:~/programs/firefox-beta$ ls
browserconfig.properties  libnss3.so          mozilla-xremote-client
chrome                    libnssckbi.so       plugins
components                libplc4.so          readme.txt
defaults                  libplds4.so         README.txt
extensions                libsmime3.so        removed-files
firefox                   libsoftokn3.chk     res
firefox-bin               libsoftokn3.so      run-mozilla.sh
greprefs                  libssl3.so          searchplugins
icons                     libxpcom_compat.so  updater
install.log               libxpcom_core.so    updater.ini
libmozjs.so               libxpcom.so         updates
libnspr4.so               libxpistub.so       xpicleanup

kirky@ubuntu:~/programs/firefox-beta$ cd plugins

kirky@ubuntu:~/programs/firefox-beta/plugins$ ls
**_flashplayer.xpt_**        libnpsoplugin.so     libtotem_mozilla.so
**_libflash-mozplugin.so_**  libtotem_mozilla.a   libtotem_mozilla.xpt
**_libflashplayer.so_**      libtotem_mozilla.la
kirky@ubuntu:~/programs/firefox-beta/plugins$

```

As you can see, the plugin is there. Although there are 2 .so packages in there. Could it be a conflict of interests? in about:plugins it shows 2 entries for shockwave player.

Would it be a good idea to get rid of the libflash-mozplugin.so one and try? or maybe the libflashplayer.so + flashplayer.xpt?

---

### Post by weblars on 2005-10-17
Did you install more than one flasplayer package (I'm using flasplayer-mozilla)?

My plugins directory contains these files:
```
**flashplayer.xpt**         mplayerplug-in-qt.so   mplayerplug-in-wmp.so
**libflashplayer.so**       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libjavaplugin_oji.so    mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in.so
```

You could try to move libflash-mozplugin.so to another directory.

---

### Post by Kirky_D on 2005-10-17
[QUOTE=weblars]Did you install more than one flasplayer package (I'm using flasplayer-mozilla)?

My plugins directory contains these files:
```
**flashplayer.xpt**         mplayerplug-in-qt.so   mplayerplug-in-wmp.so
**libflashplayer.so**       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libjavaplugin_oji.so    mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in.so
```

You could try to move libflash-mozplugin.so to another directory.[/QUOTE]

Doesn't seem to have helped.

I am also using flashplayer-mozilla from synaptic

This is really quite annoying. Anybody got any ideas at all? or did it just work when you tried it?

---

### Post by Kirky_D on 2005-10-18
bump?

In about :plugins it shows flash player as being enabled. 

Any help?

cheers

---

### Post by Kirky_D on 2005-10-18
bump?

In about: plugins it shows flash player as being enabled. 

Any help?

cheers

Edit:

Didn't mean to post twice, sorry

---

### Post by .Danny on 2005-10-18
I tried it with a sym link as well, not working.:(

---

### Post by Kirky_D on 2005-10-18
ok, for some reason my sound is working in flash just not the video?

This is getting weird

---

### Post by .Danny on 2005-10-19
I've tried to remove both firefoxes. Then install the default one, move all files from the default one to another dir and move the 1.5 beta 2 to the place where the default is... flash still not working.:(

Come on guys, there must be someone who can get it to work?:???:

---

### Post by Kirky_D on 2005-10-19
ok then, nobody knows the answer to this one. Which is fair enough. 

Could anybody please tell me how to completely remove all instances of flash and firefox and anything else that is related to  its operation so i can try a simple reinstall.

I have tried reinstalling but i don't think it was a full wipe of firefox.

Cheers all

---

### Post by pecanov on 2005-10-19
Just to say that I have been using Firefox 1.0 (that came from the ubuntu repositories), through Deer Park Alpha 1 and 2, to Firefox 1.5 b1 and b2, and all seem to work perfectly with flash plugin.
However, the installation bundles(1.1+) that I downloaded from the mozilla site I separatelly installed in /usr/local, but share the same configuration with the ubuntu 1.0 instance, located in the home directory.
Hope this helps ... somehow

---

### Post by Kirky_D on 2005-10-19
I have been having similer problems on windows with flash player. I am currently on windows and was searching the flash and firefox help sections and it said something about popupblockers stopping flash from working. 

So i went on to looking at other things, trying different things when i saw the adblock icon on one of the flash sites i visit. Which got me thinking about the no popup blocker thing. So i uninstalled the Adblock extension to firerfox and it sorted it out in windows for me. 

Perhaps thats what the problem is in ubuntu?

worth a try

---

### Post by mustang on 2005-10-19
I am using Firefox Beta 2 on Breezy---I downloaded the flash plugin from the macromedia site and both video and sound work fine.

---

### Post by Kirky_D on 2005-10-20
Adblock is the cause. you can just disable it rather than uninstalling it for flash animations. 

Tools>adblock>preferences>enable adblock

Just disable it or uninstall it and flash will work, aswell as the symbolic link to the plgins folder.

---

### Post by sanguinemoon on 2005-11-12
I can't get any flash at all to work in 1.5 and I've been trying to since the alpha version. I also have Mozilla Seamonkey and flash works in that. I copied all the sym links over from 1.0.7. When this failed I even tried reinstalling flash

---

### Post by sanguinemoon on 2005-11-12
Yeah. That does work, strangely enough. Evidently adblock blocks stupidly blocks all flash. Hopefully there's a way to block ads before the final version comes out :(

---

