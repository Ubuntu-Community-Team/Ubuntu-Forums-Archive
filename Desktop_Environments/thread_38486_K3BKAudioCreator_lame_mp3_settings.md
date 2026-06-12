---
title: "K3B/KAudioCreator lame mp3 settings"
date: 2005-05-31
forum: Desktop Environments
---

### Post by buldir on 2005-05-31
Can someone please post their K3B mp3/lame encoding settings (i.e. the command line code)? I mucked mine up and cannot rip to mp3 anymore. Has anyone had any success ripping to mp3 using KAudioCreator? If so, could you post your mp3/lame encoding settings (i.e. the command line code)? Thanks in advance.

---

### Post by ludi on 2005-05-31
[QUOTE=buldir]Can someone please post their K3B mp3/lame encoding settings (i.e. the command line code)? I mucked mine up and cannot rip to mp3 anymore. Has anyone had any success ripping to mp3 using KAudioCreator? If so, could you post your mp3/lame encoding settings (i.e. the command line code)? Thanks in advance.[/QUOTE]
 open konqueror and type: settings:/Sound/ open audio CDs and select MP3 Enconder. Choose your quality.
Kde 3.4 don't need Kaudiocreator anymore, just open Konqueror and go to media:/, open the CD and simple drag the folder MP3 or OGG (whatever) to your music folder.

---

### Post by ceti on 2005-05-31
[QUOTE=buldir]Can someone please post their K3B mp3/lame encoding settings (i.e. the command line code)? I mucked mine up and cannot rip to mp3 anymore. Has anyone had any success ripping to mp3 using KAudioCreator? If so, could you post your mp3/lame encoding settings (i.e. the command line code)? Thanks in advance.[/QUOTE]

My KAudioCreator:
lame --preset cbr 160 --tt %{title} --ta %{artist} --tl %{albumtitle} --ty %{year} --tn %{number} --tg %{genre} %f %o

Hope this helps.

---

### Post by buldir on 2005-06-01
ludi,
Thanks...using Konqueror like that is pretty slick.  Unfortunately, the mp3 tab does not show up when I try to change the settings.  I have lame installed in /usr/bin/lame.  I'm not sure why it's not showing up.  It's not the official Ubuntu version...maybe that's why.  I guess I could drag the waves somewhere and  encode them as mp3 in a command line script.

ceti,
Thanks...I got it working now.  Here's what I use for KAudioCreator:

lame -q 2 -b 128 --cbr --tt %title --ta %albumartist --tl %albumtitle --ty %year --tn %number %f %o

Thanks to you both for your help.

---

### Post by buldir on 2005-06-01
[QUOTE=ludi]open konqueror and type: settings:/Sound/ open audio CDs and select MP3 Enconder. Choose your quality.
Kde 3.4 don't need Kaudiocreator anymore, just open Konqueror and go to media:/, open the CD and simple drag the folder MP3 or OGG (whatever) to your music folder.[/QUOTE]


ludi,
I got the mp3 settings tab to appear.  The lame I installed into /usr/bin was a package I converted from a Fedora Core RPM to .deb using alien.  I uninstalled it, opened up Synaptic, and installed lame, lame-extras, and liblame0.  Konqueror impressed me tonight.  Thanks again.

---

### Post by Lord Illidan on 2005-07-03
[QUOTE=buldir]ludi,
I got the mp3 settings tab to appear.  The lame I installed into /usr/bin was a package I converted from a Fedora Core RPM to .deb using alien.  I uninstalled it, opened up Synaptic, and installed lame, lame-extras, and liblame0.  Konqueror impressed me tonight.  Thanks again.[/QUOTE]

This also worked for me.. Thanks, buldir and ludi too!

---

### Post by oliwally on 2005-07-16
> I got the mp3 settings tab to appear. The lame I installed into /usr/bin was a package I converted from a Fedora Core RPM to .deb using alien. I uninstalled it, opened up Synaptic, and installed lame, lame-extras, and liblame0. Konqueror impressed me tonight.

Worked for me also. That's just magic ! Very impressive.

---

### Post by z_pod on 2005-07-16
[QUOTE=buldir]ludi,
I got the mp3 settings tab to appear.  The lame I installed into /usr/bin was a package I converted from a Fedora Core RPM to .deb using alien.  I uninstalled it, opened up Synaptic, and installed lame, lame-extras, and liblame0.  Konqueror impressed me tonight.  Thanks again.[/QUOTE]

Hi,
can you please tell me which repositories I have to configure to install lame ?
I'm asking since I can't find it anywhere.
My repos  (I'm running kubuntu hoary) :

## Uncomment the following two lines to fetch updated software from the network
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# kde 3.4.1
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Thanks !

---

### Post by z_pod on 2005-07-16
[QUOTE=z_pod]Hi,
can you please tell me which repositories I have to configure to install lame ?
I'm asking since I can't find it anywhere.
My repos  (I'm running kubuntu hoary) :

## Uncomment the following two lines to fetch updated software from the network
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# kde 3.4.1
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Thanks ![/QUOTE]


OK Nevermind.
I've found it @ marillat repos.

Thanks anyway

---

### Post by Terracotta on 2005-07-16
Is there also a way to make konqueror rip the music to a certain folder: for example: /home/usr/music/artist/album/song.ogg ?? like in Kaudiocreator? To me that is the only advantage kaudiocreator still has above the konqueror way, because it's just simply enlighten the songs you want and then click rip. easy and faster than drag and drop to me.

---

### Post by fig_jam_uk on 2005-08-21
[QUOTE=buldir]ludi,
Thanks...using Konqueror like that is pretty slick.  Unfortunately, the mp3 tab does not show up when I try to change the settings.  I have lame installed in /usr/bin/lame.  I'm not sure why it's not showing up.  It's not the official Ubuntu version...maybe that's why.  I guess I could drag the waves somewhere and  encode them as mp3 in a command line script.

ceti,
Thanks...I got it working now.  Here's what I use for KAudioCreator:

lame -q 2 -b 128 --cbr --tt %title --ta %albumartist --tl %albumtitle --ty %year --tn %number %f %o

Thanks to you both for your help.[/QUOTE]

Thank you very much Buldir helped me out a lot  :razz:

---

