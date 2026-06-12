---
title: "Compiz fusion plugin always disabled at startup"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by KhaaL on 2007-10-30
My show desktop and resize plugins are always disabled at startup with CF (aswell the opacity settings in the general settings).

I only have the packages provided by the repos, and I used a brand new settings file in my ./config folder.

How can I find out what's wrong? it's extremly annoying having to start ccsm up at every startup in order to be able to resize windows

---

### Post by jayaramk on 2007-10-30
just goto
system->preferences->sessions and click on add..

give name and compiz
and launcher compiz --replace


thats it if u wanna check restart ur system!!!!

---

### Post by KhaaL on 2007-10-30
My compiz startsup with "compiz --replace --loose-binding -c emerald &"

---

### Post by KhaaL on 2007-10-30
Sorry about the bump...

---

### Post by Zorael on 2007-10-30
Do you save your profile in a flat-file configuration backend? (ccsm -> Preferences)

I heard other backends (such as the KDE config one) may have a hard time saving settings, where flat-files are more reliable.

Just export your profile first, then switch to flat-file, and import it again to migrate your setup.

---

### Post by KhaaL on 2007-10-30
I've tried both flatfile and KDE-backend with no diffrence.

---

### Post by Zorael on 2007-10-30
Isn't it possible to pass plugin names as arguments to compiz to force them to be loaded? Like, 'compiz --replace --ignore-desktop-hints --loose-bindings showdesktop resizewindows'. The trick would be to figure out the real names of the plugins, heh.

edit:
```
zorael@azrael:~$ cd /usr/share/compiz
zorael@azrael:/usr/share/compiz$ ls *.xml
addhelper.xml     fadedesktop.xml  plane.xml        svg.xml
animation.xml     fade.xml         png.xml          switcher.xml
annotate.xml      firepaint.xml    put.xml          text.xml
bench.xml         fs.xml           reflex.xml       thumbnail.xml
blur.xml          gconf.xml        regex.xml        trailfocus.xml
clone.xml         gears.xml        resizeinfo.xml   video.xml
colorfilter.xml   glib.xml         resize.xml       vpswitch.xml
core.xml          group.xml        ring.xml         wall.xml
crashhandler.xml  imgjpeg.xml      rotate.xml       water.xml
cubecaps.xml      ini.xml          scaleaddon.xml   widget.xml
cubereflex.xml    inotify.xml      scalefilter.xml  winrules.xml
cube.xml          mblur.xml        scale.xml        wobbly.xml
dbus.xml          minimize.xml     screenshot.xml   workarounds.xml
decoration.xml    move.xml         shift.xml        zoom.xml
expo.xml          neg.xml          showdesktop.xml
extrawm.xml       opacify.xml      snap.xml
ezoom.xml         place.xml        splash.xml
```

---

### Post by nartooki on 2007-10-30
i was also having this problem with a few plugins (mostly window resize) and somehow it isn't a problem anymore. what i did was go into the prefs and disable automatic plugin management, manualy push over the ones i needed, export and then import the config file. before i logged out/ back in i also changed my emerald theme, but i dont know if that had anything to do with the fix. good luck!

---

### Post by KhaaL on 2007-10-31
nartooki, I tried your suggestion but it STILL act irrational! it is as it randomly unloads plugins now... last thing that just happened to me was the app switcher and later the decoration plugin being unloaded!

