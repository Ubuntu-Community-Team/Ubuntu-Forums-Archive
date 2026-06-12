---
title: "avidemux convert mpg to avi"
date: 2009-05-11
forum: General Help
---

### Post by TheMagician001 on 2009-05-11
Hi. im trying to convert my mpeg files to avi so i can play them on my xbox360.. but when i try to do this .. it makes the file larger and the sound and video dont sync out by like 20 - 20 seconds can anyone help me with this or suggest a better way of doing this...

thanks
 mike

---

### Post by ckonestroh on 2009-05-11
> **TheMagician001 said:**
> Hi. im trying to convert my mpeg files to avi so i can play them on my xbox360.. but when i try to do this .. it makes the file larger and the sound and video dont sync out by like 20 - 20 seconds can anyone help me with this or suggest a better way of doing this...

thanks
 mike

I used mencoder to do this can't remember if it excepted the file types your after I will look around for file I remember finding it on Linuxquestions.org furom

later

---

### Post by ckonestroh on 2009-05-11
ok found data on mencoder sent as attachment....

Hope this helps...



Sorry no go on attachment...

This howto intends to introduce to you some of the simple commands to use MPlayer's MEncoder program to convert files from one format to another.

This is not meant to be an advanced or exhaustive guide. For in-depth details see man mencoder or the official documentation:

    * MPlayer Documentation
    * Basic usage of MEncoder
    * Encoding with MEncoder 

See also MEncoder Tips and Tricks
[edit] Installation

Complete instructions on how to install MEncoder and what USE flags to use can be found in HOWTO Emerge MPlayer.

In short, make sure you have at least the encode use flag enabled when emerging media-video/mplayer to make sure MEncoder is installed.
Note: If you are serious about doing encoding, always emerge the latest ~arch versions of MPlayer and its libraries (xvid, etc) for best support and speed. Though considered "testing" in the portage tree, development versions are usually very sane and will work well.
[edit] The Basics

Now that you have mencoder installed, it's time to convert some files.

A common misconception is that since MPlayer can playback so many audio/video codecs and containers, that it can also encode to them as well. The list of codecs to encode media is too long, but some open source ones are not included (FLAC and Theora, for example).

Not to worry though -- you still have a lot of options, even if you want to encode a file for playback on Windows or Mac.

Before jumping into details, let's look at the basics for re-encoding a video file from a format MPlayer can play to an MPEG4. Here is a very simple example:
[SIZE="3"][COLOR="Red"]
mencoder movie.wmv -o movie.avi -ovc lavc -oac lavc[/COLOR][/SIZE]

I'll explain each option being passed:

    * movie.wmv - the filename of the original movie file you want to re-encode. It can be any file format that mplayer can play (mplayer can play almost anything). 

    * -o <filename> the filename to save the encoded file to. On older version of MPlayer, if you do not provide an argument, mencoder will output to "test.avi". 

    * -ovc <video codec> OVC stands for 'output video codec'. This is the library you want to use to encode the video. 

    * -oac <audio codec> OAC stands for 'output audio codec'. This is the library you want to encode the audio portion with. 

Believe it or not -- that's about all you need to know about re-encoding a file. The example above will encode the video to DivX (mpeg4) video and the audio track to mp2.

If you want to see how another file has been encoded, just run midentify movie.avi. You can also run file movie.avi on the new file for a more basic output. Or, if you have media-video/transcode installed, you can use tcprobe -i movie.avi as well.
[edit] Codecs and Formats

Clearing up even more confusion, video codecs and formats are not the same thing.

MPEG-4 is a video format. You can create MPEG-4 videos with some of the optional codecs. DivX, XviD and lavc are the codecs that actually create the videos for you. There are lots more video formats besides MPEG-4, and lavc is one codec that can encode to a lot of those formats.

MPEG-2 is another video format. DVD videos are stored in that format. That's why you can rip a DVD with similar quality but smaller size to the newer MPEG-4.

Before you start encoding your files though, it's a good idea to decide which video format you want. MPEG-4 will be used as the default in here, since it results in highly compressed files with very good quality.
[edit] Multimedia Containers

A multimedia container is what you will put your encoded audio and video into. Some container formats include AVI, ASF, Ogg Media, Matroska, and MOV. They are called containers because you can put all kinds of stuff into them. For instance, just because a file has an extension of .avi does not mean that it is an MPEG4. It can really be any kind of file that AVI has support for, both audio and video. That's why you can encode movies with so many codecs and still put them in the same wrapper.

Let's take a brief look at some of the more common multimedia containers you'll run into. Again, even though MPlayer can play back many of these, it can't encode to all of them. That won't prove to be a limitation though.

AVI (Audio Video Interleave), although it was created by Microsoft, is open and well supported. mplayer and mencoder can play and encode AVI files. AVI is quite common, and so you'll see a lot of our examples use this one.

Matroska is an open-source video container, similar to AVI, except that it has many more advanced options and settings that can be included in the metadata. mplayer and mencoder can play and read Matroska files, but not create them. Matroska audio and video files use filename extensions .mka and .mkv, respectively.

ASF (Advanced Streaming Format) is another wrapper format, designed by Microsoft, used mostly for streaming media. Technically, anything that can be put into an AVI can also be contained in an ASF, but generally speaking, most use Windows Media Video and/or Windows Media Audio codecs.

Ogg or Ogg bitstream format is also an open-source multimedia container, part of the Xiph project. OGM is an extension of Ogg bitstream format to support some proprietary video codecs. Like Matroska, mplayer can play, but not create Ogg and OGM videos.

---

