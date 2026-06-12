---
title: "What is there in Edubuntu?"
date: 2006-11-15
forum: Education &amp; Science
---

### Post by Gargamella on 2006-11-15
Hi I would like to know,since i am a Ubuntu user, which software Edubuntu has more than Ubuntu, it interests me as distro,but i would like to know what's in it...On Edubuntu site there are some screenshots,but it doesn't let you know the included software


thanks

---

### Post by skymt on 2006-11-15
```
$ apt-cache depends ubuntu-desktop > ubuntu-desktop
$ apt-cache depends edubuntu-desktop > edubuntu-desktop
$ diff ubuntu-desktop edubuntu-desktop | grep '^>'
> edubuntu-desktop
>   Depends: atomix
>   Depends: denemo
>   Depends: dia-gnome
>   Depends: edubuntu-artwork
>   Depends: edubuntu-artwork-usplash
>   Depends: gcompris
>   Depends: gcompris-sound-da
>   Depends: gcompris-sound-de
>   Depends: gcompris-sound-en
>   Depends: gcompris-sound-es
>   Depends: gcompris-sound-fr
>   Depends: gcompris-sound-it
>   Depends: gcompris-sound-pt
>   Depends: gcompris-sound-ru
>   Depends: gcompris-sound-sv
>   Depends: gnome-icon-theme-gartoon
>   Depends: gpaint
>   Depends: kalzium
>   Depends: kanagram
>   Depends: kbruch
>   Depends: keduca
>   Depends: khangman
>   Depends: khelpcenter
>   Depends: kig
>   Depends: kino
>   Depends: kmplot
>   Depends: kpercentage
>   Depends: kstars
>   Depends: ktouch
>   Depends: ktuberling
>   Depends: kturtle
>   Depends: kverbos
>   Depends: kvoctrain
>   Depends: kwordquiz
>   Depends: pessulus
>   Depends: scribus
>   Depends: student-control-panel
>   Depends: tuxmath
>   Depends: tuxpaint
>   Depends: tuxpaint-data
>   Depends: tuxpaint-stamps-default
>   Depends: xaos
$ diff ubuntu-desktop edubuntu-desktop | grep '^<'
< ubuntu-desktop
<   Depends: diveintopython
<   Depends: f-spot
<   Depends: rss-glx
<   Depends: screensaver-default-images
<   Depends: tangerine-icon-theme
<   Depends: tango-icon-theme
<   Depends: tango-icon-theme-common
<   Depends: tomboy
<   Depends: ubuntu-artwork
<   Depends: usplash-theme-ubuntu
<   Depends: xscreensaver-data
<   Depends: xscreensaver-gl
<   Recommends: example-content
<   Recommends: gcc
<   Recommends: linux-headers-generic
<   Recommends: make
<   Recommends: ttf-arphic-ukai
<   Recommends: ttf-arphic-uming
<   Recommends: ttf-baekmuk

```

---

### Post by Gargamella on 2006-11-15
thank you

---

### Post by LaserJock on 2006-11-15
This is likely to change quite a bit too in [Feisty]("https://wiki.ubuntu.com/EdubuntuOnTwoCDs"). More educational apps for high school and university students and addition of some of the apps (like mono apps) that were taken off to make room on the Edubuntu CD.

---

### Post by kditty on 2006-11-18
is it possible to add edubuntu apps to be dapper drake install? i have a three year old who likes to draw and play around, and id like her to have some stuff to mess with and get her used to using computers(linux). 

not much on dapper drake for her to play with.

---

### Post by akniss on 2006-11-18
> **kditty said:**
> is it possible to add edubuntu apps to be dapper drake install? i have a three year old who likes to draw and play around, and id like her to have some stuff to mess with and get her used to using computers(linux). 

not much on dapper drake for her to play with.

Just type this at a terminal, and you will be able to play with all the edubuntu apps.  It has some pretty cool artwork as well.  We did the same thing on my wife's laptop (she's a fourth grade teacher).
```
sudo aptitude install edubuntu-desktop
```

---

