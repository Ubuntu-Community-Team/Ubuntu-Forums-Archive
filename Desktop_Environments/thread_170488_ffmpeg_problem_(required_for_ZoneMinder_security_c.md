---
title: "ffmpeg problem (required for ZoneMinder security camera app.)"
date: 2006-05-04
forum: Desktop Environments
---

### Post by transistor on 2006-05-04
I've reduced the ZoneMinder install problem started on thread [http://ubuntuforums.org/showthread.php?t=133506&page=2](http://ubuntuforums.org/showthread.php?t=133506&page=2) to a problem between Ubuntu and ffmpeg. The configure step results in the following output: 
```
# checkinstall -D make install

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
Making install in src
make[1]: Entering directory `/home/don/Desktop/ZoneMinder-1.22.1/src'
g++  -g -O2  -L/usr/lib -L/usr/lib/mysql   -o zmc  zmc.o zm.o zm_db.o zm_config.o zm_coord.o zm_box.o zm_poly.o zm_image.o zm_event.o zm_zone.o zm_camera.o zm_local_camera.o zm_remote_camera.o zm_file_camera.o zm_monitor.o zm_user.o zm_mpeg.o zm_jpeg.o zm_regexp.o zm_signal.o zm_buffer.o zm_debug.o  -lavformat -lavcodec -lavutil -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg
/usr/lib/libavformat.a(dc1394.o): In function `dc1394_read_header':
: undefined reference to `dc1394_create_handle'
/usr/lib/libavformat.a(dc1394.o): In function `dc1394_read_header':
: undefined reference to `dc1394_get_camera_nodes'
.
.                [many more undefined references]
.
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_decode_frame':
: undefined reference to `gsm_decode'
collect2: ld returned 1 exit status
make[1]: *** [zmc] Error 1
make[1]: Leaving directory `/home/don/Desktop/ZoneMinder-1.22.1/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.
```


Phil (Mr. ZoneMinder) suggests ([http://www.zoneminder.com/forums/viewtopic.php?p=19688#19688](http://www.zoneminder.com/forums/viewtopic.php?p=19688#19688))
> This is an ffmpeg problem. As I don't know whether you had to manually run configure or not I can't say whether it is because ffmpeg is missing or maybe just that you have a problem with the version. You will usually need to make sure you have ffmpeg cvs if installing from source or ffmpeg-devel if installing from a package.
I had installed ffmpeg with Synaptic. (Phil hasn't used Ubuntu.)

mks113 (a user on this forum) reports:
> ffmpeg is installed, apt-get isn't showing a package for ffmpeg-devel as suggested in the above [on the other thread] reply. 

Has anyone got a workaround for this?

Thanks.

---

### Post by louis_nichols on 2006-05-04
Indeed there isn't a ffmpeg-dev package, but these might help:

```
development files for libavcodec
This is the codec library from the ffmpeg project. It supports most existing
encoding formats (MPEG, DivX, MPEG4, AC3, DV, ...).
```
```
development files for libavformat
This is the codec library from the ffmpeg project. It supports most existing
file formats (AVI, MPEG, OGG, Matroska, ASF, ...).
```

And there are others. I just did a search in synaptic with keyword ffmpeg, look in: description and name

---

### Post by transistor on 2006-05-06
Thanks Louis. I have libavcoded-dev and libavformat-dev. (I don't think there are non-dev pagages.) Still no success. I want to check that I understand the error messages.

```
/usr/lib/libavformat.a(dc1394.o): In function `dc1394_read_header':
: undefined reference to `dc1394_create_handle'

```
I understand this to mean that libavformat.a references the dc1394_create_handle function but the make can't find it.

Q1. Where does it look? e.g. Is it possible that I have the files but that an environment variable isn't set?
Q2. What format is a ".a" file? I can't open it with gedit.

All suggestions welcome.

---

### Post by louis_nichols on 2006-05-06
I think .a files are binaries. Simliar to .o and .so

As for the rest, sorry, but I'm not experienced enough to answer. Perhaps, try getting the ffmpeg tarball and use that to compile. Maybe visit their homepage, they might have support forums, maybe a mailing list and/or a developer mailing list. E-mail the developers, if needed!

---

### Post by mks113 on 2006-05-08
libavcodec is installed in /usr/lib/libavcodec.a so I'm suspecting that there is another issue here.

I'm not a C programmer (perl is the extent of my coding) so these errors are beyond me.

I tried installing the ffmpeg CVS package as it was supposed to have the libavcodec dev package in it, but I'm still getting the exact same errors.  I think I am stuck.

Michael

---

### Post by Carlos_E on 2006-05-16
Finally, I have zoneminder running!

I was stuck at the same point where you are now. What I did was:

1. Compile ffmpeg from cvs:
```

mkdir src
cd src
cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg
cd src/ffmpeg/
make clean
./configure  --enable-vorbis --enable-libogg --enable-theora --enable-dc1394
make
sudo make install
sudo make install-headers 
sudo make install-libs
sudo make install-progs
sudo make install-man

```

2. Compile zoneminder telling it where are the ffmpeg libraries
```
cd ..
tar xfvz ZoneMinder-1.22.1.tar.gz 
cd ZoneMinder-1.22.1
./configure --with-webdir=/var/www/zm --with-cgidir=/usr/lib/cgi-bin --with-webuser=www-data --with-webgroup=www-data [B]--with-extralibs="/usr/lib/libtheora.so /usr/lib/libvorbis.so /usr/lib/libvorbisenc.so /usr/lib/libogg.so /usr/lib/libdc1394_control.so"
[/B]make
sudo make install

```

And that's it :D

---

### Post by transistor on 2006-05-21
Thanks Carlos. To get that to work I had to 
- Install [EasyUbuntu ]("http://easyubuntu.freecontrib.org/") and on the System tab check Repository list to enable the Main, Universe, Multiverse and PLF sources.
- Install auto-apt (to automatically call whatever is required ffmpeg) from the new repositories. You can use Synaptic for this.
- Install libvorbis-dev, libtheora-dev & libdc1394-dv.

I now have ZoneMinder installed and running but haven't got the IEEE1394 cameras working yet. If anyone else is having this problem you can use gscanbus to give you a graphical layout of the IEEE1394 bus and devices. You can use Coriander to do some further testing. I still can't see the video but I must be really close!

I've started a new thread for this particular aspect at [How can I troubleshoot IEEE1394 / Firewire board and cameras?]("http://www.ubuntuforums.org/showthread.php?t=179654")

---

### Post by adamkane on 2006-05-21
Installing ffmpeg from source is a PITA, and isn't necessary anymore. Use the Takis repository.

[http://issaris.be/breezy/]("http://issaris.be/breezy/")

EDIT:
Due to unstability of the server that previously hosted the repository, Takis has moved the Ubuntu Breezy repository. The new line to add to your /etc/apt/sources.list would be:
 deb [http://alpha.uhasselt.be/takis.issaris/breezy/]("http://alpha.uhasselt.be/takis.issaris/breezy/") ./

---

### Post by BrownieMan on 2006-05-29
[QUOTE=adamkane]Installing ffmpeg from source is a PITA, and isn't necessary anymore. Use the Takis repository.

[http://issaris.be/breezy/]("http://issaris.be/breezy/")

EDIT:
Due to unstability of the server that previously hosted the repository, Takis has moved the Ubuntu Breezy repository. The new line to add to your /etc/apt/sources.list would be:
 deb [http://alpha.uhasselt.be/takis.issaris/breezy/]("http://alpha.uhasselt.be/takis.issaris/breezy/") ./[/QUOTE]

the edited repository doesnt work anymore, it was moved to "http://issaris.be/breezy/" so if/when you add teh repository  when it asks you for input give the line "deb [http://issaris.be/breezy](http://issaris.be/breezy) ./". I think you might have to remove the original ffmpeg first to install teh one formt eh new repository, but I'm not sure.

---

### Post by octavious on 2006-05-30
congrats Carlos - I am new to linux and ubuntu, it seems so easy to use and install - unfortuantely I have had little success with the livecds and the fedora livecd due to my zoneminder machine not liking the built in ethernet (another story) ... anyway, do you happen to knopw if there is a an idiots guide to installing on ubuntu which can take me step by step?
thanks for any guidance
oactavious

 
[QUOTE=Carlos_E]Finally, I have zoneminder running!

I was stuck at the same point where you are now. What I did was:

1. Compile ffmpeg from cvs:
```

mkdir src
cd src
cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg
cd src/ffmpeg/
make clean
./configure  --enable-vorbis --enable-libogg --enable-theora --enable-dc1394
make
sudo make install
sudo make install-headers 
sudo make install-libs
sudo make install-progs
sudo make install-man

```

2. Compile zoneminder telling it where are the ffmpeg libraries
```
cd ..
tar xfvz ZoneMinder-1.22.1.tar.gz 
cd ZoneMinder-1.22.1
./configure --with-webdir=/var/www/zm --with-cgidir=/usr/lib/cgi-bin --with-webuser=www-data --with-webgroup=www-data [B]--with-extralibs="/usr/lib/libtheora.so /usr/lib/libvorbis.so /usr/lib/libvorbisenc.so /usr/lib/libogg.so /usr/lib/libdc1394_control.so"
[/B]make
sudo make install

```

And that's it :D[/QUOTE]

---

### Post by BrownieMan on 2006-06-03
Here is what I've done basicaly

- Install EasyUbuntu  and on the System tab check Repository list to enable the Main, Universe, Multiverse and PLF sources.
- Install auto-apt (to automatically call whatever is required ffmpeg) from the new repositories. You can use Synaptic for this.
- Install libvorbis-dev, libtheora-dev & libdc1394-dev (libdc1394-13 & libdc1394-dev)


install in synaptic:

apache2
build-essential
libdate-manip-perl
libdbi-perl
libdbd-mysql-perl
libjpeg62-dev
libmysqlclient14-dev (or latest version)
libssl-dev
php5
php5-mysql
libpcre3
libpcre3-dev
libavcodec-dev
libavformat-dev
libwww-perl
auto-apt
libgsmme-dev
svn-buildpackage



```
mkdir src
cd src
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd src/ffmpeg/
make clean
./configure  --enable-vorbis --enable-libogg --enable-theora --enable-dc1394 --enable-gpl --enable-dts --enable-libgsm
make
sudo make install
sudo make install-headers 
sudo make install-libs
sudo make install-progs
sudo make install-man
```



```
cd ..
tar xfvz ZoneMinder-1.22.1.tar.gz 
cd ZoneMinder-1.22.1
./configure --with-webdir=/var/www/zm --with-cgidir=/usr/lib/cgi-bin --with-webuser=www-data --with-webgroup=www-data --with-extralibs="/usr/lib/libtheora.so /usr/lib/libvorbis.so /usr/lib/libvorbisenc.so /usr/lib/libogg.so /usr/lib/libdc1394_control.so /usr/lib/libgsm.a /usr/lib/libdts.a"
make
sudo make install
```



I thought all of that was going to work, it didn't. Everything seems to go fine until I 'make' zoneminder. Here is the final output:

```
philip@server:~/ZoneMinder-1.22.2$ make
make  all-recursive
make[1]: Entering directory `/home/philip/ZoneMinder-1.22.2'
Making all in src
make[2]: Entering directory `/home/philip/ZoneMinder-1.22.2/src'
g++  -g -O2  -L/usr/lib -L/usr/lib/mysql  /usr/lib/libtheora.so /usr/lib/libvorbis.so /usr/lib/libvorbisenc.so /usr/lib/libogg.so /usr/lib/libdc1394_control.so /usr/lib/libgsm.a /usr/lib/libdts.a -o zmc  zmc.o zm.o zm_db.o zm_config.o zm_coord.o zm_box.o zm_poly.o zm_image.o zm_event.o zm_zone.o zm_camera.o zm_local_camera.o zm_remote_camera.o zm_file_camera.o zm_monitor.o zm_user.o zm_mpeg.o zm_jpeg.o zm_regexp.o zm_signal.o zm_buffer.o zm_debug.o  -lavformat -lavcodec -lavutil -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_init': undefined reference to `dts_init'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_frame'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_blocks_num'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_block'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_samples'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_blocks_num'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_syncinfo'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_init': undefined reference to `gsm_create'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_close': undefined reference to `gsm_destroy'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_encode_frame': undefined reference to `gsm_encode'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_decode_frame': undefined reference to `gsm_decode'
collect2: ld returned 1 exit status
make[2]: *** [zmc] Error 1
make[2]: Leaving directory `/home/philip/ZoneMinder-1.22.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/philip/ZoneMinder-1.22.2'
make: *** [all] Error 2

```

I know for sure that I instaled 'libavcodec-dev' thorugh synaptic, which is what I've seen other people with similar problems on forums be told they need to do. I've installed and reinstalled ffmpeg and other things in synaptic quite a few times. My only idea now is to do a fresh install and do everything I did again but much cleaner, though I'm not sure if that will help or not or should make a difference. Any help or advice would be appreciated. Once I get this thing working I'm going to try and build a package for this if possible. Thanks in advance guys and gals.

---

### Post by mks113 on 2006-06-09
I'm afraid I'm still stuck.  I thought my problem was related to not being able to use cvs through our proxy server.  I downloaded the latest cvs of mplayer and compiled it, but I'm still getting the same errors as BrowieMan.

I should have the new version of Ubuntu in a few days.  We'll see if that fixes anything.

---

### Post by BrownieMan on 2006-06-09
okay looks like i've made some progress. The following code configures zoneminder which is where i think the problem lies. 

[CODE]./configure --with-webdir=/var/www/zm --with-cgidir=/usr/lib/cgi-bin --with-webuser=www-data --with-webgroup=www-data --with-extralibs="/usr/lib/libtheora.so /usr/lib/libvorbis.so /usr/lib/libvorbisenc.so /usr/lib/libogg.so /usr/lib/libdc1394_control.so /usr/lib/libgsm.a /usr/lib/libdts.a"[/CODE

The last parmaters /usr/lib/... etc tell zoneminder where certain libraries are that do certain functions. The reason the errors come about is because it cant find the functions zoneminder is calling that are listed in the errors. The last two parameters don't list any valid libraries so they can be removed. The ones that are needed have similar names though: libgsm.so and libdts.so (notice the different file extensions). libgsm should be in /usr/lib but libdts.so isn't so it's nto worth putting in as a parameter. But put in the /usr/liblibgsm.so , this will leave errors relating to dts. I found a a thread that talks about the same problem sorta. 
http://www.blender.org/forum/viewtopic.php?t=8108&postdays=0&postorder=asc&start=0&sid=73a4f7cbc72eaa9357e22d5ee20acc0e
The file that we need that is most like libdts.so is in the gstreamer package /usr/lib/gstreamer-0.8/libgstdtsdec.so, unfortunately when I try to use it I get a error that it wont even try to configure the file. One of the people in the threat said that they linked to it from inside /usr/lib. I'm guessing that means a file should be made libdts.so (anyfile name should do but it prolly makes mroe sense to do that i think) and then link that file to /usr/lib/gstreamer-0.8/libgstdtsdec.so. After that I think it should work, unfortunatly I don't know how to link the files. Any ideas?

---

### Post by sergiusz.pawlowicz on 2006-08-26
Hello, I have finally resolved your question.

I use: 

```

./configure --prefix=/opt/zm-1.22.2 --with-webdir=/var/www/cam --with-cgidir=/var/www/cgi-bin --with-webuser=www-data --with-webgroup=www-data --with-ffmpeg --with-extralibs="-ldc1394_control -logg -ldts_pic -ldts -lvorbis -lvorbisenc -ltheora -lgsm -lavcodec_pic -lavcodec -lpostproc /usr/lib/gstreamer-0.8/libgstdtsdec.so /usr/lib/gstreamer-0.8/libgstaudio.so"

```

libgstdtsdec.so is from gstreamer0.8-misc ubuntu package

And do not forget to add /usr/lib/gstreamer-0.8/ into /etc/ld.so.conf and reload it.

Zoneminder works as a charm :)

---

