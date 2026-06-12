---
title: "HOW TO: play 3gp movies with sound on ubuntu ..."
date: 2006-05-17
forum: Desktop Environments
---

### Post by CookieNinja on 2006-05-17
This is not the definitive how to, but a reasonable bodge that should work quite easily. This particular version of ffmpeg, ffplay & ffserver will be installed in /usr/local/bin, and will not overwrite theversion of ffmpeg. ffplay & ffserver installed via synaptic or apt-get.

*in case this matters, before the following steps were done I could play 3gp files in mplayer but there was no sound.* I didn't install any additional files or packages to make this work, but it might be that I have stuff installed to do another job that not everyone has, which just so happen to required for this to work.*

First of all open a shell.

Next use this command to get the source for ffmpeg:

cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg

This puts the sources inside ~/ffmpeg.

Next get the codec you need for the audio by typing this into the shell

wget [http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip](http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip)

The file, "26.104/26104-510.zip", needs to be unzipped anywhere you like. A folder inside ~/ffmpeg/libavcodec called "amr_float" needs to be created. Next the file within it called "26104-510_ANSI_C_source_code.zip" needs to be unzipped, and the contents placed in "~/ffmpeg/libavcodec/amr_float/".

Now that all this has been done, you need to do the following in the shell.

cd ~/ffmpeg

./configure  --enable-amr_nb

make

make install

Now you should be able to play 3gp movies by typing the following:

/usr/local/bin/ffplay <full-path-to-3gp-file>

This particular version of ffmpeg, ffplay & ffserver will be installed in /usr/local/bin, and will not overwrite theversion of ffmpeg. ffplay & ffserver installed via synaptic or apt-get.

Now all that's needed is some clever clogs to tell us how to compile ffmpeg exactly the same way it's compiled in ubuntu so that it can replace the ffmpeg that's usually installed via synaptic & apt-get.

A 2nd best option would be to have a how-to on using ffmpeg to convert the 3gp files to a more standard format that plays in all or most media players.

---

### Post by CookieNinja on 2006-05-17
The 3gp files now seem to play, with sound, with mplayer too! There's no need to specifically use /usr/local/bin/ffplay.

*warning* this means that I am now not confident of files being affected that might lead to an inability to play formats other than 3gp!

On a postive note, I suspect that even if it does cause the above problem, it should be possible to re-install the version of ffmpeg that you can install via synaptic or apt-get and restore things to how they were before my bodge/how-to was followed.

---

### Post by Ptero-4 on 2006-05-17
you can use the prefix=/usr in the ./configure script and then use checkinstall instead of make install to make a deb package of ffplay, etc that replaces the ones from the repos.

---

### Post by CookieNinja on 2006-05-24
[QUOTE=Ptero-4]you can use the prefix=/usr in the ./configure script 
[/QUOTE]

I knew this bit already :-) I was just happy for it to be in /usr/local/ instead of /usr

[QUOTE=Ptero-4]
use checkinstall instead of make install to make a deb package
[/QUOTE]

THAT information is, for me, one of those really tiny bits of information that makes a HUGE difference. Despite having compiled and run software myself for years when I need to, I've only got as far as reading how to make debs the long, and very boring, mannual way and not been bothered to make the effort.

That's going to make my life SO much easier! Now, what I really need to know, is a quick and easy way to discover what dependancies a program has so that I can make "proper" debs with all the right information in them. Yeah, I know a lot of people list the dependencies with their software, but there's nothing like being sure you've got a complete list so's not to look stupid when someone else can't run the program after installing your .deb.

---

### Post by bluenova on 2006-10-08
Thanks for that.

Small change though. The mplayer team now use svn instead of cvs.

So instead of:
```
cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg
```

