---
title: "FFMpeg installation fail"
date: 2012-06-21
forum: Desktop Environments
---

### Post by kmccmk9 on 2012-06-21
Hello,

I am trying to compile ffmpeg from source as detailed here [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). So far everything has worked except when I try to make ffmpeg. I issue the command and it tells me it can't find libx264. Which is weird since I had installed it with complete success. Any help would greatly be appreciated.

---

### Post by hwychld on 2012-06-21
Can you post a screen shot of the error?  Also, the link to the instructions you are following did not work.

---

### Post by kmccmk9 on 2012-06-21
> **hwychld said:**
> Can you post a screen shot of the error?  Also, the link to the instructions you are following did not work.

Sorry about that, my apologies. I have edited the post and posted a screen shot here.

**Picture won't show so here is the direct link**
[http://s148.photobucket.com/albums/s37/kmccmk9/?action=view¤t=FFMPEG.png]("http://s148.photobucket.com/albums/s37/kmccmk9/?action=view&current=FFMPEG.png")
[IMG]http://s148.photobucket.com/albums/s37/kmccmk9/?action=view&current=FFMPEG.png[/IMG]

---

### Post by hwychld on 2012-06-21
OK, I can get to the instructions now but I can't get the screenshot big enough to see what the text says.  Can you copy the text to a code block like this 
```

paste terminal output here

```

---

### Post by kmccmk9 on 2012-06-21
> **hwychld said:**
> OK, I can get to the instructions now but I can't get the screenshot big enough to see what the text says.  Can you copy the text to a code block like this 
```

paste terminal output here

```

No problem see code block below:
```

kyle@kyle-linux:~/ffmpeg$ sudo ./configure --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
ERROR: libx264 not found

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
ffmpeg-user@ffmpeg.org mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solving the problem.

```

---

### Post by hwychld on 2012-06-21
From what I can tell, the library in question should have been created with this:

```

cd x264 ./configure --enable-static make sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | \   awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes \   --fstrans=no --default
```

Were there any errors with ./configure or make.  What was the result of checkinstall?

What is the reason for compiling this from source as opposed to installing via apt-get (you very well may have a good reason, I do this for programs like nmap so I have the most recent OS signatures)?

---

### Post by kmccmk9 on 2012-06-21
> **hwychld said:**
> From what I can tell, the library in question should have been created with this:

```

cd x264 ./configure --enable-static make sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | \   awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes \   --fstrans=no --default
```Were there any errors with ./configure or make.  What was the result of checkinstall?

What is the reason for compiling this from source as opposed to installing via apt-get (you very well may have a good reason, I do this for programs like nmap so I have the most recent OS signatures)?

To answer the first part, I did use that command and it worked flawlessly. I'm compiling to source so I can enable all the codecs that are normally blocked.

---

### Post by Jose Catre-Vandis on 2012-06-21
I spotted a sudo in there somewhere which may not have been needed.

Are you using "sudo make" on ffmpeg too  ???


If you used sudo where it wasn't needed you may end up with some permissions problems later on, this is why the guide asked you to git / clone / configure / make in your home directory. Only the install requries sudo.

---

### Post by kmccmk9 on 2012-06-21
> **Jose Catre-Vandis said:**
> I spotted a sudo in there somewhere which may not have been needed.

Are you using "sudo make" on ffmpeg too  ???


If you used sudo where it wasn't needed you may end up with some permissions problems later on, this is why the guide asked you to git / clone / configure / make in your home directory. Only the install requries sudo.

When I tried commands without sudo I got permission error.

---

### Post by Jose Catre-Vandis on 2012-06-22
Did you follow the guide to the letter? You should only have to use sudo on the apt-get commands at the beginning and the install command at the end. everything else is in your ~/home area so should not require sudo.

---

### Post by kmccmk9 on 2012-06-22
> **Jose Catre-Vandis said:**
> Did you follow the guide to the letter? You should only have to use sudo on the apt-get commands at the beginning and the install command at the end. everything else is in your ~/home area so should not require sudo.

I followed it but I had to use sudo otherwise I got a permission error. Like I had to use sudo make for x264. I was in the x264 directory.

---

### Post by Jose Catre-Vandis on 2012-06-22
but where was the x264 directory?

~/home/"user"/x264 ?

with you loogged in as that user?

I could, of course be barking up the wrong tree (awaits Fakeoutdoorsman to be put straight ;))

---

### Post by kmccmk9 on 2012-06-22
> **Jose Catre-Vandis said:**
> but where was the x264 directory?

