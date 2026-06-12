---
title: "libxine 1.1.1 + xine-ui 0.99.4 trouble"
date: 2006-02-25
forum: Desktop Environments
---

### Post by anton123 on 2006-02-25
Hello,

When I was using Ubuntu 5.04 all I did was:

1)download the latest tarballs of libxine and xine-ui from [www.xinehq.de](www.xinehq.de)
2)compile them
3)making *.deb packages using checkinstall that exists in the Ubuntu repositories

Packages were built and installed, I was able to use xine without problems. The story is different with ubuntu 5.10

1)download the latest tarballs of libxine and xine-ui from [www.xinehq.de](www.xinehq.de) (libxine 1.1.1 and xine-ui 0.99.4)
2)download build-essential and whatever packages I was prompted by the compilation of libxine (here I don't know what packages to get for sure, yet I was just as uncertain when I was using Ubuntu 5.04 and things somehow worked out)
3)xine-ui was complaining about not finding version >= 1.0.1 of libxine even if version 1.1.1 was installed. I had to create ld.conf.so in /etc/bin as prompted by the compilation and added /usr/lib path to libxine. Here, I don't know what I am doing. Another option was to set path variable and $prefix but since I am new to Linux I have no idea what to do and how to do it, so I did what I stated. This step 3) was not a problem I had in Ubuntu 5.04.
4)compile them. Now xine-ui was compiling after I did the mentioned steps in step 3.
4)making *.deb packages using checkinstall that exists in the Ubuntu repositories
5)xine 0.99.4 launches but the volume slider is disabled. I click on it and a volume level is selected. When playing a media file there is no sound.
6)I go to advanced interface and move volume slider higher and select option to remember volume level as set
7)I close xine
8)I open xine. The volume slider is yet again disbaled and I have to again click on it to select a volume level. Yet there is never sound.
9)sometimes, xine becomes unstable and I have to shut it down from either konsole or the System Monitor.
10)I have redone steps 1 to 9 countless times but nothing changes.

So, what is going on here? Am I an idiot or what? I did nothing different from Ubuntu 5.04 compilation & installation of both libxine and xine-ui.
To those who have already compiled a newer version of both libxine and xine-ui than those in the Ubuntu repositories, what and how did you do it? I need step by step guidance as to how to compile these two libraries and make *.deb packages to install them. I am really frustrated!

---

### Post by Spano on 2006-02-26
I think Xine install is a pain too!  Figuring out that I needed to create an ld.so.conf is what cracked the problem for me, here is a copy of mine:
```
# Begin /etc/ld.so.conf

/usr/local/lib
LIBDIR

# End /etc/ld.so.conf
```
Here is a link to the most concise and simple guide I could find on the net:
[http://davis.lbl.gov/Manuals/XINE/howto-3.html](http://davis.lbl.gov/Manuals/XINE/howto-3.html)
And two ideas from a relative noob:
Have you run ```
xine-check
``` from terminal on your current install?
If you compile again consider skipping making the .deb packages.
I wish you luck.  If you can get it working it's really a nice media player.

---

