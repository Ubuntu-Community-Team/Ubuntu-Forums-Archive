---
title: "[SOLVED] Debian multimedia"
date: 2008-06-10
forum: Debian
---

### Post by Inxsible on 2008-06-10
What packages do we need to install in Debian in order to:
1) Get sound working
2) Get mp3s to play
3) Getting videos to play ( I have already installed libdvdcss2,libdvdread3 & libdvdnav4)
4) Getting videos to play in browsers - including flash and such.


Seems like in ubuntu you just search for the gstreamer and you were good to go. Is there a meta package like that in Debian as well.

---

### Post by SunnyRabbiera on 2008-06-10
there is a media repository for debian, though I forget its address...

---

### Post by Inxsible on 2008-06-10
> **SunnyRabbiera said:**
> there is a media repository for debian, though I forget its address...yeah its ```
deb http://www.debian-multimedia.org/ lenny main
```I have already added it. But what packages do we need? I don't want to have to install all 230 of them just for multimedia.

---

### Post by SunnyRabbiera on 2008-06-10
You can probably be selective, like if you need flash you can just install it in debian by using that repo...
it depends on what you want.

---

### Post by Inxsible on 2008-06-10
> **SunnyRabbiera said:**
> You can probably be selective, like if you need flash you can just install it in debian by using that repo...
it depends on what you want.I just want my music to play and my movies to play as well. What would be the packages that I would need to install?

---

### Post by davtaine on 2008-06-10
> **Inxsible said:**
> I just want my music to play and my movies to play as well. What would be the packages that I would need to install?

Install w32codecs

---

### Post by Inxsible on 2008-06-10
> **davtaine said:**
> Install w32codecsNope still doesn't work :(

---

### Post by CREEPING DEATH on 2008-06-10
mp3s played out of the box last debian install... maybe gstreamer plugins or something?  I haven't used Debian on a desktop in a while though.

CD

---

### Post by CJ56 on 2008-06-10
Have you checked out the Debian Wiki? I'm running Etch & there are a bunch of things the Wiki suggests you install:

aptitude install gstreamer0.8-plugins gstreamer0.8-misc ffmpeg gstreamer0.10-ffmpeg-full sox toolame vorbis-tools lame lame-extras faad w32codecs libdvdcss2 totem-xine

Which I did & everything works fine - I use Audacious to play Mp3s, WAVs etc. VLC for everything else - Audacious is in the Debian repos, VLC I think you just get off their webpage

Hope this helps

---

### Post by kerry_s on 2008-06-10
> **Inxsible said:**
> What packages do we need to install in Debian in order to:
1) Get sound working
2) Get mp3s to play
3) Getting videos to play ( I have already installed libdvdcss2,libdvdread3 & libdvdnav4)
4) Getting videos to play in browsers - including flash and such.


Seems like in ubuntu you just search for the gstreamer and you were good to go. Is there a meta package like that in Debian as well.

1. apt-get install alsa-base alsa-utils alsa-oss
as root: alsaconf
reboot
alsamixer

2. i use vlc for everything
3. vlc
4. vlc + mediaplayerconnectivity:   [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
i use flash player for flash, but there is a setting for flash.

---

### Post by Arthur Archnix on 2008-06-10
I don't recall installing anything in particular to add mp3 support in Lenny. AFAIRemember it worked upon install.

You really need to learn to use aptitude. It has a search function and descriptions of all packages. It's faster than waiting for someone else to tell you what you could look-up on your own.

There's also [http://www.debian.org/distrib/packages#search_contents](http://www.debian.org/distrib/packages#search_contents)

---

### Post by Inxsible on 2008-06-10
> **kerry_s said:**
> 1. apt-get install alsa-base alsa-utils alsa-oss
as root: alsaconf
reboot
alsamixer

2. i use vlc for everything
3. vlc
4. vlc + mediaplayerconnectivity:   [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
i use flash player for flash, but there is a setting for flash.I had already done that part kerry. I did it over again. This is what i get when I run alsaconf```
debian:/home/murtuza# alsaconf
Unloading ALSA sound driver modules: snd-maestro3 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-alloc.
Building card database...


Loading driver...
Setting default volumes...
amixer: Mixer attach default error: No such file or directory
Saving the mixer setup used for this in /var/lib/alsa/asound.state.
/usr/sbin/alsactl: save_state:1497: No soundcards found...


===============================================================================

 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!

```Note that it finds my sound card which I select...but here at the end it says "No soundcards found...

So I am not sure what actually went on.

---

### Post by Inxsible on 2008-06-10
> **Arthur Archnix said:**
> I don't recall installing anything in particular to add mp3 support in Lenny. AFAIRemember it worked upon install.

You really need to learn to use aptitude. It has a search function and descriptions of all packages. It's faster than waiting for someone else to tell you what you could look-up on your own.

There's also [http://www.debian.org/distrib/packages#search_contents](http://www.debian.org/distrib/packages#search_contents)Hi Arthur..I do use aptitude and did search thru it. I am new to Debian but not to Linux. I have already installed the required codecs that CJ56 mentioned a couple of posts back. I asked here on the forum only because nothing seems to work for me. So I wanted to kow if I missed a package or something.

---