~/home/"user"/x264 ?

with you loogged in as that user?

I could, of course be barking up the wrong tree (awaits Fakeoutdoorsman to be put straight ;))

Yes I was in that directory I believe. I didn't do the first cd that the article says to do. Could that have screwed it up?

---

### Post by hwychld on 2012-06-22
It may have. A cd with nothing following it changes to the home directory of the current user.  This ensures that you are operating in a directory with which you have full permissions. Therefore you should not need to use sudo. If you do, then the library created will be owned by root, not you.

---

### Post by kmccmk9 on 2012-06-23
> **hwychld said:**
> It may have. A cd with nothing following it changes to the home directory of the current user.  This ensures that you are operating in a directory with which you have full permissions. Therefore you should not need to use sudo. If you do, then the library created will be owned by root, not you.

Ok so how do I remove what I have already done and start over?

---

### Post by kmccmk9 on 2012-06-23
> **hwychld said:**
> It may have. A cd with nothing following it changes to the home directory of the current user.  This ensures that you are operating in a directory with which you have full permissions. Therefore you should not need to use sudo. If you do, then the library created will be owned by root, not you.

As I was going through it again, I came to the ./configure --enable-static portion for x264. After doing command I received error. I don't have the version of yasm that it wants. Do I compile without asm or do I try to update yasm? I have tried updating yasm before but it tells me I'm at the latest version.

---

### Post by mc4man on 2012-06-23
> **kmccmk9 said:**
> As I was going through it again, I came to the ./configure --enable-static portion for x264. After doing command I received error. I don't have the version of yasm that it wants. Do I compile without asm or do I try to update yasm? I have tried updating yasm before but it tells me I'm at the latest version.

What release of Ubuntu are you using?
That guide is for  - 
> This guide supports Ubuntu Precise Pangolin 12.04, Ubuntu Oneiric Ocelot 11.10, Ubuntu Natty Narwhal 11.04, and Ubuntu Maverick Meerkat 10.10.

If using earlier then you'll notice right below the above there are links for 
> Separate guides are available for Ubuntu Lucid Lynx 10.04 and Ubuntu Hardy Heron 8.04.

---

### Post by kmccmk9 on 2012-06-23
> **mc4man said:**
> What release of Ubuntu are you using?
That guide is for  - 


If using earlier then you'll notice right below the above there are links for

Okay I got it installed with your help. However I can't get it to work for me at all. I have tried so many combinations to convert my mp4 to ogv. I have tried the simple ```
sudo ffmpeg -i IntroVideo.mp4 IntroVideo.ogv
``` to the complex
```
sudo ffmpeg -i IntroVideo.mp4 -acodec libmp3lame -vcodec libtheora -ar 22050 IntroVideo.ogv

```

---

### Post by Jose Catre-Vandis on 2012-06-24
Something must still be wrong with the installation, the first command works fine here (on Xubuntu 12.04 with ffmpeg/x264 compiled as per the ffmpeg guide). And you are still using sudo!! Should not be needed to run the ffmpeg command.

Which Ubuntu and version are you on? Does the compile include ogg/ogv? ( run ffmpeg -codecs | grep vorbis in terminal )

What output do you get from running that first command?

---

### Post by mc4man on 2012-06-24
And it also appears you continue to  use sudo Way too much

---

### Post by kmccmk9 on 2012-06-25
> **mc4man said:**
> And it also appears you continue to  use sudo Way too much

Well, I found out I just had to define the -acodec to make it work. And I did not use sudo. My problem, video quality. How can I increase the video quality.

---

### Post by Jose Catre-Vandis on 2012-06-26
For example, set video bitrate to 64kbits/sec
```
-b:v 64k
```

[http://ffmpeg.org/ffmpeg.html](http://ffmpeg.org/ffmpeg.html)

---

### Post by FakeOutdoorsman on 2012-06-26
> **Jose Catre-Vandis said:**
> I could, of course be barking up the wrong tree (awaits Fakeoutdoorsman to be put straight ;))
I thought you were already doing a good job.

> **kmccmk9 said:**
> How can I increase the video quality.
You can also use *-q:v* (an alias for *-qscale:v*). It will set a constant quality level. If you have several videos to encode, *-q:v* will allow them to all be the same output quality.

The values of *-q:v* vary depending on the encoder. See [How to convert flv file to Theora: best practices](http://ubuntuforums.org/showpost.php?p=11530735&postcount=2) for examples on what values to use.

---

