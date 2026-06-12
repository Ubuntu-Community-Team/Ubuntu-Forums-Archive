---
title: "Audacity huge Ugly fonts why?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by atasaRossios on 2006-06-19
Hi guys,
Anybody knows why Audacity has these ugly fonts?
Is it because uses GTK1?
Any Idea to make to this nice prog look also nice?

---

### Post by Perfect Storm on 2006-06-19
Aye, it's compiled with libgtk1. If you want to use GTK2 you need to compile it yourself.

---

### Post by atasaRossios on 2006-06-19
Thanks
I will give it a try

---

### Post by Perfect Storm on 2006-06-19
Get the beta version (1.30) the cvs version is broken at the moment.

You'll need

build-essential
libwxgtk2.6-dev
libmad0-dev
libsndfile1-dev
libvorbis-dev
libid3tag0-dev
libsamplerate0-dev
libportaudio-dev
libflac++-dev
libgtk2.0-dev

```
sudo apt-get install build-essential libwxgtk2.6-dev libmad0-dev libsndfile1-dev  libvorbis-dev libid3tag0-dev libsamplerate0-dev libportaudio-dev libflac++-dev libgtk2.0-dev
```

Before running ./configure you might look into ./configure --help if youwant to set some flags.

If you saved the source file to your desktop:
```
cd Desktop
tar zxvf audacity-src-1.3.0b.tar.gz
cd audacity-src-1.3.0b-beta
./configure
make
sudo make install
cd && audacity

```

---

### Post by atasaRossios on 2006-06-21
Thanks Man,
It did work the beta with libgtk2.0 see my screenshot.
[http://ubuntuforums.org/gallery/files/7/7/4/3/1/audacity_thumb.png](http://ubuntuforums.org/gallery/files/7/7/4/3/1/audacity_thumb.png)

I was wondering did you also have enabled PortAudio v19(alsa)?

thnx again....

---

### Post by Perfect Storm on 2006-06-21
No I didn't enable it, the libs for enable it was to old for dapper, so I took default....well I could just compile the newest lib, but since PortAudio v19 is still experimental I think it's not worth it.

---

### Post by PhrankDaChickenGeek on 2006-07-07
Thanks so much! I've been looking for a better-looking audacity! :-D

---

### Post by Kashirigi on 2006-08-24
I've compiled and installed both portaudio v19 and audacity using portaudio v19. Unfortunately, I still have no option for ALSA. If I try to remove libportaudio0 (v18), I get this:
libportaudio-dev
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-java-common
openoffice.org-math
openoffice.org-writer
python-uno
ubuntu-desktop

That's clearly a problem. How can I compile portaudio v19 to overwrite portaudio v18, so that I don't have this problem?

Thanks.

---

### Post by Paul_UK on 2006-09-04
Excellent - thanks.  It's still not quite perfect but it's MUCH better!  :)

---

### Post by wilberfan64 on 2006-11-04
Thanks for this HowTo.   It looks great!   Now I have to figure out why my .rm rips sounds so horrible...

---

### Post by backdoc on 2007-06-25
You might try this:  download the latest portaudio source, go to the audacity source and find the matching set of files under lib-src, recompile.  if this doesn't work, try installing libasound2-dev.

Read [this thread]("http://audacityteam.org/forum/thread/5110").

hth

> **Kashirigi said:**
> I've compiled and installed both portaudio v19 and audacity using portaudio v19. Unfortunately, I still have no option for ALSA. If I try to remove libportaudio0 (v18), I get this:
libportaudio-dev
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-java-common
openoffice.org-math
openoffice.org-writer
python-uno
ubuntu-desktop

That's clearly a problem. How can I compile portaudio v19 to overwrite portaudio v18, so that I don't have this problem?

Thanks.

---

