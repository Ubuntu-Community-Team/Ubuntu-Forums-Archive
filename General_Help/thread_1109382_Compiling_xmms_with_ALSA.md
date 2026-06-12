---
title: "Compiling xmms with ALSA"
date: 2009-03-28
forum: General Help
---

### Post by UbunUsr on 2009-03-28
Hello,

I decided to compile xmms and i configured it with following option:

```
./configure --prefix=/opt/xmms
```

and at the i get this:

```
Configuration:
  Install path:               /opt/xmms
  Build OSS plugin:           yes
  Build esd plugin:           no
  Build Solaris plugin:       no
  Build BSD Sun plugin:       no
  Build ALSA plugin:          no
  Build mikmod plugin:        no
  Build Ogg Vorbis plugin:    no
  Build OpenGL plugins:       yes
  Pthread flag:               -lpthread
  Use one plugin dir:         no
  Allow user plugin dir:      yes

```

What i want is to build ALSA plugin.I read ./configure --help,and i saw:
--with-alsa-prefix and --with-alsa-inc-prefix but i'm unsure what directory to put?Thanks in advance....

---

### Post by cariboo on 2009-03-29
If I remember correctly xmms already has alsa support builtin, you can get a deb [here]("http://www.pvv.ntnu.no/~knuta/xmms/").

Jim

---

### Post by jocko on 2009-03-29
> **UbunUsr said:**
> Hello,

I decided to compile xmms and i configured it with following option:

```
./configure --prefix=/opt/xmms
```and at the i get this:

```
Configuration:
  Install path:               /opt/xmms
  Build OSS plugin:           yes
  Build esd plugin:           no
  Build Solaris plugin:       no
  Build BSD Sun plugin:       no
  Build ALSA plugin:          no
  Build mikmod plugin:        no
  Build Ogg Vorbis plugin:    no
  Build OpenGL plugins:       yes
  Pthread flag:               -lpthread
  Use one plugin dir:         no
  Allow user plugin dir:      yes

```What i want is to build ALSA plugin.I read ./configure --help,and i saw:
--with-alsa-prefix and --with-alsa-inc-prefix but i'm unsure what directory to put?Thanks in advance....
Are you sure you have all dependencies installed. I would guess you need the package "libasound2-dev" to build the alsa plugin.

Why do you want to compile xmms? That project was abandoned years ago.
Is it just that you want a simple music player without any silly database engine or library functions?
In that case, have you tried audacious? It's a fork of bmp (another dead project), which was a fork of xmms. Audacious is still actively developed, it is still just a music player similar to xmms, bmp and old winamp 2. It uses winamp 2 skins (just like xmms/bmp), but it's using gtk2 instead of gtk1 (so its menus, preferences window and file browser windows use the same theme as the rest of gnome), and... it's in the repos:```
sudo apt-get install audacious
```

---

### Post by UbunUsr on 2009-03-30
@jocko

Thank you very much, the problem was missing dependencies i.e libasound2-dev.

> 

Why do you want to compile xmms? That project was abandoned years ago.


No any special reason,just learning and doing it for fun ;)
Oh,i tried audacious,i compiled it too :)
Thanks again and cheers...

---

### Post by RabidWeezle on 2009-08-07
I think many people don't care if the app looks exactly like the rest of their desktop if they love the program and are familier with it (and it's the only one that lets us use our old favorite winamp skins and has a full equalizer), then why question why they want to compile it? It's pretty simple why they want to compile it, it should have never been taken out of the repo in the first place. Just because it's old doesn't mean it's not loved. Like everytime I start a new system I will sit there and compile quakeforge, even though it hasn't seen an update in a couple years, doesn't mean it's not my favorite quake 1 client. Ever think that the reason they stopped updating xmms was because the old saying, "If it's not broke, don't fix it".

---

### Post by jocko on 2009-08-07
> **RabidWeezle said:**
> I think many people don't care if the app looks exactly like the rest of their desktop if they love the program and are familier with it (and it's the only one that lets us use our old favorite winamp skins and has a full equalizer), then why question why they want to compile it? It's pretty simple why they want to compile it, it should have never been taken out of the repo in the first place. Just because it's old doesn't mean it's not loved. Like everytime I start a new system I will sit there and compile quakeforge, even though it hasn't seen an update in a couple years, doesn't mean it's not my favorite quake 1 client. Ever think that the reason they stopped updating xmms was because the old saying, "If it's not broke, don't fix it".
Read the date of the last post in the thread and let it die in peace. 
I didn't question his right to compile xmms, I was just curious why he wanted to compile xmms when a perfectly good replacement is in the repos. Audacious uses winamp skins, has an equalizer and the most important part (the audio playback engine) is still based on xmms code, so audacious is what xmms would have been if it would have been actively developed the last few years... I'm sure the decision to quit packaging xmms has been discussed in other threads already, so there's no point starting up again.

---

