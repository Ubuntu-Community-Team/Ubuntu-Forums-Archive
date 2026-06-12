---
title: "Encoding mp3 with sox"
date: 2005-02-27
forum: Desktop Environments
---

### Post by Rottweiler on 2005-02-27
I want to encode wav files to mp3 using sox. I've installed sox, lame, libmad0, lame-extras, liblame0, but when I do 'sox -h' it still lists mp3 as a "readonly" format.

What does it take to enable mp3 encoding in sox?

---

### Post by ChrisQ on 2005-03-04
I'd like to know this too

---

### Post by bored2k on 2005-03-04
[QUOTE=Rottweiler]I want to encode wav files to mp3 using sox. I've installed sox, lame, libmad0, lame-extras, liblame0, but when I do 'sox -h' it still lists mp3 as a "readonly" format.

What does it take to enable mp3 encoding in sox?[/QUOTE]

u installed lame?

> $lame audioslave.mp3 
does the job ...

---

### Post by ChrisQ on 2005-03-04
I have a slightly different problem. I have to take a 25 second stereo mp3 change it to mono, change the bitrate to 16kbps change the sample rate to 16000 Hz and speed it up about 1.8 times so that it still sounds like it is running at the right tempo. Can I do this with lame and if so, how?

---

### Post by Rottweiler on 2005-03-04
[QUOTE=ChrisQ]I have a slightly different problem. I have to take a 25 second stereo mp3 change it to mono, change the bitrate to 16kbps change the sample rate to 16000 Hz and speed it up about 1.8 times so that it still sounds like it is running at the right tempo. Can I do this with lame and if so, how?[/QUOTE]Sox can do that.

Anyone know how to get sox to encode mp3's? I had this working under RH9 so it's not rocket science.

---

### Post by MIchael Walma on 2008-03-14
I know this thread is ancient, but it's the one I came across when googling for an answer, so I thought I'd post my solution here.

You can recompile sox with mp3 encoding support.  First, ensure that multiverse, universe and restricted are in your /etc/apt/sources.list.  Then install the necessary software and libraries:

```
sudo aptitude install sox build-essentials liblame liblame-dev
```

You need to install liblame and liblame-dev as they are not dependencies of sox and so won't get installed automatically at the build-dep stage.  I put sox in there so as to ensure that all the other non-lame run-time library dependencies for sox get installed before we build and install our new version.

Change directory to a nice place (I like /usr/src), then get the source for sox and the libraries on which it depends:

```
sudo apt-get build-dep sox
```
```
sudo apt-get source sox
```

Unpack the source:

```
sudo dpkg-source -x sox_12.18.2-1.dsc
```

Edit the debian/rules file with your favourite editor:

```
sudo vim sox-12.18.2/debian/rules
```

and comment out, by putting an '#' at the beginning of the line, the two lines that read:

> DEB_CONFIGURE_EXTRA_FLAGS := --disable-lame

Change directory into the sox source directory 

```
cd sox-12.18.2
```

and build the binary deb:

```
sudo dpkg-buildpackage -b
```

Change directory up one level and install the newly built mp3 encoding sox .deb:

```
sudo dpkg -i sox_12.18.2-1_i386.deb
```

And you are done...

---

