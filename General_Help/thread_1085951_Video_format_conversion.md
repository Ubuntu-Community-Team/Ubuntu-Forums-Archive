---
title: "Video format conversion"
date: 2009-03-03
forum: General Help
---

### Post by Chamillionaire2 on 2009-03-03
Hello.

Is there any video format converters for ubuntu? :-k

Thanks Bye.

---

### Post by kellemes on 2009-03-03
> **Chamillionaire2 said:**
> Hello.

Is there any video format converters for ubuntu? :-k

Thanks Bye.

What you need to convert? And to what?

---

### Post by binbash on 2009-03-03
handbrake, winff etc

---

### Post by mb_webguy on 2009-03-03
There are numerous GUI converters available, but they're generally front-ends for mencoder and/or ffmpeg.  If you're comfortable with the command-line, you can convert to and from just about any audio or video format to any other audio or video format using one of these tools.

If, however, you're more comfortable with a GUI application, I'd suggest Handbrake (which is great if you're converting videos to play on something like an iPod or PS3), Avidemux (which is actually a video editor, but also allows for fairly easy conversion), or WinFF (which doesn't have the most intuitive interface, but is very configurable).  The VLC media player can also convert between any formats it can play (which is most of them).

All of these, I believe, can be found in the repositories, though you should definitely add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository if you haven't already, and you might want to consider getting the newest versions of these programs.

[Handbrake PPA]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")
[Debs for recent versions of VLC]("http://archive.getdeb.net/dump/intrepid/vlc/")
[WinFF repository]("http://code.google.com/p/winff/wiki/UbuntuInstallation") instructions

---

### Post by michael37 on 2009-03-03
Avidemux is an excellent video conversion package.  It's available in the multiverse repository.

Handbrake for Ubuntu is available in a repository listed here:
```

deb http://ppa.launchpad.net/handbrake-ubuntu/ubuntu hardy main

or 

deb http://ppa.launchpad.net/handbrake-ubuntu/ubuntu intrepid main

```

depending on your version of Ubuntu.

Add this repository in System/Administration/Software Sources/Third-Party Software.

Ignore the "errors" about unauthenticated packages.

---

### Post by 3rdalbum on 2009-03-04
I wouldn't recommend VLC. It's a great video player, but I've never been able to get it to transcode video.

I do actually recommend learning FFmpeg on the command-line. You get a great degree of control and it's easy to use for a command-line application. However, a lot of people get put off because they don't understand the difference between a container format and a compression format. If you understand that, for instance, AVI is a container format and H264 is a compressor, you will probably like using ffmpeg on the command-line.

Read the manual:

```
man ffmpeg
```

Look at what formats (and names for formats) are used in ffmpeg:

```
ffmpeg -formats
```

---

### Post by mb_webguy on 2009-03-04
> **3rdalbum said:**
> I wouldn't recommend VLC. It's a great video player, but I've never been able to get it to transcode video.

Well, I just ripped the audio from a wmv to an mp3 with no problem whatsoever using VLC.  I'm using 0.9.8a rather than the repository version, but I don't know if that has anything to do with it, since I've been transcoding audio and video for quite a while with VLC.

Granted, depending on what you're doing, other apps are easier or better -- Handbrake and Avidemux are better for video-to-video transcoding, for example -- but for things like ripping just the audio or just the video from a file, VLC is one of the simplest methods I've used.

---

### Post by michael37 on 2009-03-06
> **3rdalbum said:**
> I wouldn't recommend VLC. It's a great video player, but I've never been able to get it to transcode video.

I do actually recommend learning FFmpeg on the command-line. You get a great degree of control and it's easy to use for a command-line application. However, a lot of people get put off because they don't understand the difference between a container format and a compression format. If you understand that, for instance, AVI is a container format and H264 is a compressor, you will probably like using ffmpeg on the command-line.
 <>

FFmpeg is a sledgehammer.  It's the most powerful tool, but is also the hardest to learn and the most dangerous and frustrating if used incorrectly.

If you do want to learn FFmpeg, start with a graphical interface to it, [Winff, follow link to see instructions to install it]("http://code.google.com/p/winff/wiki/UbuntuInstallation").

---

### Post by andrew.46 on 2009-03-06
Hi michael,

> **michael37 said:**
> FFmpeg is a sledgehammer.  It's the most powerful tool, but is also the hardest to learn and the most dangerous and frustrating if used incorrectly.

Mind you the basic syntax could not be easier:

```
ffmpeg -i infile outfile
```

and often it does not have to be much more complicated than that. I acknowledge of course that this is just the very *beginning* with FFmpeg.

Andrew

---

