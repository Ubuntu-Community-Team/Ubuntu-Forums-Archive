---
title: "how to convert wmv to mpg"
date: 2009-04-03
forum: General Help
---

### Post by eeeek on 2009-04-03
I have home videos in wmv format that I'd like to convert to mpg. What's the easiest way to do that?

I have checked and I haven't found any good solutions that don't include going out and buying software.

Shall I use mencoder? I can't find docs on anything with wmv.

---

### Post by maheshasolkar on 2009-04-03
Have you tried ffmpeg? Something like following should easily convert a WMV file to MPG:

```
ffmpeg -i file_name.wmv file_name.mpg
```

If ffmpeg is not already installed on your system, following will install it:

```
sudo aptitude install ffmpeg
```

There are a zillion other things you can do with ffmpeg. Explore with:

```
man ffmpeg
```

I am pretty sure there is a GUI around ffmpeg out there, but I have not used it yet.

Hope this helps.

---

### Post by Dejai on 2009-04-03
I head that memcoder works fairly well, apparently a GUI for ffmpeg is kmediafactory. I  got that info from the following post [http://ubuntuforums.org/showthread.php?t=319004](http://ubuntuforums.org/showthread.php?t=319004)

---

### Post by eeeek on 2009-04-03
Thank you for the GUI suggestion. I'll give kmediafactory a try when I get home tonight.

I am willing to try video conversion with the command line, but I'm not wild about it. 

By the way, I was able to run TMPGenc via Wine. That's what I use to do the wmv to mpg conversion in windows. However, there was some sort of plugin for wmv files that I can't remember where it is. TMPGenc, under the free version, lets you do mpeg1 conversions (mpeg2 requires paying guests).

Anyways, I'll tackle this tonight and report back. Thanks again for the help, guys.

---

### Post by logic++ on 2009-04-03
You should try out [avidemux]("http://fixounet.free.fr/avidemux/"). You can install it from the Ubuntu repositories with:
```
sudo apt-get install avidemux
```

---

### Post by maheshasolkar on 2009-04-03
There's another GUI for ffmpeg - traGtor:

  [http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)

It is from a German company, but provides english interface. It is delivered in a .deb package, so it is easy to install on Ubuntu. It puts a pretty GUI around ffmpeg. But, in my opinion, does not make using ffmpeg any easier.

Its interface seems like GUI elements to input all the ffmpeg command line options.

It does not have a dumbed-down interface to do simple conversions easily - which most of us would love.

I haven't played around with it a lot, yet.

---

### Post by andrew.46 on 2009-04-04
Hi,

Sometimes even FFmpeg has some trouble with these files. Have a look at the athletics required to transcode one such difficult file:

[http://ubuntuforums.org/showpost.php?p=6737807&postcount=15](http://ubuntuforums.org/showpost.php?p=6737807&postcount=15)

A fair amount of time and effort invested into that little promo video :-).

Andrew

---

### Post by mb_webguy on 2009-04-04
You can do it with [VLC]("http://wiki.videolan.org/Transcode"), either with the GUI or from the command line.  You can even do batch transcoding.

---

### Post by maheshasolkar on 2009-04-04
> **mb_webguy said:**
> You can do it with [VLC]("http://wiki.videolan.org/Transcode"), either with the GUI or from the command line.  You can even do batch transcoding.
VLC just never seizes to amaze me. Thanks for the info. The option is right there in the Media menu, but never spotted it!

---

### Post by eeeek on 2009-04-06
Well, I tried kmediafactory. No dice - I think that is set up for something else - DVD creation or something. Avidemux didn't present an obvious solution in looking over it. 

I was able to convert the wmv to mpg 1 with VLC. Very easy and straight forward via the Wizard - Transcode option. Yes, VLC is amazing.

However the output was a little choppy. I wasn't sure what to put for the video bitrate - which is probably where the problem lies. I selected 1024 kb/s. I'll have to figure that out.

But again, thanks so much for the tip on VLC - that's exactly what I was looking for.

---

