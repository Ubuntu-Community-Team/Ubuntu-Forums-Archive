---
title: "No video thumbnail previews in nautilus"
date: 2009-11-25
forum: Desktop Environments
---

### Post by bburkert517 on 2009-11-25
Hi, I was messing around in the preferences of nautilus and clicked on compact view and then learned I didn't like that view so I switched it back to normal but ever since then I have been unable to view my video thumbnail previews. I have done some searching and have have tried reinstalling totem and totem-common, I have installed totem-gstreamer, I have all of the proper codecs installed and I have tried deleting ~/.thumbnails but I have had no luck. None of the settings under preferences -> preview seem to have any effect on it. I am throughly stumped :confused:

Any help would be appreciated thanks

---

### Post by Minsky on 2009-11-26
In Nautilus, go to **Edit>Preferences** again and set **Show_thumbnails** to **Always**, and the limit to 4GB. Exit Nautilus and go to **home directory/.thumbnails/fail/gnome_thumbnail-factory** and delete everything in there to force  Nautilus to rebiuld the thumbnails.
 If that doesn't work then there's a couple more things that you can try. In **gconf-editor** go to **apps>nautilus>preferences**. in the right hand pane set the value of **thumbnail_limit** to -1. Also in **gconf-editor**, go to **desktop>gnome>thumbnailers** and scroll down until you see a list of settings in the format of **video@####**. Click on each one and make sure that it's enabled. Hopefully, one of those methods will solve your problem. if not, then I'm as stumped as you are.

---

### Post by esc1 on 2009-12-13
Tried all of this. Still doesn't work for me. :/

---

### Post by nutznboltz on 2009-12-13
Is /usr/bin/totem-video-thumbnailer installed on your system?

Do you get this:

```
$ ls -l /usr/bin/totem-video-thumbnailer
ls: cannot access /usr/bin/totem-video-thumbnailer: No such file or directory
```

---

### Post by esc1 on 2009-12-14
Nope.

```
-rwxr-xr-x 1 root root 169472 2009-11-11 04:15 /usr/bin/totem-video-thumbnailer
```

---

### Post by esc1 on 2009-12-15
Bump.

---

### Post by esc1 on 2009-12-30
It was a simple fix. Just wanted to reply in case any noob like me has the issue. I like to use vlc but totem creates the video previews. My totem codecs were not up to speed.

---

### Post by tenjin1 on 2010-03-10
So what exactly was the fix?
there is no totem codecs package I can find per esc1 post.

I'm having the same issue. I don't want totem installed but want my video thumbnails to work. I've tried ffmpegthumbailer and also doesn't work. Everytime I go to install something that has to do with totem it wants to install the whole totem package again which I don't want totem but do want video thumbnails.

help?

---

### Post by kelvin.illa on 2010-03-13
> **tenjin1 said:**
> So what exactly was the fix?
there is no totem codecs package I can find per esc1 post.

I'm having the same issue. I don't want totem installed but want my video thumbnails to work. I've tried ffmpegthumbailer and also doesn't work. Everytime I go to install something that has to do with totem it wants to install the whole totem package again which I don't want totem but do want video thumbnails.

help?

I second this; I had to re-install totem to get video thumbnails back. Is there another way?

---

### Post by benerivo on 2010-03-13
You can try nailer, which relies on having mplayer installed...

[http://sites.google.com/site/kdekorte2/nailer](http://sites.google.com/site/kdekorte2/nailer)

---

### Post by garrison on 2010-04-08
> **benerivo said:**
> You can try nailer, which relies on having mplayer installed...


It seems to also rely on having Fedora installed, but I did get it working:

[LIST]
[*]sudo aptitude install gnome-devel
[*]./configure; make && sudo make install 
[*]cp nailer.schemas /usr/share/gconf/schemas/
[*] sudo aptitude install gnome-xcf-thumbnailer
[/LIST]

Despite removing failed thumbnails and restarting nautilus, it didn't work until I installed gnome-xcf-thumbnailer, which presumably performs a step I missed.

Without ./configure options, these two files are installed in the wrong place:

/usr/local/etc/gconf/schemas/nailer.schemas
/usr/local/share/thumbnailers/video-thumbnailer.desktop

---

### Post by superconductor on 2010-05-05
Assuming you have not uninstalled the default totem package and reinstalled totem-xine, the following procedure should work. It only requires you to install packages available in the standard Ubuntu repositories and does not require you to compile anything manually, as described above. 

1. Open file manager. 
2. Edit->Preferences->Preview. Change preferences as required. 
3. Close file manager and open terminal.
4. Run the following command to install the necessary packages. 
> $ sudo apt-get install ffmpeg ffmpegthumbnailer gstreamer0.10-ffmpeg 5. Remove old thumbnails.
> $ rm ~/.thumbnails/fail/gnome-thumbnail-factory/*
$ rm ~/.thumbnails/normal/*6. Open the file manager and enjoy your new thumbnails!

Please post back when / if this works. I think I've listed the minimum packages required for thumbnails using the default totem with gstreamer (NOT xine), but I might have missed a few.

---

### Post by dee4life2005 on 2010-05-10
> **superconductor said:**
> Assuming you have not uninstalled the default totem package and reinstalled totem-xine, the following procedure should work. It only requires you to install packages available in the standard Ubuntu repositories and does not require you to compile anything manually, as described above. 

1. Open file manager. 
2. Edit->Preferences->Preview. Change preferences as required. 
3. Close file manager and open terminal.
4. Run the following command to install the necessary packages. 
5. Remove old thumbnails.
6. Open the file manager and enjoy your new thumbnails!

Please post back when / if this works. I think I've listed the minimum packages required for thumbnails using the default totem with gstreamer (NOT xine), but I might have missed a few.

I had un-installed totem and was using VLC instead, and my video thumbnails weren't working. After trying the above commands they have returned. Haven't checked all codecs yet, but it looks promising.

Thanks.

\\:D/

---

### Post by fritzm on 2010-05-20
Thanks a lot - everything you list was installed except for ffmpegthumbnailer . Installing that and deleting the files fixed the problem. I had a new default installation of 10.4, so I think this is a bug in the default configuration.

Fritz

---

### Post by ephman on 2010-11-03
superconductor thank you.  worked like a charm!

thanks for the bandwidth,
ephman

---

