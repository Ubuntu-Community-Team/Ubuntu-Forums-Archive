---
title: "Where can I find xine codecs?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by drummer4lifex on 2006-06-07
Hello, I searched and found out that the reason my Totem can't play .mp3's and .avi's is because I don't have the w32codec or the xineextracodecs installed. However, when I went to the xine website, I could only find the download for the xine engine. Also, when I get these, is there any special way to install them?

---

### Post by vseehua on 2006-06-07
try synaptic package manager under menu->system->administration and search for the packages... you will have to enable the multiverse repositories though... hope that helps... ;)

---

### Post by ubman on 2006-06-07
[QUOTE=drummer4lifex]Hello, I searched and found out that the reason my Totem can't play .mp3's and .avi's is because I don't have the w32codec or the xineextracodecs installed. However, when I went to the xine website, I could only find the download for the xine engine. Also, when I get these, is there any special way to install them?[/QUOTE]



I found everything that i needed Below:) 

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by tonyr on 2006-06-07
I don't know about the **xineextracodecs**.  To get the **w32codecs**, add the lines
```

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

to **/etc/apt/sources.list**, then in a terminal do
```

sudo apt-get update
sudo apt-get install w32codecs

```

or **update** in **synaptic** or **adept** or whatever tool you use to install 
packages, and the **w32codes** package should show up in the list.

---

### Post by vseehua on 2006-06-07
i think it's easier to use automatix or BUMPS or EasyUbuntu instead... you can locate them under the 3rd party projects at the main page. 

I prefer Automatix, since it sets up pretty much everything for me... ;)

enjoy.. ;)

fyi, libxine-extracodecs provides the infratructure for xine to support w32codecs, or so i had read from it's package description... without it, the media files just can't be played...

---

### Post by tonyr on 2006-06-07
Just to be redundant here, the package for the xineextracodes is **libxine-extracodecs**.
You have to enable the **multiverse** repositories.  There is a way to do that in 
**synaptic**, if that is the tool you are using.  Otherwise, edit **/etc/apt/sources.list**
and uncomment the lines for dapper universe and multiverse if they are not already.
Then you can install the **libxine-extracodes** package.

---

### Post by scxtt on 2006-06-07
all i did was go to [http://www1.mplayerhq.hu/design7/codecs.html](http://www1.mplayerhq.hu/design7/codecs.html) and download the "all" bzip'd tar and extract it to /usr/lib/codecs and pointed to that directory w/in xine's config ...

don't know if that'll impact totem at all - i've never really liked totem ...

i've just decided to skip the whole repository all together when it comes to codecs ...

hell, i've even gotten away w/ having xine point to /media/windows/system32 (or whatever the path to where all the codecs were in windows) and it worked like a charm ... but i'm window-less presently :-D

just a thought ...

---

### Post by drummer4lifex on 2006-06-08
Thanks a lot!!! :mrgreen:

---

