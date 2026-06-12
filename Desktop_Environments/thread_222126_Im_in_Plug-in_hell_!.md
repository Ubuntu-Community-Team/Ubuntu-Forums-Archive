---
title: "Im in Plug-in hell !"
date: 2006-07-24
forum: Desktop Environments
---

### Post by XeroCurve on 2006-07-24
Hello all, I am not a newbie but I am starting to feel like one =). I am running breezy on a fairly new machine and I have installed Automatix, and none of the plugins work in Firefox. The only internet/multimedia item that seems to work is connecting to an online radio stream through Steam Tuner. I have read a lot of threads and went to the plugin tester site and tried all of them and the only one that it said was installed is FLASH. After the install of Automatix it appeared that a lot of things changed. Different menu items and such, but im not sure what I didnt do. All the threads I have read seem to infer that after installing the items in Automatix that the plugins should be functional. Am I missing something? Please help!

---

### Post by Ziox on 2006-07-24
navigate to the folder /usr/lib/firefox/plugins. are there anything there?

---

### Post by XeroCurve on 2006-07-24
No, I dont even have the directory "Firefox"

---

### Post by Ziox on 2006-07-24
> **XeroCurve said:**
> No, I dont even have the directory "Firefox"

well...can you start firefox?

EDIT: If you are missing that directory, then firefox shouldn't start, and that would explain why Automatix didn't install the plugins, it can't find the folder!

---

### Post by XeroCurve on 2006-07-24
Yes, Firefox surfs the web fine.

---

### Post by Ziox on 2006-07-24
sorry our post must've crossed, enter terminal and input:

whereis firefox

and paste the output here

---

### Post by XeroCurve on 2006-07-24
Here it is:

firefox: 
/usr/bin/firefox.ubuntu 
/usr/bin/firefox 
/usr/bin/X11/firefox.ubuntu 
/usr/bin/X11/firefox 
/usr/share/man/man1/firefox.1.gz

Alson one other question when I go to Dapper will all this have to be done again?

---

### Post by Johnsie on 2006-07-24
no, your firefox settings will stay when you upgrade.

---

### Post by Ziox on 2006-07-24
> **XeroCurve said:**
> Here it is:

firefox: 
/usr/bin/firefox.ubuntu 
/usr/bin/firefox 
/usr/bin/X11/firefox.ubuntu 
/usr/bin/X11/firefox 
/usr/share/man/man1/firefox.1.gz

Alson one other question when I go to Dapper will all this have to be done again?

navigate to the folder /usr/bin and right click on firefox, check where it is targeting...then navigate to that folder and check the plugins folder in that folder

---

### Post by XeroCurve on 2006-07-24
Just in case I forget, I really appreciate the help =) I have done tech support and know how it can be, but obviously im the noob (At least with linux). =)

---

### Post by XeroCurve on 2006-07-24
OK there is a folder there in:

/opt/firefox/plugins

this is whats in it:

flashplayer.xpt
libflashplayer.so
libjavaplugin_oji.so
libjavaplugin.so
nphelix.so
nphelix.xpt
nppdf.so

---

### Post by Ziox on 2006-07-24
these are the files i have in my plugin folder, it looks like that you are missing mplayer, if you want to play media within browser, other things look like they are all installed...

flashplayer.xpt  
      mplayerplug-in-gmp.so 
  mplayerplug-in-rm.so 
  mplayerplug-in-wmp.xpt
libflashplayer.so    
  mplayerplug-in-gmp.xpt 
 mplayerplug-in-rm.xpt 
 mplayerplug-in.xpt
libjavaplugin.so   
    mplayerplug-in-qt.so  
  mplayerplug-in.so
libunixprintplugin.so 
 mplayerplug-in-qt.xpt  
 mplayerplug-in-wmp.so

go to automatix and install mplayer and its plugins

---

### Post by XeroCurve on 2006-07-24
OK this seems wierd, when I start Automatix all the boxes are unchecked, is this the way its supposed to be. Anyway I checked the Mplayer and tried to install it and it tells me this:

mencoder-386 has no installation candidate

It says that it may be old, obsolete, missing or replaced with mencoder-k6, mencoder-custom or mencoder-586

---