Do:
```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

---

### Post by CookieNinja on 2006-10-08
> **bluenova said:**
> Thanks for that.

Small change though. The mplayer team now use svn instead of cvs.



Cheers for updating that, so that other people can do things easily. I've since upgraded my phone and the movie clips on that play with no need for doing that stuff anymore.

---

### Post by studio84 on 2007-06-19
```
ole@hybelgrom86:~/ffmpeg$ ./configure --enable-amr_nb
Unknown option "--enable-amr_nb".
See ./configure --help for available options.
```

how do I solve this? :S have I done something wrong?

---

### Post by Dooglus on 2007-06-22
> **studio84 said:**
> ```
ole@hybelgrom86:~/ffmpeg$ ./configure --enable-amr_nb
Unknown option "--enable-amr_nb".
See ./configure --help for available options.
```

how do I solve this? :S have I done something wrong?

Use
./configure --enable-libamr-nb
instead.

---

### Post by tgu on 2007-07-01
Hi folks!

Here's an update on building the latest ffmpeg with libamrnb support. Note that it is probably easier to choose standard prefixes for ffmpeg and libamrnb, but I prefer to put them in a location where I can easily remove them if I want. Choose whatever prefix you like and update your paths if necessary.

Get the ffmpeg sources

```
svn co svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg-svn
```

Also get the libamrnb wrapper build script from this guy at [http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

```
wget http://ftp.penguin.cz/pub/users/utx/amr/amrnb-6.1.0.4.tar.bz2
```

Extract the libamrnb wrapper and go to the source directory. Configure, build and install it

```
./configure --prefix=/opt/libamrnb
```

```
make && sudo make install
```

Go to the ffmpeg source directory then configure, build and install it

```
./configure --prefix=/opt/ffmpeg-svn --enable-libamr-nb --extra-cflags=-I/opt/libamrnb/include -extra-ldflags=-L/opt/libamrnb/lib
```

```
make && sudo make install
```

Done. Hope this helps.

/ Tobias

---

### Post by ElemonGW on 2007-07-01
Thanks for that tgu. Worked perfectly. Oh, and a correction:
```
./configure --prefix=/opt/ffmpeg-svn --enable-libamr-nb --extra-cflags=-I/opt/libamrnb/include -extra-ldflags=-L/opt/libamrnb/lib
```
should be
```
./configure --prefix=/opt/ffmpeg-svn --enable-libamr-nb --extra-cflags=-I/opt/libamrnb/include --extra-ldflags=-L/opt/libamrnb/lib
```

EDIT: Seams I spoked too fast, as it didn't worked.

---

### Post by tgu on 2007-07-02
> **ElemonGW said:**
> Thanks for that tgu. Worked perfectly. Oh, and a correction:
```
./configure --prefix=/opt/ffmpeg-svn --enable-libamr-nb --extra-cflags=-I/opt/libamrnb/include -extra-ldflags=-L/opt/libamrnb/lib
```
should be
```
./configure --prefix=/opt/ffmpeg-svn --enable-libamr-nb --extra-cflags=-I/opt/libamrnb/include --extra-ldflags=-L/opt/libamrnb/lib
```

EDIT: Seams I spoked too fast, as it didn't worked.

Thanks for the correction. What seems to be the problem? Post some output and perhaps I'd be able to help.

---

### Post by ElemonGW on 2007-07-02
This is the odd thing. Nothing went wrong. No errors. However, the 3gp videos still have no sound.
EDIT: Just noticed that your guide is about ffmpeg with libamrnb, which is..... ? So it is not for sound in 3gp videos?

---

### Post by ElemonGW on 2007-07-02
And another thing. With the guide posted by CookieNinja @ the first step I get this error:
```
cvs [checkout aborted]: connect to mplayerhq.hu(213.144.138.186):2401 failed: Connection refused
```

---

### Post by vikramsharma on 2007-07-02
VLC plays almost all the formats MPlayer does, except for VCD formats.  I always use VLC for playing 3gp format. In case you choose to download MPlayer don't forget to get all the required codecs from [here ]("http://www3.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2") .

---

### Post by ElemonGW on 2007-07-02
OH, and a note. I AM able to play 3gp videos with sound in VLC (managed to do before a while) but no other program can. So I still want a way to fix it for all programs but at least I am now able to play them with sound.
EDIT: vikramsharma. just show your post and, as I said, I did it. I now was wondering if I can fix it for all programs. And a note: VLC CAN PLAY VCDs.

---

### Post by tgu on 2007-07-02
> **ElemonGW said:**
> This is the odd thing. Nothing went wrong. No errors. However, the 3gp videos still have no sound.
EDIT: Just noticed that your guide is about ffmpeg with libamrnb, which is..... ? So it is not for sound in 3gp videos?

Ok, well correct... The reason you still have no sound in your media player is that it's probably not aware of libamrnb. My instructions only explains how to build the ffmpeg converter with amr-nb support. You can use ffmpeg to convert your 3gp videos to another (well supported) format with sound. That's what i did with my 3gp videos.

Try this

Add

```
# libamrnb
/opt/libamrnb/lib
```

to /etc/ld.so.conf.d/libamrnb.conf. Then run

```
sudo ldconfig
```

Convert a video like this

```
/opt/ffmpeg-svn/bin/ffmpeg -i video.3gp -ar 22050 video.mpg
```

I'll see if there's a way to make the gstreamer-ffmpeg plugin use libamrnb.

Regards,
Tobias

---

### Post by Roozbehma on 2007-07-02
The easiest way is to install realplayer.

Cheers,
Roozbeh Maadani

---

### Post by ElemonGW on 2007-07-02
W8 w8 I think we have a misunderstanding over here. The videos DO have sound. However all of my programs weren't able to play it (except vlc which as I said before managed to play it). So I was wondering if I could make all the programs play them with sound. It is minor bu ok, just wondering...

---

### Post by tgu on 2007-07-02
> **ElemonGW said:**
> W8 w8 I think we have a misunderstanding over here. The videos DO have sound. However all of my programs weren't able to play it (except vlc which as I said before managed to play it). So I was wondering if I could make all the programs play them with sound. It is minor bu ok, just wondering...

If you don't mind borking your system a bit, you could try changing prefix to /usr for both libamrnb and ffmpeg. :D Also enable at least shared libraries for ffmpeg (--enable-shared). I wouldn't recommend this method though. Someone else could probably tell you how to make deb packages to make a clean installation that would be protected against future updates of ffmpeg. I would be interested to learn this myself.

---

### Post by Spam Banjo on 2007-07-18
Of cause the easiest way of playing 3GP with sound is to install [Real Player for Linux]("http://www.real.com/linux").
:popcorn:

---

### Post by cikson on 2007-08-22
I typed:
```
 ./configure --enable-libamr-nb
