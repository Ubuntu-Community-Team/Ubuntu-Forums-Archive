---
title: "How to read Chinse"
date: 2006-10-31
forum: Desktop Environments
---

### Post by satimis on 2006-10-31
Hi folks,

ubuntu-6.06.1-LAMP-server-amd64
xfce4

Please advise;
1) how to read Chinese
2) how to edit Chinese

Because this is a server, few X-packages installed only to satisfy browsing on Internet

$ cat /etc/X11/xorg.conf```

.....
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/X11/fonts/encodings"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
.....

```

Just ran;
$ sudo apt-get install xfonts-intl-chinese
$ sudo apt-get install xfonts-intl-chinese-big
still could not read Chinese.

Please help.  TIA.


B.R.
satimis

---

### Post by wenty on 2006-11-01
Have you tried adding the Chinese language support? 
To add Chinese support:
System->Administration->Language Support 
In the supported language section choose Chinese. I think after that(maybe a relogon is needed) it will display Chinese characters correctly.

And if you want to make the Chinese fonts look nicer or if you want to input Chinese in English local you can follow this thread (written in Chinese):
[http://forum.ubuntu.org.cn/about15039.html](http://forum.ubuntu.org.cn/about15039.html)

---

### Post by satimis on 2006-11-01
Hi wenty,

Tks for your advice and URL


> To add Chinese support:
System->Administration->Language Support

Xfce4 which I'm running is a light weight desktop.  It does not have such items.  Is there command line instead?

> And if you want to make the Chinese fonts look nicer or if you want to input Chinese in English local you can follow this thread (written in Chinese):
[http://forum.ubuntu.org.cn/about15039.html](http://forum.ubuntu.org.cn/about15039.html)I can't read this link because no Chinese support here, only symbols displayed.

B.R.
satimis

---

### Post by wenty on 2006-11-01
Hi satimis, I am a green hand. I am sorry that I don't know how to use commod to do this.

---

