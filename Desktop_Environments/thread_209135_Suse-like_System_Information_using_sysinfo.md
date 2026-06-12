---
title: "Suse-like System Information using sysinfo:/ ?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by msak007 on 2006-07-04
I was looking at screenshots of Suse 10.1 the other day, and my brother is currently trying it out so I used his comp for a little just to get a feel for it. Overall I don't like SuSE (KDE) as much as Kubuntu and always keep coming back, but there's one thing I really liked about it: there's a "My Computer" shortcut on the Desktop that opens Konqueror with a "sysinfo:/" KIO-slave and it displays all the System Information. Here's a [screenshot]("http://shots.osdir.com/slideshows/slideshow.php?release=637&slide=26"):

My question is whether or not something like this is possible in Kubuntu? I searched everywhere and found little to no information on this. If anybody has any info on whether or not this is possible and how to achive it please let me know.

---

### Post by Jucato on 2006-07-04
Well, for one, the screenshot you linked to is just a plain, clean desktop, with no opened application, so I can't seem to see what you are talking about.

Secondly, those screenshots are SUSE 10.1 using GNOME, not KDE.

Anyway, what "system information" is being displayed by that sysinfo:/ kioslave in SUSE? If it's not in Kubuntu, it's probably a SUSE-only kioslave.

---

### Post by msak007 on 2006-07-04
I apologize for the mistake, I simply copied / pasted the URL of the screenshot I was looking at and didn't realize it doesn't go to the one I was referring to. The page itself is a slideshow of all the screenshots and must've gone to the first one, which like you said is a blank Gnome Desktop. [This]("http://shots.osdir.com/slideshows/original.php?release=637&slide=63") is what I was referring to. You can't really see the bottom because the window wasn't maximized and it was cut off, but the Display portion even shows you what driver you're using. I know there are plenty of ways to get the system info there (I use a SuperKaramba theme myself to get most of that info on my Desktop), but something centralized like this would be nice to have as an option. I kinda figured it was a SuSE-only thing, but thought I'd ask anyway in case somebody knew anything about it.

---

### Post by Jucato on 2006-07-04
Oh I see. That is indeed nice. Unfortunately, we (Kubuntu) don't have that, AFAIK. It's a purely SUSE-only thing. 

Side note: I wouldn't expect much from Kubuntu when it comes to KDE innovation. A sad fact, but true. Hopefully, things will be better in the future. Hopefully... (Take note, I'm a Kubuntu user, through and through. :D)

---

### Post by msak007 on 2006-07-04
I know what you mean about KDE innovation. It's a shame because Kubuntu really is a great distro, and I prefer Debian-based distros so I see myself sticking around for a long time. I started out with Breezy so I haven't seen all the changes from one release to the next as others who've been around from the start have, but I have hope that it'll get better with every release. Don't get me wrong, Dapper by no means disappointed (was MUCH better than Breezy) and has worked flawlessly for me (for the most part - most of the problems I've had are KDE-specific), but there are things I see other distros doing that I wish would be adopted.

---

### Post by mrmonkeyman on 2007-07-08
It is a kde application not suse only. It is called kio-sysinfo

---

### Post by mrmonkeyman on 2007-07-08
It is a kde application not suse only. It is called kio-sysinfo

---

### Post by Gremlinzzz on 2007-07-08
Is this it
[http://kde-look.org/content/show.php/KIO+Slave+sysinfo:+?content=58704&PHPSESSID=828c9b01f495a86cbd4fa499b6076ca](http://kde-look.org/content/show.php/KIO+Slave+sysinfo:+?content=58704&PHPSESSID=828c9b01f495a86cbd4fa499b6076ca)

---

### Post by shadyzay on 2007-07-19
1. download the deb package for your system from:
[INDENT][http://download.tuxfamily.org/kiosysinfo/Distro/Kubuntu/](http://download.tuxfamily.org/kiosysinfo/Distro/Kubuntu/)[/INDENT]
2. run:
```
sudo apt-get install kdelibs4c2a libacl1 libart-2.0-2 libattr1 libaudio2 libc6 libdbus-1-3 libfontconfig1 libfreetype6 libgcc1 libhal1 libhd13 libice6 libidn11  libjpeg62 libpcre3 libpng12-0 libqt3-mt libsm6 libstdc++6  libx11-6 libxcursor1 libxext6 libxft2  libxi6 libxinerama1 libxrandr2 libxrender1 libxt6 zlib1g
```
3. from the folder you put the downloaded file run ( replace the file name with the one you downloaded ):
```
sudo dpkg -i kio-sysinfo_1.7.1_i386.deb
```

now just open konqueror and test it ( sysinfo:/ )

ciao

---

### Post by amadeus266 on 2007-07-19
Does anyone know if there is something like that for Gnome? I like the info and layout but I prefer gnome over KDE.

---

