---
title: "I installed every single gstreamer plugin and still no DVD playback"
date: 2006-06-21
forum: Desktop Environments
---

### Post by braveerudite on 2006-06-21
I installed every single gstreamer in synaptic and I still get no play back for DVD.

I get the following message from Xine-UI: "ERROR Reading NAV packet"

I have also try the following media players with no success :(

Movie Player
Gxine movie player

I installed Totem but is not showing up on my menus. Please help. ](*,)

I also followed these instruction and still didn't work.

Windows Codecs (w32codecs)

    *

      i386 architecture
          o

            Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions. You can download the package from an unoffical repository and install it with dpkg:
          o

            wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
            sudo dpkg -i w32codecs_20060611-0.0_i386.deb

                +

](*,) ](*,) ](*,)

---

### Post by DarthMandeep on 2006-06-21
What about libdvdcss? Have you installed that?

---

### Post by MetalMusicAddict on 2006-06-21
Xine doesnt use gstreamer AFAIK. Totem by default will unless you installed totem-xine then you will need the w32codecs and libdvdcss installed.

---

### Post by braveerudite on 2006-06-21
[QUOTE=MetalMusicAddict]Xine doesnt use gstreamer AFAIK. Totem by default will unless you installed totem-xine then you will need the w32codecs and libdvdcss installed.[/QUOTE]

This is what I'm getting 

jok3r@NAOMI-LINUX:~$ sudo apt-get install libdvdcss Password:
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
jok3r@NAOMI-LINUX:~$


and my source list looks like this.  Any other repo worth adding?


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by lindyslack on 2006-06-21
I think the easiest way to get dvd playback is to install Automatix...

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

Make sure to add the right line to your sources.list and then just:

sudo apt-get install automatix.

Now remember, based on where you live will dictate wheather or not you can legally install libdvdcss2 and some of the the other codecs available to you through automatix...

---

### Post by braveerudite on 2006-06-21
[QUOTE=lindyslack]I think the easiest way to get dvd playback is to install Automatix...

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

Make sure to add the right line to your sources.list and then just:

sudo apt-get install automatix.

Now remember, based on where you live will dictate wheather or not you can legally install libdvdcss2 and some of the the other codecs available to you through automatix...[/QUOTE]

None of the repos in my source list has it.  Which repository can I get this from?

---

### Post by lindyslack on 2006-06-21
From the getautomatix web site

If you use Dapper, add this: 

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

---

### Post by braveerudite on 2006-06-21
[QUOTE=lindyslack]From the getautomatix web site

If you use Dapper, add this: 

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main[/QUOTE]


Dude, I Love you!!! I was looking for something like this.  I hope the guys at automatix never give up on this project.  OMG I Love Automatix Woot!!!=D> \\:D/

---

### Post by nix4me on 2006-06-21
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

All you had to do was add multiverse to your sources.  You only had universe.  Like this:

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse

nix4me

---

### Post by lindyslack on 2006-06-21
Automatix has been around for some time and has expanded to include MEPIS Linux as well as Ubuntu... I hope they keep going for a long time as well!!! It's always the first thing I installl after loading Ubuntu on anything!!!

---

### Post by braveerudite on 2006-06-21
[QUOTE=nix4me]deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

All you had to do was add multiverse to your sources.  You only had universe.  Like this:

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse

nix4me[/QUOTE]

Thx for taking the time to check out my source.list I will be adding those two lines right now. Thx so much.  I love Ubuntu community you guys are the best!!! ;-)

---

### Post by MetalMusicAddict on 2006-06-21
[QUOTE=braveerudite]I love Ubuntu community you guys are the best!!! ;-)[/QUOTE]
IMHO its half of the reason Ubuntu is great (other half being the distro itself). I like other distros as well but this community makes all the difference.

---

### Post by nix4me on 2006-06-21
[QUOTE=braveerudite]Thx for taking the time to check out my source.list I will be adding those two lines right now. Thx so much.  I love Ubuntu community you guys are the best!!! ;-)[/QUOTE]


No problem, glad i could help.

nix4me

---

### Post by temcat on 2006-06-22
Another way of installing libdvdcss is the following

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by FreDeas on 2006-06-24
I've also tried everything, including what you 've posted here, and I still can;t play any dvd!! The problem is **libdvdcss**. Automatix can't find it, it posts an error. I visited *[http://developers.videolan.org/libdvdcss/](http://developers.videolan.org/libdvdcss/)*, but I can't understand what I have to do. Ok I choose releases and I download all the files of the latest version, then?? Where do I put these files??
  I also tried the last command (that of temcat) and it posts this :
""No binary deb available.  Will try to build and install it.
You need to have debhelper, dpkg-dev and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed""

I'm afraid of clicking enter... I don;t understand nothing of these..


Please help..

---

### Post by temcat on 2006-06-25
> **FreDeas]I've also tried everything, including what you 've posted here, and I still can said:**
> http://developers.videolan.org/libdvdcss/[/url]*, but I can't understand what I have to do. Ok I choose releases and I download all the files of the latest version, then?? Where do I put these files??
  I also tried the last command (that of temcat) and it posts this :
""No binary deb available.  Will try to build and install it.
You need to have debhelper, dpkg-dev and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed""

I'm afraid of clicking enter... I don;t understand nothing of these..


Please help..

It says that it can't find libdvdcss packaged for Ubuntu, but can build it from source code and install it on your system. For this, you have to have the following packages installed: debhelper, dpkg-dev and fakeroot.

Install these packages via Synaptic or via command line with the following command:

```
sudo apt-get instal debhelper dpkg-dev fakeroot
```

After that, re-run this script and press Return when it asks you that question.

---

