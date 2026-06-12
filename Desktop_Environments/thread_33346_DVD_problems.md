---
title: "DVD problems"
date: 2005-05-10
forum: Desktop Environments
---

### Post by daryl on 2005-05-10
I am having a few DVD problems.

I place a CD into the CD drive [/dev/hda] and I get an icon on the desktop. This links to `media:/hda' which is fine, I click it and it plays the songs. If I place a DVD into the DVD drive [/dev/hdb] I get an icon on the desktop. If I double click this it sends me to `media:/hdb' which then gives the error "Malformed URL" when Konqueror tries to open it. If I right click the disc icon it says that the DVD is empty, and it also confirms that it is pointing to /dev/hdb. If I go to the command prompt and type `mount /dev/hdb' then the DVD gets mounted, and I can successfully read the contents using 'dir' or 'ls'. 

If I try and play a DVD in Kaffeine then I get the error "The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error reading NAV packet.)". This same thing happens if I try and play it whilst being logged in as root so it is not to do with the permissions.

If I try and play a DVD in Kaffeine, but by running it from the command line, I get another error, "kaffeine: ERROR: KXineWidget: Can't find/play logo file!". It does spam several lines above that with contents like "libdvdnav: DVD Title: STARSKY_AND_HUTCH" and "libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a". This suggests that maybe there is a package that I am missing for DVD playback. I installed libdvdcss, and I installed the win32 codecs. Running 'kaffeine -w' from the command prompt says that they are found.

I really don't know what to make of all this, so I came looking for assistance. Any help will be greatfully appreciated.

Thanks,

Daryl.

---

### Post by daryl on 2005-05-10
I have solved the DVD media not playing:

```
If you would like full DVD support, run the following script: /usr/share/doc/libdvdread3/examples/install-css.sh
```

As is so nicely says [here](http://www.ubuntulinux.org/wiki/RestrictedFormats).

As for the "Malformed URL" error, it's still there.

---