```

and output is:

```
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

```

How to solve this problem?

thx

---

### Post by tonyhawz on 2007-11-25
try ```
sudo apt-get install build-essential
``` and then ./configure again

---

### Post by tonyhawz on 2007-11-25
If you enable medibuntu repos and install ffmpeg , ffplay will play 3gp files with sound .
so no need to compile ffmpeg

---

### Post by cikson on 2008-04-30
I have sources.list:
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://hr.archive.ubuntu.com/ubuntu/ gutsy universe main restricted
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://hr.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://hr.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://hr.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

```

insalled ffmpeg, modem connection and when I type:
```
./configure --enable-libamr-nb
```
now output is
```
ERROR: libamrnb not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-user@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

```

Please help me I can't play sounds with video files from my mobile phone.

---

### Post by multisimple on 2008-06-24
taken from [http://ftp.penguin.cz/pub/users/utx/amr/amrnb-7.0.0.2.tar.bz2](http://ftp.penguin.cz/pub/users/utx/amr/amrnb-7.0.0.2.tar.bz2)

1. Install required components

Code:

```
sudo apt-get install g++ subversion nasm zlib1g-dev libx264-dev
```
also try 
```
sudo apt-get install build-essential
```

2. Install AMR

The latest versions of AMR can be found here: [http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr) 
or just use the ones on this thread

AMR-NB
Code:
```

wget http://ftp.penguin.cz/pub/users/utx/amr/amrnb-7.0.0.2.tar.bz2
tar -jxvf amrnb-7.0.0.2.tar.bz2
cd amrnb-7.0.0.2

./configure --prefix=/usr
make
sudo make install
```


AMR-WB
Code:

```
wget http://ftp.penguin.cz/pub/users/utx/amr/amrwb-7.0.0.3.tar.bz2
tar -jxvf amrwb-7.0.0.3.tar.bz2
cd amrwb-7.0.0.3

./configure --prefix=/usr
make
sudo make install
```

3. Get the latest ffmpeg source
Code:

```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg-svn
```

4. Compile ffmpeg

Code:

```
cd ffmpeg-svn

./configure --enable-libamr-nb --enable-libamr-wb --enable-nonfree
make
```
i also did a sudo make install

still no audio. my conclusion is that ffmpeg is installed but not active as totem uses gstreamer.

any help is welcomed

---

### Post by Diptansu on 2008-07-13
As newbie in linux i must say what you guys are talking is simply too complicated for me to understand ... :p

And i think its also too difficult to understand what really i have to do after so many corrections in such a long thread.

Will anybdy please tell us what chronologically we should do to play 3gp with sound in linux.

Thanking you in anticipation. :p

---

### Post by soxs on 2008-07-13
~ = is your home dir
simply type in terminal ```
mkdir ~/ffmpeg/libavcodec/amr_float
``` this will create the named dir

---

### Post by Diptansu on 2008-07-13
yah, i have understood what u said ... actually have done that myself ... and put that file named '26104-510_ANSI_C_source_code' into that folder 'amr_float' ...

But what s next?

that configure command is not working for me ... moreover what wd b the actual command? ... people are saying so many things , i m confused ... :(.

plss tell me what i should do now?

---

