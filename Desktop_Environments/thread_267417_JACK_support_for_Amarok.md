---
title: "JACK support for Amarok?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by motin on 2006-09-28
This sucks: [http://bugs.kde.org/show_bug.cgi?id=134767](http://bugs.kde.org/show_bug.cgi?id=134767) - JACK support for Amarok is a big no-no at least from the developers of Amarok. 

Is there any other way to get Amarok to route it's audio to JACK? Maybe with an unstable gstreamer package or something? Can't find the amarok-gstreamer engine in the Dapper repos...

And if it is totally impossible, what are the best alternatives (with JACK support of course)? I have tried XMMS+Madman but I do not really like it... Are there other options?

UPDATE 09-dec-2007:
[SIZE="5"]THE SOLUTION (For Gutsy):[/SIZE]

If you haven't enabled the backports repository, then you are running version 1.1.7 of xine and you can either rebuild the plugin (described in a post on Page 2) or (if on i386) use the attached variant (from a rebuild of the official ubuntu packages with the building of this plugin enabled). Put xineplug_ao_out_jack.so in /usr/lib/xine/plugins/1.1.7/ and restart Amarok. Then choose jack output in the Amarok Engine settings!

If you are using 1.1.8, then you can use the Debian testing version of libxine1-misc-plugins that includes this plugin. I use it and it works great! Available here: [http://packages.debian.org/lenny/libxine1-misc-plugins](http://packages.debian.org/lenny/libxine1-misc-plugins) . Or you can use the attached one (it's the same one, and copying this one file doesn't require any package installation. Put xineplug_ao_out_jack.so in /usr/lib/xine/plugins/1.1.8/ , restart Amarok and choose the Jack output plugin in the Amarok Engine settings.)

Listening to my amarok tunes and playing on my keyboard right now! :guitar:

Hope this works for you too!

---

### Post by naught101 on 2007-10-05
My inderstanding of the amarok dev's positions is that it should be the audio engine that interacts with jack, not amarok itself. In otherwords, we need xine to play nicely with jack, not amarok. I've seen reports of people getting it to work with the SVN version of xine, comiled from source, but I tried that, and it didn't work.

Definitely with you though, I'd love to be able to use amarok and jack at the same time..

---

### Post by naught101 on 2007-10-22
oh, there's a program called "Aqualung" ([http://aqualung.sourceforge.net/](http://aqualung.sourceforge.net/)), which isn't in the repos, but is available from getdeb.net. It's kind of similar to winamp2 in terms of use. Not as good as amarok, but it works with jack.

I've put in a wishlist report: [https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/152487](https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/152487)

---

### Post by naught101 on 2007-10-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/152487](https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/152487) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				eh, what do you know... it works now.
Go to the xine website, and the downloads page: [http://xinehq.de/index.php/releases](http://xinehq.de/index.php/releases)
download the latest... oh, just do this:

```
wget http://prdownloads.sourceforge.net/xine/xine-lib-1.1.8.tar.bz2
tar -jxf xine-lib-1.1.8.tar.bz2
cd xine-lib-1.1.8
./configure
make
sudo make install 

```
then start up jack, and then start amarok. Go to "settings" > "configure amarok" > engines. Xine should be selected, and output can be set to Jack manually (check to make sure it's there).

Auto detect doesn't seem to work... but jack output is mighty fine.

---

### Post by naught101 on 2007-10-22
Wma playback is absolutely shot... another good reason to re-rip/download all those dodgy old proprietary files.

---

### Post by wheezart on 2007-10-22
I'd like to point out as well that the installation required g++ and zlib-dev packages to be installed =)

---

### Post by nynoah on 2007-11-28
I am trying to get Amarok to work with Jack too.  I tried the codes you gave, but it did not work.  Is this because I am on a 64bit system?

---

### Post by AudioGarf on 2007-12-04
I've tried to compile xine but I'm not able to do this... :-(

I've installed libxine 1.1.8 by the backports repositery, but I still havn't Jack in amarok settings.

---

### Post by Tom Mann on 2007-12-04
From release notes I've seen - no Ubuntu base libxine will ever work with JACK, and the patches actively disable Xine from compiling with JACK.

---

### Post by xl_cheese on 2007-12-04
So is this why I cannot play any mp3, wav, etc when I start qjackctl?  Only after restarting can I play those file types and again starting qjackctl breaks that.

---

### Post by motin on 2007-12-09
Solved! And without re-installing xine etc. 

Went the whole mile with this one now, having tried:
 1. Compiling from tar.gz sources using the above instructions (didn't help)
 2. Writing up a guide on howto compile from the tar.gz sources based on the official FAQ and trial and error to make sure everything was done the official way. (didn't help)
 3. Downloading Ubuntu deb-src package, enabling jack output plugin and recompiling (probably should have worked but with a lot of overhead and interfered with the fact that I have the 1.1.8 version as is availale in gutsy backports. Had to pin-down all xine packages bla and try and hell etc)
 4. Same as 2 but with version 1.1.8 from gutsy-backports (bah the sources had changed - couldn't find how to activate the plugin...)

(As I went along, I was writing a guide on how to solve the issue, which subsequently was revised again and again and rewritten 2-3 times...)

Then, on step 4 above while searching for files with "jack" in it I realized that the jack output plugin was what it claims to be: a PLUGIN. 

The list of available output options in Amarok is taken from the available output plugins, listed with:
```
ls -l /usr/lib/xine/plugins/1.1.7/xineplug_ao_*
```

Investigating further, it seems that the only disabling that has been done with the Ubuntu packages was to build the specific plugin!

And smack, there is the solution. Get hold of the compiled plugin file, put it in the xine plugin directory and you are good to go!

Attached to the original post are the compiled plugins for xine, for your convenience.

THE SOLUTION:
If you haven't enabled the backports repository, then you are running version 1.1.7 of xine and you can either rebuild the plugin or using the attached variant (from this day's earlier building session). Put xineplug_ao_out_jack.so in /usr/lib/xine/plugins/1.1.7/ and restart Amarok. Then choose jack output in the Amarok Engine settings!

If you are using 1.1.8, then you can use the Debian testing version of libxine1-misc-plugins that includes this plugin. I use it and it works great! Available here: [http://packages.debian.org/lenny/libxine1-misc-plugins](http://packages.debian.org/lenny/libxine1-misc-plugins) . Or you can use the attached one (it's the same one, and copying this one file doesn't require any package installation. Put xineplug_ao_out_jack.so in /usr/lib/xine/plugins/1.1.8/)

Hope this works for you too!

PS My in-writing guide on how to rebuild and re-enable building of the xine jack output plugin with Gutsy's native xine 1.1.7 disappeared when I mistakenly killed firefox. If you are interested, I can probably write it again - but the above should be enough to solve the Amarok Jack support issue without needing to rebuild yourself. Just tell me you're interested! Here is a quick recollection from memory:
```
apt-get source xine-lib # make sure you have the deb-src repo first
cd xine-lib-1.1.?
nano debian/libxine1.install # uncomment the jack audio output line
sudo apt-get install fakeroot libjack0.100.0-dev
sudo apt-get build-dep xine-lib
sudo nano debian/control # append libjack0.100.0-dev to the Build-Depends line(s). Hmm not really needed though as we are not installing any packages...
dpkg-buildpackage -rfakeroot
sudo cp ./debian/libxine1/usr/lib/xine/plugins/1.1.7/xineplug_ao_out_jack.so /usr/lib/xine/plugins/1.1.7/

```

---

### Post by Tom Mann on 2007-12-11
I had figured out how to fix this!

When I get home I'll upload a script to run which will build a replacement xinelib (which in turn will enable JACK as an output in all Xine Multimedia programs including Amarok).

:)

---

### Post by Steveway on 2007-12-11
There is a much easier way to do this, did it myself.
Since Ubuntu is just a Snapshot of Debian-Sid, Debian-sid-packages should work on Ubuntu.
So I went to the debian site and downloaded their amarok and also amarok-xine and amarok-engines.
Since the version numbering is different Synaptic will keep on telling you that there are updates, if you want you can lock those and stop Synaptic from doing that.
Link to the deb-files, select your architecture and then the mirror:
[http://packages.debian.org/unstable/kde/amarok](http://packages.debian.org/unstable/kde/amarok)
[http://packages.debian.org/unstable/kde/amarok-engines](http://packages.debian.org/unstable/kde/amarok-engines)
[http://packages.debian.org/unstable/kde/amarok-xine](http://packages.debian.org/unstable/kde/amarok-xine)
That should work.

---

### Post by motin on 2007-12-12
> **Tom Mann said:**
> I had figured out how to fix this!

When I get home I'll upload a script to run which will build a replacement xinelib (which in turn will enable JACK as an output in all Xine Multimedia programs including Amarok).

:)

> **Steveway said:**
> There is a much easier way to do this, did it myself.
Since Ubuntu is just a Snapshot of Debian-Sid, Debian-sid-packages should work on Ubuntu.
So I went to the debian site and downloaded their amarok and also amarok-xine and amarok-engines.
Since the version numbering is different Synaptic will keep on telling you that there are updates, if you want you can lock those and stop Synaptic from doing that.
Link to the deb-files, select your architecture and then the mirror:
[http://packages.debian.org/unstable/kde/amarok](http://packages.debian.org/unstable/kde/amarok)
[http://packages.debian.org/unstable/kde/amarok-engines](http://packages.debian.org/unstable/kde/amarok-engines)
[http://packages.debian.org/unstable/kde/amarok-xine](http://packages.debian.org/unstable/kde/amarok-xine)
That should work.

Sorry, but I think you missed that the solution is already presented above. No need to install all of Sid's amarok packages, it's enough with libxine1-misc-plugins.deb as stated above. 

Also, the different output plugins for 1.1.7 and 1.1.8 (for i386) are attached to the OP.

---

### Post by geoff123 on 2007-12-17
Motin, THANK YOU! WORKING GREAT and so easy. Geoff

---

### Post by warbread on 2008-01-27
Awesome!  Finally, I can have jack on all the time instead of turning it off to listen to music.  Kudos to you, motin.

---

### Post by Pettman on 2008-02-06
> **motin said:**
> 

PS My in-writing guide on how to rebuild and re-enable building of the xine jack output plugin with Gutsy's native xine 1.1.7 disappeared when I mistakenly killed firefox. If you are interested, I can probably write it again - but the above should be enough to solve the Amarok Jack support issue without needing to rebuild yourself. Just tell me you're interested! Here is a quick recollection from memory:
```
apt-get source xine-lib # make sure you have the deb-src repo first
cd xine-lib-1.1.?
nano debian/libxine1.install # uncomment the jack audio output line
sudo apt-get install fakeroot libjack0.100.0-dev
sudo apt-get build-dep xine-lib
sudo nano debian/control # append libjack0.100.0-dev to the Build-Depends line(s). Hmm not really needed though as we are not installing any packages...
dpkg-buildpackage -rfakeroot
sudo cp ./debian/libxine1/usr/lib/xine/plugins/1.1.7/xineplug_ao_out_jack.so /usr/lib/xine/plugins/1.1.7/

```On  the uncomment the libjack bit, I can't find a commented libjack line in said file (I've got 1.1.8 if that makes any difference).

---

### Post by warbread on 2008-02-07
Is anyone else having trouble listening to flac songs?

---

### Post by motin on 2008-02-08
> **Pettman said:**
> On  the uncomment the libjack bit, I can't find a commented libjack line in said file (I've got 1.1.8 if that makes any difference).

Yeah I too couldn't find it in 1.1.8 - so I searched around more and that's when I found the debian packages with the plugin. You ought to be able to use one of them - no need to compile.

---

### Post by leethargo on 2008-03-18
> **warbread said:**
> Is anyone else having trouble listening to flac songs?

Yes, me too. I've built the jack output plugin for jack myself and it worked so far, with mp3 and vorbis files.

What also works (without jack):
vlc plays flacs
amarok plays flacs
xine plays flacs

What works (with jack):
xine plays flacs (from command line, with -A  jack parameter) (!)

What doesn't work:
Amarok starts to play flacs (with xine/jack backend), but after a second or so stutters along.

Strange problem, especially because the xine standalone player handles the same files perfectly fine with the jack plugin.

Any help here?

---

### Post by motin on 2008-03-18
Have you tried inactivating Amarok's cross-fade?

---

### Post by leethargo on 2008-03-18
> **motin said:**
> Have you tried inactivating Amarok's cross-fade?

Cross-fading is always disabled. I tried also disabling the fade-out, but that didn't help either.

---

### Post by neltnerb on 2008-05-31
> **motin said:**
> Solved! And without re-installing xine etc. 

Went the whole mile with this one now, having tried:
 1. Compiling from tar.gz sources using the above instructions (didn't help)
 2. Writing up a guide on howto compile from the tar.gz sources based on the official FAQ and trial and error to make sure everything was done the official way. (didn't help)
 3. Downloading Ubuntu deb-src package, enabling jack output plugin and recompiling (probably should have worked but with a lot of overhead and interfered with the fact that I have the 1.1.8 version as is availale in gutsy backports. Had to pin-down all xine packages bla and try and hell etc)
 4. Same as 2 but with version 1.1.8 from gutsy-backports (bah the sources had changed - couldn't find how to activate the plugin...)

(As I went along, I was writing a guide on how to solve the issue, which subsequently was revised again and again and rewritten 2-3 times...)

Then, on step 4 above while searching for files with "jack" in it I realized that the jack output plugin was what it claims to be: a PLUGIN. 

The list of available output options in Amarok is taken from the available output plugins, listed with:
```
ls -l /usr/lib/xine/plugins/1.1.7/xineplug_ao_*
```

Investigating further, it seems that the only disabling that has been done with the Ubuntu packages was to build the specific plugin!

And smack, there is the solution. Get hold of the compiled plugin file, put it in the xine plugin directory and you are good to go!

Attached to the original post are the compiled plugins for xine, for your convenience.

THE SOLUTION:
If you haven't enabled the backports repository, then you are running version 1.1.7 of xine and you can either rebuild the plugin or using the attached variant (from this day's earlier building session). Put xineplug_ao_out_jack.so in /usr/lib/xine/plugins/1.1.7/ and restart Amarok. Then choose jack output in the Amarok Engine settings!

If you are using 1.1.8, then you can use the Debian testing version of libxine1-misc-plugins that includes this plugin. I use it and it works great! Available here: [http://packages.debian.org/lenny/libxine1-misc-plugins](http://packages.debian.org/lenny/libxine1-misc-plugins) . Or you can use the attached one (it's the same one, and copying this one file doesn't require any package installation. Put xineplug_ao_out_jack.so in /usr/lib/xine/plugins/1.1.8/)

Hope this works for you too!

PS My in-writing guide on how to rebuild and re-enable building of the xine jack output plugin with Gutsy's native xine 1.1.7 disappeared when I mistakenly killed firefox. If you are interested, I can probably write it again - but the above should be enough to solve the Amarok Jack support issue without needing to rebuild yourself. Just tell me you're interested! Here is a quick recollection from memory:
```
apt-get source xine-lib # make sure you have the deb-src repo first
cd xine-lib-1.1.?
nano debian/libxine1.install # uncomment the jack audio output line
sudo apt-get install fakeroot libjack0.100.0-dev
sudo apt-get build-dep xine-lib
sudo nano debian/control # append libjack0.100.0-dev to the Build-Depends line(s). Hmm not really needed though as we are not installing any packages...
dpkg-buildpackage -rfakeroot
sudo cp ./debian/libxine1/usr/lib/xine/plugins/1.1.7/xineplug_ao_out_jack.so /usr/lib/xine/plugins/1.1.7/

```
Rather infuriatingly, the forum decided to give me a stupid error on submitting my original post in which I gave detailed instructions for translating this to Hardy Heron. I don't have the patience to type it all again, so here is a summary.

The format of the source file has changed in Hardy, so the above instructions won't quite work. Work from them as a starting point, I have coaxed it into working by doing the following.

Edit debian/rules to replace --without-jack to --with-jack. If you don't do this, then it won't build the module regardless of what you do with the .install file.

Edit debian/libxine1-misc-plugins.install and uncomment the xineplug_ao_out_jack.so line as instructed above.

After doing this, I still had a number of errors compiling the other subpackages of libxine due to presumably missing development library packages. As the only thing that actually needs to compile is the xineplug_ao_out_jack.so file, I didn't bother tracking all of these down and instead simply commented out the missing files from the referenced libxine1-*.install files (I believe it was only libxine1-console and libxine1-x for me, both the flac and directfb files).

After doing this, it compiled fine, and copying the plugin file as instructed above into the same location as instructed above has made jack work fine on my computer.

I have attached the plugin I compiled against xine-lib-1.1.11.1-1ubuntu3.

---

### Post by motin on 2008-06-02
> **neltnerb said:**
> 
I have attached the plugin I compiled against xine-lib-1.1.11.1-1ubuntu3.

Great work neltnerb! I had yet to fix Amarok JACK output in Hardy. 

Too bad about that forum issue*, but would you mind sharing where you put your compiled plugin?
I have no /usr/lib/xine/plugins/1.1.11/-folder, instead my plugins seem to be located in /usr/lib/xine/plugins/1.20/, and downloading your plugin to my Desktop and running:
```
bunzip2 Desktop/xineplug_ao_out_jack.bz2
sudo cp Desktop/xineplug_ao_out_jack /usr/lib/xine/plugins/1.20/xineplug_ao_out_jack.so
```

... does not allow me to choose jack for output in Amarok...

* We know never to trust web-based input forms, so install glipper and then make a habit of Ctrl+A Ctrl+C before any textarea submit - it will save you a lot of frustration over time.

---

### Post by motin on 2008-06-02
Btw, I really hope that the more generic approach [PulseAudio through JACK on Hardy]("http://ubuntuforums.org/showthread.php?p=4795013#post4795013") will work eventually, giving JACK output options for not only Amarok, but all PulseAudio-compatible applications. If you have anything to contribute in making that a reality, please do. Thanks a million!

---

### Post by neltnerb on 2008-06-05
> **motin said:**
> Great work neltnerb! I had yet to fix Amarok JACK output in Hardy. 

Too bad about that forum issue*, but would you mind sharing where you put your compiled plugin?
I have no /usr/lib/xine/plugins/1.1.11/-folder, instead my plugins seem to be located in /usr/lib/xine/plugins/1.20/, and downloading your plugin to my Desktop and running:
```
bunzip2 Desktop/xineplug_ao_out_jack.bz2
sudo cp Desktop/xineplug_ao_out_jack /usr/lib/xine/plugins/1.20/xineplug_ao_out_jack.so
```

... does not allow me to choose jack for output in Amarok...

* We know never to trust web-based input forms, so install glipper and then make a habit of Ctrl+A Ctrl+C before any textarea submit - it will save you a lot of frustration over time.
Aha.

It was compressed using the 'tar -cjf' command, not just bzip. You have to uncompress it by using 'tar -xjf xineplug_ao_out_jack.bz2'. What you copied into your 1.20 directory is a tar file containing the plugin. And yes, it should go into the /usr/lib/xine/plugins/1.20/ directory.

I agree that pulseaudio outputting to jack is ideal, but this seems to be much further from functional than your HOWTO here as far as amarok is concerned =) I feel like a reasonable workaround should be to have ALSA recognize jack as an output device, but even though I was able to do this, it didn't integrate at all into the rest of the system.

In particular, jackd has to be running before you try to connect ALSA to it -- since ALSA starts far before you can open qjackctl or run jackd from the command line as a human, this has to be addressed by some sort of script. I'm not sure as to the timing, so that's something that would have to be addressed. Further, the System->Sound configuration tool didn't list the jack devices even when I started the jack server and then restarted ALSA. I could *try* to figure out how to configure gnome to output to my chosen device, but it's a lot of hassle.

I'd personally rather just use this workaround for my music along with 'mplayer -ao jack' for movies until the Ubuntu developers consider jack to be stable enough to include in universe. The only other thing I'd like to be able to do is get firefox to output to jack as well, but I don't see anything reasonable matching 'sound' or 'audio' in about:config.

---

### Post by motin on 2008-07-03
> **neltnerb said:**
> Aha.

It was compressed using the 'tar -cjf' command, not just bzip. You have to uncompress it by using 'tar -xjf xineplug_ao_out_jack.bz2'. What you copied into your 1.20 directory is a tar file containing the plugin. And yes, it should go into the /usr/lib/xine/plugins/1.20/ directory.

Thanks man, now it worked as expected!

Regarding your comments about JACK/PulseAudio, I have responded to it in the other thread. 

Now I'm off for some jamming... Cheers!

---

