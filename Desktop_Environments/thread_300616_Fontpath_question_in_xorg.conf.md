---
title: "Fontpath question in xorg.conf"
date: 2006-11-15
forum: Desktop Environments
---

### Post by svenyun on 2006-11-15
The xorg.conf that Ubuntu sets up has its Fontpath section listed like this:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

But /usr/share/X11/fonts is an invalid dir, it's really /usr/share/fonts/X11 (at least it is on my system) which hasn't been changed from the normal install.

So what's up, why is it listing the wrong dirs?  Only reason I noticed is the errors in the X log stating it couldn't find any of these dirs.

---

### Post by eeried on 2006-11-16
i've noticed the same thing and it is not new. I had in Libranet 2.7 (a couple of years ago) and in Debian Etch + Sid very recently.

No idea why and would be interested to learn something about this.

Ithis wrong font path thing is annoying but it doesn't seem to matter at all. It probably slows down the boot up.

---

### Post by leikao on 2006-11-16
It's all right in my Ubuntu. I can find the fonts dir in the /usr/share/X11 folder.

/usr/share/X11$ ls
fonts  locale  XErrorDB  XKeysymDB

---

### Post by svenyun on 2006-11-16
Hmm, my install of Edgy has this

/usr/share/X11$ ls
locale  rgb.txt  XErrorDB  XKeysymDB

No fonts dir here.

As I said there is a /usr/share/fonts/X11 though

/usr/share/fonts$ ls
fonts.cache-1  truetype  type1  X11

/usr/share/fonts$ ls X11
100dpi  75dpi  encodings  fonts.cache-1  misc  Type1  util

Don't understand why the FontPaths in the default xorg.conf would have this screwed up...

I installed from the 6.10 LiveCD.  Nothing was changed from the default install except for installing nvidia driver and Thunderbird.

---