Urgh, someone make it stop! :(

---

### Post by ch_123 on 2007-10-31
> **Zorael said:**
> Do you save your profile in a flat-file configuration backend? (ccsm -> Preferences)

I heard other backends (such as the KDE config one) may have a hard time saving settings, where flat-files are more reliable.

Just export your profile first, then switch to flat-file, and import it again to migrate your setup.

I tried changing from KDE to Flat-file. Yet, when I exit out of the programme and go back in, its back to KDE! It seems to be completely ignoring all the changes Im making to it, anyone know whats going on? (I have tried reinstalling it, but that failed)

---

### Post by Zorael on 2007-10-31
It couldn't be a permissions problem, right?

I've had a similar issue with Dolphin, after I'd opened it as sudo once by mistake (doh). I don't know where the KDE backend settings reside, but I think you'd notice it in other applications as well, were it so.

This is probably dangerous and it may mess up something, but you could try this. Replace username with your username.
```
$ sudo chown -Rc username ~/.*
$ sudo chown -R root ~/.gnupg
$ sudo chown -R root /home
```

---

### Post by KhaaL on 2007-11-01
I thought also the other day that it might have been a ownership issue... well, I just did a "ls -lR |less" to see the ownership of everyfile in my ~/ (phew, there was LOTS!!). (Un?)fortunatly, they was all set to me so appearently there isn't anything that can be done there... got more ideas Zorael? :)

---

### Post by Zorael on 2007-11-01
Are they still disabled if you start compiz with this command?

```
$ compiz --replace --loose-binding -c emerald **showdesktop resize** &
```

---

### Post by KhaaL on 2007-11-02
yea it worked, but the resize plugin changed itself from "outline" to something else. When I opened ccsm to check on that plugin, it didn't matter what resize mode I chose, they all act as the normal setting. For some reason, if i disable resize plugin, all works well again. I ran ccsm through the konsole to try and get any info, but it didn't give any warning messages at all.

I ran CF through the console, but it didn't give much for me to go on
```

[1] 9572
khaal@Xeraphim:~$ Checking for Xgl: not present.
Detected PCI ID for VGA: 03:00.0 0300: 10de:0290 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (core) - Warn: pixmap 0x1c02e1e can't be bound to texture
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop

```


I have the feeling that some of the plugins aren't compatible with eachother... But I don't know how to confirm this. 

and strangest of all, why am I all alone in having these issues?!  :confused: :-?

EDIT: oh, and I lost the opacity settings in general options again. screensaver is transculent again! groan...

---

### Post by Zorael on 2007-11-02
I think '-c emerald' is a deprecated argument, a remnant from Beryl, so I think you can omit that.

Anyway, you could try purging Compiz and Emerald, and then reinstalling. It fixes stuff for some, apparently. If that doesn't work, heck, I don't know what will. :>

```
$ sudo apt-get **purge** compiz* libcompiz* libdeco* emerald* libemerald*
```

This may help, too, but you'd lose your profile. Just make sure to start out in flat-file again, when you rebuild a new one. From the start.

```
$ rm -r ~/.config/compiz
```

---

### Post by KhaaL on 2007-11-09
You, my friend, are a man with a magic finger. I did purge all packages and reinstalled all of them again (except two kde specific packages) and it's working after X-restart, and after a reboot!

...let's hope it will not freak out after a while :D

thanks for the help again

---

### Post by KhaaL on 2007-11-10
well, i just *knew* it would be too good to be true if this just worked:rolleyes: 

The water plugin is now always disabled at startup (so is showdesktop)... but at least the bottom-left hotcorner works. 

I guess I just have to live with it or try a diffrent desktop enviorment / distro in worst case.

---

### Post by Zorael on 2007-11-10
And you are running with a flat-file backend now?

If nothing else, add **water** to your ever-growing list of arguments. :>

Failing that, see if there's new developments in the terminal output errors.

---

### Post by KhaaL on 2007-11-10
Zorael, I start up CF by putting a link to it in ~/.kde/Autostart/ folder... is there a way to make it always start up in a console (in order to make it easier to see errors on startup?) I tried changing the command to "konsole compiz --replace --loose-binding emerald &" with no luck.

By the way, I always ran flat-file backend except for a small while when I tried a diffrent approach. I also noticed that my opacity settings are going haywire (screensaver & games are not always opaque...) I'm really out of ideas of what might cause this as I have a fresh install. I only had my old home folder intact on that install, but i removed the compiz profile... Grunt, I might have to remove my ~/.kde folder and see how it works then. I tried but I couldn't get myself use a diffrent DE, I'm weak like that! heh

Thanks for sticking to be my aid, Z.

PS. I still get a error "/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'", even though it does show up and work... is this normal behaviour?

---