### Post by Ziox on 2006-07-24
yeah..all the boxes are unchecked..it doesn't display which software you have installed, but i think it keeps a log, if you are interest you can search for it.

as for your problem with mplayer...you can try manually installing other mencoder, such as mencoder-586.  Or you can go to the automatix thread, and ask them about your problem. I'm not an expert at automatix at all...so...

but keep posting here until you solve the problem, i'm sure some can and will solve it.

---

### Post by XeroCurve on 2006-07-24
Anyway of installing the plugin is fine with me. I just used Automatix because it seemed to be the easy way to do them all at the same time, but if anyone else has a way of installing the Mplayer plugin please let me know =)

---

### Post by randcoop on 2006-07-24
Automatix is a great helper program, but it doesn't do anything you can't do yourself.  To get the mplayer plugin, you can run ```
sudo apt-get install mozilla-mplayer
```.

As far as I can tell from my own setup and from the information in Adept, you don't need mencoder for mplayer.

The plugins for Firefox can end up in a variety of places, including your profile directory in ~/.mozilla.

To determine which plugins Firefox is actually using, enter:```
about:plugins
```in the Firefox URL address bar.

Another approach to playing streams and the like from Firefox is to use an extension called Media Connectivity.  You can configure it to start the programs themselves when certain file types are encountered.  It's very flexible and if you uncheck a particular program start, Firefox reverts to the plugins it has in the plugin directories.  This gives you the best of both worlds: when the web site mandates a plugin, you can use it, but when the plugin won't work, often the full program will.  Media Connectivity will start that program.

You might also want to install Kmplayer; it's a very strong GUI for mplayer and I find that it buffers much more quickly.  When you use the mozilla-mplayer plugin, it will start mplayer itself, but if you configure  Media Connectivity to run kmplayer, then that will start.

I hope some of these suggestions prove helpful.  Multimedia remains a weakness for all of us who use Linux and I fear that we're only going to fall further behind.  While many Linux users disdain anything they can't do under Linux, many others would prefer having the ability to seamlessly run streams from websites whether they are built for Windows or not.

---

### Post by XeroCurve on 2006-07-25
OK, so I did the ```
about:plugins
``` and it appears that Firefox does not have mplayer plugin installed. I have tried to install it numerous times to no avail. The strange thing is I have checked numerous locations and the correct plugins are in this folder:

/usr/lib/firefox/plugins

but not:

/opt/firefox/plugins

I am not sure if this is the location that they are supposed to be in or not. I tried to set a sym link via another poster and it didnt seem to work. I am kind of at my wits end on this one. If you could explain how to do the Media Connectivity I will try that. Thanks.

---

### Post by Ziox on 2006-07-25
the firefox plugins are mearly links to the actual app, so if you can make links and then move them to the correct folder, then firefox should have all the plugins it needs...I'll make a list of where my links link to...

EDIT: Ok, here they are:

flashplayer.xpt - /usr/lib/flashplugin-nonfree/flashplayer.xpt
mplayerplug-in-gmp.so - /usr/lib/mozilla/plugins/mplayerplug-in-gmp.so
mplayerplug-in-rm.so - /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
mplayerplug-in-wmp.xpt - /usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt
libflashplayer.so - /usr/lib/flashplugin-nonfree/libflashplayer.so
mplayerplug-in-gmp.xpt - /usr/lib/mozilla/plugins/mplayerplug-in-gmp.xpt
mplayerplug-in-rm.xpt - /usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt
mplayerplug-in.xpt - /usr/lib/mozilla/plugins/mplayerplug-in.xpt
libjavaplugin.so - /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
mplayerplug-in-qt.so  - /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
mplayerplug-in.so - /usr/lib/mozilla/plugins/mplayerplug-in.so
libunixprintplugin.so - (resides in the current folder)
mplayerplug-in-qt.xpt - /usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt
mplayerplug-in-wmp.so - /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so

---

### Post by randcoop on 2006-07-25
With regard to the plugins, it's true that Firefox looks in a variety of places for plugins, but you really want your plugins in either /usr/lib/mozilla/plugins or /home/[username]/.mozilla/plugins.

To install Mediaplayer Connectivity, go to [HTML]https://addons.mozilla.org/firefox/446/[/HTML] and click on Install Now .  You'll need to re-start Firefox after you've installed in order for the installation to take effect.

---

